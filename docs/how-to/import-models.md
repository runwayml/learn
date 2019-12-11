# Add Models to RunwayML

## Overview
RunwayML models are platform-agnostic; models written in any framework/language can be used by RunwayML as long as the model can be made accessible via an HTTP server. This process, however, is easiest in Python where we provide an SDK for parsing the inputs to the model, serializing its outputs, and setting up the server environment.

A RunwayML model consists of an HTTP server that exposes a common interface over a network and a configuration file that specifies dependencies and build steps for running that server (and your model code) inside a Docker container. Both the network interface for interacting with the model and the Docker images created as a result of the configuration file are abstracted from the developer using the [RunwayML Model SDK](https://sdk.runwayml.com).

Here are the steps involved in porting an ML model written in Python to RunwayML:

1. Create a `runway_model.py` file which implements several methods from the [RunwayML Model SDK](https://sdk.runwayml.com).
2. Write a `runway.yml` config file.
3. Upload your code to a GitHub repository.
4. Import your new model into RunwayML using your GitHub account.
5. Push new commits to your GitHub repo to trigger new model versions to be built and published on RunwayML.
6. Add additional information to your model.
7. (Optional) Add files to your model.
8. (Optional) Make your model public!

Once you've imported your model into RunwayML using your GitHub account, each `git push` will trigger the latest version of your code to be built and optionally deployed publicly through RunwayML.

## Tutorial 1: Adding Models to RunwayML
This is a [two-part video series](https://www.youtube.com/playlist?list=PLj598ZXODDO_YUkKaBK9yBgIhOlPia_eL) with Gene Kogan:
<div id="video-container">
<iframe width="560" height="515" src="https://www.youtube.com/embed/m5EhZR9SFvc" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

## Tutorial 2: Importing the SqueezeNet Model
In this tutorial, we will demonstrate how to port the [SqueezeNet](https://arxiv.org/abs/1512.03385) computer vision model to RunwayML. We also provide a [RunwayML Model Template](https://github.com/runwayml/model-template) repository that contains boilerplate code for porting a new model.

We recommend forking the [`runwayml/model-squeezenet`](https://github.com/runwayml/model-squeezenet) GitHub repository to your own GitHub user account so that you can follow along with the tutorial.

### Step 1. Create a `runway_model.py` model server file

SqueezeNet is a neural network architecture used for computer vision tasks, optimized for mobile/embedded devices. [PyTorch](https://github.com/pytorch/vision) includes an implementation of SqueezeNet pre-trained on ImageNet that can be used out-of-the-box for object recognition.

Here's the code to classify a single local image (via a hard-coded path) with pre-trained SqueezeNet:

```python
# runway_model.py
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

And here's the modified code for the same model wrapped in a server so that RunwayML can access it:


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
+     runway.run()
```
<p class='subtitle'>Contents of model.py</p>

Behind the scenes, the RunwayML Python SDK uses the `@runway.command()` decorator to set up a server with a `/classify` endpoint that accepts a base64-encoded image. The SDK then converts this image into a `PIL.Image` before passing it to the `classify()` function, which classifies it and returns a text label.

<p class="note"><b>NOTE:</b> You don't have to use the RunwayML Python SDK to set up the server. You can just use any server framework (e.g. Flask) and set up the classification endpoint manually. The SDK just makes things easier by taking care of parsing/serializing inputs/outputs and setting up the endpoints for you.</p>

#### Testing your `runway_model.py` locally

Before you configure your build environment and add your model to RunwayML, you should test it locally to make sure that it works as expected. Using RunwayML's Develop Mode, you can connect directly to your model server in order to test your model before building it remotely. Open your command line and type:

```bash
## Optionally create and activate a Python 3 virtual environment
# virtualenv -p python3 venv && source venv/bin/activate

pip install -r requirements.txt

# Run the entrypoint script
python RunwayML_model.py
```

You should see an output similar to this, indicating your model is running.

```
Setting up model...
Starting model server at http://0.0.0.0:9000...
```

You can now open RunwayML, and click the "From Server" button under "Create New Model."

![Click "From Server"](assets/images/how-to/github-link/from-server.png)

Choose a name for your workspace, and click "Create." 

After making sure that the Port under Server Options matches the port that your model server is running at, click "Connect" to connect to your model server.

![Connect to model server](assets/images/how-to/github-link/dev-model-connect.png)

You can now interact with your model using RunwayML. For example, try dragging an image in the Input area to see your model classify it:

![Classify using your model server](assets/images/how-to/github-link/dev-model-classify.png)

Once you've confirmed your model works correctly locally, you can create a `runway.yml` config file before building the model remotely with RunwayML + GitHub.

### Step 2. Write a `runway.yml` config file

Next you need to write a config file that defines the environment, dependencies, and build steps required to build and run our model. This file is written in [YAML](https://learnxinyminutes.com/docs/yaml/), a human-readable superset of JSON. Below is an example of the `runway.yml` file for Squeezenet:

```yaml
python: 3.6
cuda: 9.2
entrypoint: python runway_model.py
build_steps:
  - pip install -r requirements.txt
```

This file specifies the Python and CUDA versions to use, the entry point command which launches the RunwayML model and HTTP server, and a build step which installs the Python dependencies required to run our model. See the [RunwayML YAML reference page](https://sdk.runwayml.com/en/latest/runway_yaml_file.html) for a full list of config values supported in the `runway.yml` config file.

Peeking at the `requirements.txt` file reveals that the only dependencies for the SqueezeNet RunwayML model are PyTorch and PyTorch Vision, as well as the RunwayML Model SDK itself.

```
torch==1.0.0
torchvision==0.2.1
runway-python
```

<p class="note">
  <b>NOTE:</b> The <code>runway-python</code> module must always be installed via the <code>build_steps</code>. Failing to install this required dependency via the <code>runway.yml</code> file will cause all model builds to fail.
</p>

### Step 3. Upload your code to a GitHub repository

Once your model has a `runway_model.py` and `runway.yml` config file it's time to upload your repository to GitHub. If you forked the `runway/model-squeezenet` repo at the beginning of this tutorial, you should already have a `git remote` that points to the forked repository on your GitHub user account. If you instead cloned the repo, or you started creating a model from scratch instead of using the `runwayml/model-squeezenet` repo, you should publish your code to GitHub as an open source repository now. For the remainder of this tutorial, we will assume the repository being ported is located at `https://github.com/YOUR_USERNAME/runway-model-tutorial`.

### Step 4. Import the model

Once you've pushed your model to GitHub, it's time to import your model in the RunwayML. Open RunwayML and select the _Create New Model From GitHub_ button on the lower left.

![Import Model #1](assets/images/views/model-directory.png)

Authorize RunwayML to access public data on your GitHub account.

![Import Model #2](assets/images/how-to/github-link/github-01.png)

Back in RunwayML, select the repository that contains your RunwayML model; `runway-model-tutorial` in our case.

![Import Model #4](assets/images/how-to/github-link/github-03.png)

### Step 5. Push a new commit to trigger a build

Once you've imported your model to RunwayML, you must push a new commit to GitHub to trigger a model build. When you do so, RunwayML will clone the code from your repository and use its `runway.yml` file to build a Docker image from your model. Each new commit pushed to the `master` branch of GitHub repository linked to a model will trigger a new model version to be built by RunwayML. Select the "Versions" tab in your model page to view all builds, past and present.

![Import Model #6](assets/images/how-to/github-link/model-versions.png)

Click on a model version to view details about the version builds. You will notice that the `default` switch is flipped automatically for the first build. This means that the model is now published by your RunwayML users and is available for others to use. You can set any successfully built version to be the `default` version, but you must have at least one default version. This is an intentional decision for the time being, as _Private Models_ is a feature that is still to come.

![Import Model #7](assets/images/how-to/github-link/logs.png)

You can view model logs during or after a build to debug your model build process.

![Import Model #8](assets/images/how-to/github-link/logs2.png)

Once a model version has been successfully built you can add it to a workspace. You can also add any successful model versions to your personal workspace by hovering over the model version check mark in the "Versions" panel until it becomes a "+" icon, and then selecting it. This allows you to test new model versions before making them the default model version that is published to all RunwayML users.

### Step 6. Add information to your model

Once you've imported your model, you can add additional information to help others understand the model. As the publisher of the model, you can do this from the model page using the **Edit Info** button. We recommend adding these fields for your model:

* **Model Name**: The name of the model. Alphanumeric values, underscores, and hyphens are allowed here. No spaces.
* **Tagline**: A short one-line description of what your model does.
* **Description**: A long description of what your model does. The description can be a paragraph or more and is interpreted as Markdown.
* **Images**: A collection of images showcasing your model. The first image you add in the "Gallery" tab will be used as the thumbnail for the image.
* **Attributions**: A list of names and respective roles for people or organizations that significantly contributed to a model. This usually includes authors or publishers of machine learning papers or frameworks. Be generous with attributions; give credit where credit is due. We intentionally differentiate between a model publisher (the RunwayML user that adds/publishes a model) and the original authors of the model code or paper. This provides flexibility and encourages remix, experimentation, and "forking" of models.
* **LICENSE**: The license defining how the model can be used.
* **Keywords**: A list of tags that can be used to find your model in RunwayML.
* **Performance Notes**: How can users expect the model to perform on GPU or CPU environments?
* **Code, Paper, and More**: A list of links to resources related to your model, such as source code, arXiv papers, blog posts, or more.

### Step 7. (Optional) Add files to your model

Some models may require files that are too large to include in the Github repository, such model checkpoints. RunwayML provides a space to upload large files to include with your model. 

To upload a model file, you need to specify a setup option in `runway_model.py` that has the [`runway.file`](https://sdk.runwayml.com/en/latest/data_types.html#runway.data_types.file) data type. For instance, if your model supports loading checkpoints in a Python pickle format (`.pkl`), you can add a setup option to your model for accepting pickle files in the following way:

```python
# runway_model.py
@runway.setup(options={'checkpoint': runway.file(extension='.pkl')})
def setup(opts):
   checkpoint_path = opts['checkpoint']
   model = load_model_from_checkpoint(checkpoint_path)
   # ...
```

Once you've added a file option to your model and built your model successfully, you can upload files to associate with that option by selecting the "Files" tab in your model page and clicking "Upload File."

![Import Model #9](assets/images/how-to/github-link/model-files.png)

(If you are seeing a "No File Options in Model" message, that means that you either have not added a `file` option, or your model has not built successfully since you added the option. Check the "Versions" tab to see the status of your builds.)

Click "Choose File..." and select the file you want to upload, provide a name for your file, and click "Upload File" to start the uploading process.

![Import Model #10](assets/images/how-to/github-link/model-file-dialog.png)

Once you have uploaded your file, you can now use that file with your model in RunwayML. Add your model to your workspace, and your file should appear in Options on the right hand side:

![Import Model #11](assets/images/how-to/github-link/file-in-options.png)

### Step 8. (Optional) Make your model public!

Once you've successfully built and tested your model, and are satisfied with its results, you can make the model public, allowing anyone in the RunwayML community to use it and make projects with it! 

To make your model public, select the "Settings" tab in your model page, and click on the "Make Public" button.

![Import Model #12](assets/images/how-to/github-link/make-public.png)

## Tutorial 3: Importing the Progressive Growing of GANs (PGAN) Model

This tutorial is posted on the RunwayML Medium blog: [Porting a machine learning model from GitHub to RunwayML in 5 minutes](https://medium.com/runwayml/porting-a-machine-learning-model-from-github-to-runway-in-5-minutes-555c5c9310af)

## RunwayML Python SDK
Developer documentation for the Python SDK to import models: [RunwayML Model SDK Docs](https://sdk.runwayml.com)

## RunwayML Model Template
A boilerplate model template that you can use as a starting point to import models: [RunwayML Model Template](https://github.com/runwayml/model-template)



---
Related Technical Support Resource: [Add Your Own Models](https://support.runwayml.com/en/articles/3037632-add-your-own-models)

