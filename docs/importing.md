# Importing Models into Runway

Runway models are platform-agnostic; models written in any framework/language can be used by Runway as long as the model can be made accessible via an HTTP server. This process, however, is easiest in Python where we provide an SDK for parsing the inputs to the model, serializing its outputs, and setting up the server environment.

A Runway Model consists of an HTTP server that exposes a common interface over a network and a configuration file that specifies dependencies and build steps for running that server (and your model code) inside a Docker container. Both the network interface for interacting with the model and the Docker images created as a result of the configuration file are abstracted from the developer using the [Runway Model SDK](https://sdk.runwayml.com).

Here are the steps involved in porting an ML model written in Python to Runway:

1. Create a `runway_model.py` file which implements several methods from the [Runway Model SDK](https://sdk.runwayml.com).
1. Write a `runway.yml` config file.
1. Upload your code to a GitHub repository.
1. Import your new model into the Runway app using your GitHub account.

Once you've imported your model into Runway using your GitHub account, each `git push` will trigger the latest version of your code to be built and optionally deployed publicly through Runway.

In this tutorial, we will demonstrate how to port the [SqueezeNet](https://arxiv.org/abs/1512.03385) computer vision model to Runway. We also provide a [Runway Model Template](https://github.com/runwayml/model-template) repository that contains boilerplate code for porting a new model.

### Importing SqueezeNet into Runway

We recommend cloning the `runwayml/squeezenet` GitHub repository so that you can follow along with the tutorial.

```bash
git clone https://github.com/runwayml/model-squeezenet
cd model-squeezenet
```

#### 1. Create a `runway_model.py` model server file

SqueezeNet is a neural network architecture used for computer vision tasks, optimized for mobile/embedded devices. [PyTorch](https://github.com/pytorch/vision) includes an implementation of SqueezeNet pre-trained on ImageNet that can be used out-of-the-box for object recognition.

Here's the code to classify a single local image (via a hard-coded path) with pre-trained SqueezeNet:

```python
# model.py
import json
from PIL import Image
from torchvision import models, transforms
from torch.autograd import Variable

# Read the index -> label mapping from a file
labels = json.load(open('labels.json'))

# set up preprocessing transformations

normalize = transforms.Normalize(
   mean=[0.485, 0.456, 0.406],
   std=[0.229, 0.224, 0.225]
)

preprocess = transforms.Compose([
   transforms.Scale(256),
   transforms.CenterCrop(224),
   transforms.ToTensor(),
   normalize
])

# initialize the model and download pre-trained weights

model = models.squeezenet1_1(pretrained=True)

# open a local image
img = Image.open('still_life.jpg')

# preprocess the image and convert it into a tensor
img_tensor = preprocess(img)
img_tensor.unsqueeze_(0)
img_variable = Variable(img_tensor)

# do a forward pass and classify the image
fc_out = model(img_variable)
label = labels[str(fc_out.data.numpy().argmax())]
print(label)
# lemon
```

And here's the modified code for the same model wrapped in a server so that Runway can access it:


```diff
import json
from PIL import Image
from torchvision import models, transforms
from torch.autograd import Variable
+ import runway
+ from runway.data_types import image, text

labels = json.load(open('labels.json'))

normalize = transforms.Normalize(
   mean=[0.485, 0.456, 0.406],
   std=[0.229, 0.224, 0.225]
)

preprocess = transforms.Compose([
   transforms.Scale(256),
   transforms.CenterCrop(224),
   transforms.ToTensor(),
   normalize
])

+ @runway.setup
+ def setup():
+     return models.squeezenet1_1(pretrained=True)

+ @runway.command('classify', inputs={ 'photo': image() }, outputs={ 'label': text() })
+ def classify(model, input):
+     img = input['photo']
      img_tensor = preprocess(img)
      img_tensor.unsqueeze_(0)
      img_variable = Variable(img_tensor)
      fc_out = model(img_variable)
      label = labels[str(fc_out.data.numpy().argmax())]
+     return { 'label': label }

+ if __name__ == '__main__':
+     rw.run()
```
<p class='subtitle'>Contents of model.py</p>

Behind the scenes, the Runway Python SDK uses the `@runway.command()` decorator to set up a server with a `/classify` endpoint that accepts a base64-encoded image. The SDK then converts this image into a `PIL.Image` before passing it to the `classify()` function, which classifies it and returns a text label.

<p class="note"><b>NOTE:</b> You don't have to use the Runway Python SDK to set up the server. You can just use any server framework (e.g. Flask) and set up the classification endpoint manually. The SDK just makes things easier by taking care of parsing/serializing inputs/outputs and setting up the endpoints for you.</p>

#### 2. Write a `runway.yml` config file

Next we need to write a config file that defines the environment, dependencies, and build steps required to build and run our model. This file is written in [YAML](https://learnxinyminutes.com/docs/yaml/), a human-readable superset of JSON. Below is an example of the `runway.yml` file for Squeezenet:

```yaml
python: 3.6
cuda: 9.2
entrypoint: python runway_model.py
build_steps:
  - pip install -r requirements.txt
```

This file specifies the Python and CUDA versions to use, the entrypoint command which launches the Runway model and HTTP server, and a build step which installs the Python dependencies required to run our model. See the [Runway YAML reference page](https://sdk.runwayml.com/en/latest/runway_yaml_file.html) for a full list of config values supported in the `runway.yml` config file.

Peeking at the `requirements.txt` file reveals that the only dependencies for the SqueezeNet Runway model are PyTorch and PyTorch Vision, as well as the Runway Model SDK itself.

```
torch==1.0.0
torchvision==0.2.1
runway-python
```

<p class="note">
  <b>NOTE:</b> The <code>runway-python</code> module must always be installed via the <code>build_steps</code>. Failing to install this required dependency via the <code>runway.yml</code> file will cause all model builds to fail.
</p>

#### 3. Upload your code to a GitHub repository

Once your model has a `runway_model.py` and `runway.yml` config file Runway it's time to upload your repository to GitHub. Create a new GitHub repo named `runway-model-tutorial` on your GitHub account.

If you cloned the example `runway/model-squeezenet` repo at the beginning of this tutorial, you reset the remote `origin` to point to your newly created repo instead of the original you cloned from.

```bash
# change the remote "origin" to point to your new repo
git remote set-url origin https://github.com/<YOUR_USERNAME>/runway-model-tutorial
# push the code to your repo
git push origin master
```

#### 4. Import the model

Once you've pushed your model to GitHub, it's time to import your model in the Runway app. Open Runway and select the _Create New Model From GitHub_ button on the lower left.

![Import Model #1](https://runway.nyc3.cdn.digitaloceanspaces.com/documentation/tutorial_model_importing/1_small.png)

Authorize Runway to access public data on your GitHub account.

![Import Model #2](https://runway.nyc3.cdn.digitaloceanspaces.com/documentation/tutorial_model_importing/2_small.png)
<img src="https://runway.nyc3.cdn.digitaloceanspaces.com/documentation/tutorial_model_importing/3_small.png" style="max-width: 50%; margin: auto; display: block;">

Back in the Runway app, select the repository that contains your Runway model; `runway-model-tutorial` in our case.

![Import Model #4](https://runway.nyc3.cdn.digitaloceanspaces.com/documentation/tutorial_model_importing/4_small.png)

Next you can edit the model name and add a category to your model. Other info settings are available to edit later.

![Import Model #5](https://runway.nyc3.cdn.digitaloceanspaces.com/documentation/tutorial_model_importing/5_small.png)

Once you've imported your model, a model build should be triggered automatically. Runway will clone the code from your repository and use its `runway.yml` file to build a Docker image from your model. Select the "Versions" tab in your model page to view all builds, past and present.

![Import Model #6](https://runway.nyc3.cdn.digitaloceanspaces.com/documentation/tutorial_model_importing/6_small.png)

Clicking on a model version to view details about the build. You will notice that the `default` switch is flipped automatically for the first build. This means that the model is now published by your Runway users and available for others to use. You can set any successfully built version to be the `default` version, but you must have at least one default version. This is an intentional decision for the time being, as _Private Models_ is a feature still to come.

![Import Model #7](https://runway.nyc3.cdn.digitaloceanspaces.com/documentation/tutorial_model_importing/7_small.png)

You can view model logs during or after a build to debug your model build process.

![Import Model #8](https://runway.nyc3.cdn.digitaloceanspaces.com/documentation/tutorial_model_importing/8_small.png)

