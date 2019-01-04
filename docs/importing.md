# Importing Models into Runway

<p class='note'><b>Note</b>: The importing functionality will be enabled in the next version of the beta.</p>

A Runway Model consists of a Docker image serving a machine learning algorithm, and a specification that includes instructions for how to run that Docker image (e.g. entrypoint command, server port, inputs/outputs) and relevant metadata (e.g. author, paper, Github repo). 

Runway is platform-agnostic; models written in any framework/language can be used by Runway as long as the model can be made accessible in an HTTP server. The process however is easiest in Python where we provide an SDK for parsing the inputs to the model, serializing its outputs, and setting up the server.

Here are the steps involved in porting an ML model into Runway:

1. Create a model server
2. Wrap the model server and its dependencies in a Docker container
3. Write a specification JSON file that points to the Docker container and also contains input/output datatype information, so that Runway knows how to interact with the model
4. Import the model into the Runway app

### Example: Importing SqueezeNet into Runway

#### 1. Create a model server

[SqueezeNet](https://arxiv.org/abs/1512.03385) is a neural network architecture used for computer vision tasks, optimized for mobile/embedded devices. [PyTorch](https://github.com/pytorch/vision) includes an implementation of SqueezeNet pretrained on ImageNet that can be used out-of-the-box for object recognition.

Here's the code to classify a single local image (via hard-coded path) with pretrained SqueezeNet:

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

# initialize the model and download pretrained weights 

model = models.squeezenet1_1(pretrained=True)

# open a local iamge
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
# model.py 

import json
from PIL import Image
from torchvision import models, transforms
from torch.autograd import Variable
+ from runway import RunwayServer

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

model = models.squeezenet1_1(pretrained=True)

+ rw = RunwayServer()

+ @rw.command('classify', inputs={'photo': 'image'}, outputs={'label': 'text'})
+ def classify(input):
+  img = input['photo']
   img_tensor = preprocess(img)
   img_tensor.unsqueeze_(0)
   img_variable = Variable(img_tensor)
   fc_out = model(img_variable)
   label = labels[str(fc_out.data.numpy().argmax())]
+  return {'label': label}

+ if __name__ == '__main__':
+     rw.run()
```

Behind the scenes, the Runway Python SDK sets up a server with an endpoint `/classify` accepting a base64-encoded image, which it then converts into a `PIL.Image` before passing it to the `classify()` function.

<p class="note"><b>NOTE:</b> You don't have to use the Runway Python SDK to set up the server. You can just use any server framework (e.g. Flask) and set up the classification endpoint manually. The SDK just makes things easier by taking care of parsing/serializing inputs/outputs and setting up the endpoints for you.</p>

#### 2. Wrap the model server and its dependencies in a Docker container

Runway uses Docker to bundle up all of a model's dependencies and make them portable across platforms/setups.

There are already official PyTorch images available on Dockerhub, so we'll just use those as a starting point for our image, and simply install the Runway SDK, copy `model.py` and `labels.json` over to the container, and start the server.

Here's our `Dockerfile`: 

```dockerfile
FROM pytorch/pytorch:v0.2

RUN pip install runway-python

WORKDIR /root

COPY . .

CMD python model.py
```

To build the docker image:

```bash
$ docker build -t agermanidis/squeezenet .
```

We can try running the image to make sure it works:

```bash
$ docker run --rm -it agermanidis/squeezenet
...
 * Running on http://0.0.0.0:8000/ (Press CTRL+C to quit)
```

(Optional) If we want others to be able to use the model, we can publish the image to Docker Hub:

```bash
$ docker publish agermanidis/squeezenet
```

#### 3. Write a specification JSON file

Next we need to write a specification file that will allow Runway to interact with the model. This will include a reference to the Docker image that we just created, information about what input the model expects, what output it produces, and other information (description, license, etc).

We can write it by hand, or [use a JSON schema editor](https://json-editor.github.io/json-editor/?schema=N4IgLglmA2CmIC4QCUDqACAsgewCa2nQBFYAzCAOygmwpABpwBPAB3iWwCMArWAYzAMQ+clUi0AzolABlAK4sW2AE5hYuACqtYUhAG0QEALYBDAObxGJubhpC1AD0GMAbvzAqh3CbRABdRgAxCAJcaWY2RBAuXgEhZVgARzkIBLD9EAoTI0sI+ACQFmVsNlUQ3VAsnPCwbSiJMGVKMxAAX0ZayIRQTvYQBqaKFvbhHT4mlnE6brz6xua2xiNKGrqkCjkjTlhlRZBTB1WuzM3t3ZGG2BYjvo2tnbbWkeDQitmkE2VlEyYhKFgjG8ACQJUhRADEAHoRJRqJJIS9oGEnkEQkiAIJfH43KIxdzxJIpNKIAyfb5MADyYIKRRKO0gOnCZJ+VPCtFgrP0oBBZAh0LIsKmEgRaOR9G5oL5MLENAowsRuCkrT8TxGAGFsEZTBRcCRRHDpj01tEePjGAlkql1CTMtlcpQWHIwFJGNgnY7nf5GLTSgy3lV2EbjgMFiMHU63r0oszfox/oC2RQOWCuSAeSmQFDpQb5aLFhLeUgswKZfCFZjyW0VSM3WAPZHjTG/moEzN2Zy9AWM8X9UKRaF82nJUX+b3ZbnQhXscrVSiQBaidaMgGhG5lBJZUJ8BJxhBJrKZAALFTOUY7iZTAAytBajHGsBMHl2jGgED4sDluVw2D4AGsdgAkqYFguiAfCatqipeoUxS+uU4QrjMUZICGQx7GuG6+EhxqocMjDbru+60EeJ44ih8xoSMBEXrK15odhwYUXhYEJI+ngMX0uF7K+76fmR/RMXs35/oBwGMjMPr0vBMx8I6/FcSMZhyRxcyDMMc7Cf+ygUkRcrhJJZTiaASiqPxlBqBYz6jKQ1jQIICAABwAAwuaqrq6Q2xxNnGLbAsOmajoK479kijx3hBJg6p5fTeYYvnhOmUoljmkIalqkW6slUyPE8QAA==&value=N4IgdghgtgpiBcIQBoQDcYCcDOBLA9mAkqgCYzYDGmuADgC4FgDKAFvpvcSiOVTQyYAZQgHNuqajAj0OEkABtclGGGxxEPUvkoBrLAEkoEURQTAAvpPxRjYUtgQBtALoWgA=&prompt_before_delete&theme=bootstrap2&iconlib=fontawesome4&object_layout=normal&show_errors=interaction).

Here's a barebones specification for our SqueezeNet model (saved to `runway.json`):

```json
{
  "name": "SqueezeNet",
  "version": "0.1",
  "publisher": "Anastasis Germanidis",
  "license": "MIT",
  "dockerImages": {
    "cpu": "agermanidis/squeezenet"
  },
  "commands": [
    {
      "name": "classify",
      "inputs": [
        {
          "name": "photo",
          "type": "image"
        }
      ],
      "outputs": [
        {
          "name": "label",
          "type": "text"
        }
      ]
    }
  ]
}
```

#### 4. Import the model

We are now ready to import our new model into the Runway app. Open the Runway app, then go to the Models Directory.

![step 1](https://i.imgur.com/ZK27Dm7.png)

Click the "Import Model" button and select your `runway.json` file.

![step 2](https://i.imgur.com/6gSBwnU.jpg)

Runway automatically discovers the local Docker image, so it should appear in the Installed models in the sidebar. We can go ahead and add it to a workspace to start using it (we can additional information in the specification later so it's not so empty 🙂)

![step 3](https://i.imgur.com/YxRP2LMr.png)

Finally, we can use SqueezeNet within Runway to classify our images!

![step 4](https://i.imgur.com/IUF8HxT.jpg)