# Use Models in RunwayML

## Overview
RunwayML is a platform for publishing and creating with open source [machine learning models](/?id=what-is-machine-learning). 

There are many types of machine learning models. For creative purposes, we can start to categorize them into three broad types: models that identify objects or people, models that transform content, and models that generate new media from the training data. 

This guide will cover:
* how to find models to use in RunwayML 
* how to find their published attributes
* how to set them up, run them, and stop them 

<div id="video-container">
<iframe width="560" height="515" src="https://www.youtube.com/embed/J4FQGYI9gpQ" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

## Find Models
Use RunwayML's **Model Directory** to search for and discover machine learning models with specific attributes, functionalities, or by the names of those who published the models on the platform. 

<div id="video-container">
<iframe width="560" height="515" src="https://www.youtube.com/embed/ePIRExcanjg" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>


## Model Information
Models published on the RunwayML platform include the following information on their overview pages. If you [add a model](how-to/import-models) to RunwayML, you have access to sections that are private ( 🔒) and not public to other users.

| Attribute| Description | 
| :--- | :--- | 
| Title | The name of the model. | 
| Overview | A quick description of the model and how it works, often copied directly from the abstract of the model's research paper. If you are the publisher of the model, then you can edit this information directly. | 
| Versions | 🔒 When you add models to RunwayML via our [GitHub integration](how-to/import-models?id=_3-upload-your-code-to-a-github-repository) and push updates to your repository, RunwayML builds a new version of your model every time. You can see a list of all your versions, switch between different ones, and select the default. Take a look at the [Model SDK](https://sdk.runwayml.com/en/latest/) to learn more about model versioning.| 
| Files | 🔒 As a model publisher on the RunwayML platform, you can associate checkpoints, files, and other related files, such as a model's weights. In order to activate the Files tab, you'll need to define a `category` type in the `runway_model.py,` i.e.: `category(choices=["day", "night"]).` Check the [category type in the SDK](https://sdk.runwayml.com/en/latest/data_types.html?highlight=choices#data-types) for more information. | 
| Gallery | A image gallery where with associated images. | 
| Templates | A quick start template guide for models - coming soon! | 
| License | Every model in RunwayML is licensed for a specific type of use. Some of the models' outputs may be restricted to non-commercial purposes. **Be sure to check a model's license before using it!**  | 
| Settings | 🔒 Any settings for the model. | 
| Publishers  |  The users who added the model to RunwayML.  | 
| Attributions  |  The designers, developers, researchers and institutions that created the model.  | 
|  Characteristics  | These include when the models was published on the RunwayML platform, when it was last updated, input and output types, file size, support for CPU and GPU, and license name. | 
| Keywords   |  Keywords describing the model.  | 
|  Performance Notes  |  How the model performs (inference time, etc).  | 
|  Code, Paper and More  | Links to external sites containing the code of the model and its research paper. |

![versions](assets/images/views/model.jpg)


## Workspaces
A **Workspace**, pictured in the left sidebar below, is a place to collect and organize models. By adding models to workspaces and grouping them together, perhaps by project or theme, you can experiment and create in ways logical to you.

![Input/Output View](assets/images/views/io.jpg)


## Model Inputs
The Input section allows you to change the type of input used for a specific model. Supported inputs include:

| Input     | Supported Types | Description  |
|------------|-----------------| ------------------|
| Camera     | image           | Use frames from the webcam stream as input        |
| Text       | text            | Free-from text input                              |
| File       | all types       | Use a supported file type                         |

## Model Outputs
The Output section allows you to change the type of input used for a specific model. 

Supported outputs include:

| Output     | Description
|------------|---------------|
| Local      | Preview the model output inside Runway                              |
| File       | Stream the model output into a file using supported formats         |

?> Every model in RunwayML is licensed for a specific type of use.  Some of the models' outputs may be restricted to non-commercial purposes. Be sure to check the model's license on its overview page.

Currently, we don't offer control over the size of the images output from models. This is because each model imposes its own restrictions on image sizes. These restrictions are largely due to the current state-of-the-art algorithms that process images using machine learning. (But you can use the ESRGAN image-upscaling model to synthetically upscale the output by 4X.)

Related Technical Support Resource: [Output Image Dimensions](https://support.runwayml.com/en/articles/3069430-output-image-dimensions)


## Model Options
Each model has a set of options that you can change and update.


## Run Models
Depending on the model, there are several ways to run models in RunwayML: 
1. [Run Models with Local CPU](how-to/use-models?id=run-models-with-local-cpu)
1. [Run Models with Local GPU (Linux Only)](how-to/use-models?id=run-models-with-local-gpu-linux-only)
1. [Run Models with Remote GPU](/how-to/use-models?id=run-models-with-remote-gpu) in RunwayML's cloud infrastructure


<div id="video-container">
<iframe width="560" height="515" src="https://www.youtube.com/embed/db1USOwbRPQ" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

### Run Models with Local CPU
To run models locally, you need to download and install them individually. 

Some **local** models require you to install [Docker](https://www.docker.com/). Docker CE is a free and open-source software. You **do not** need Docker to run models remotely! If you need to install Docker, here are the steps:

#### **Step 1: Download and install Docker from the following links:** 
* [Mac](https://download.docker.com/mac/stable/Docker.dmg)
* [Windows](https://download.docker.com/win/stable/Docker%20for%20Windows%20Installer.exe)
* [Linux](https://docs.docker.com/install/linux/docker-ce/ubuntu/)

?> Docker for Windows requires Microsoft Hyper-V, which is supported only in the Pro, Enterprise, or Education editions of Windows. If you don't have a Pro, Enterprise ,or Education Windows edition then you will not be able to install Docker, and you can only run some RunwayML models. 

#### **Step 2: Once Docker is installed and running, you should see the following:**

**On Mac**: a Docker icon in the top status bar. This indicates that Docker is running and accessible from Runway. Please refer to [this official Docker](https://docs.docker.com/docker-for-mac/install/#install-and-run-docker-for-mac) installation guide on Mac if you are having any issues.

<div class="Img-Small">
  <img src="https://runway.nyc3.digitaloceanspaces.com/documentation/docker-bar-mac.png" alt="Docker Icon mac" >
  <p>A whale in the top status bar indicates that Docker is running.</p>
</div>

**On Windows**: a Docker icon in the bottom notifications area. This indicates that Docker is running and accessible from RunwayML. If you encounter any issues with Docker on Windows, please check that your Windows Firewall is not affecting Docker. Also, be sure that Windows has at least one Share Drive with Docker. Please refer to [this official Docker](https://docs.docker.com/docker-for-windows/) installation guide on Windows if you continue to have any issues.

<div class="Img-Small">
  <img src="https://runway.nyc3.digitaloceanspaces.com/documentation/docker-bar-windows.png" alt="Docker Icon mac" >
  <p>Docker icon in the Notifications area or System tray. </p>
</div>

**On Linux**: verify if docker is installed and running with the following command: `docker --help`

#### **Step 3: RunwayML will notify you if Docker is running or not:**
 In the bottom status bar inside RunwayML, look for a whale icon and a message that that Docker is available:

<div class="Img-Small">
  <img src="https://runway.nyc3.digitaloceanspaces.com/documentation/docker-available-Runway.png" alt="Docker Icon mac" >
  <p>A whale icon in the bottom status bar inside RunwayML.</p>
</div>

If Docker is not installed, unavailable, or not running you will see the following message:

<div class="Img-Small">
  <img src="https://runway.nyc3.digitaloceanspaces.com/documentation/docker-unavailable-Runway.png" alt="Docker Icon mac" >
  <p>If Docker is not available, RunwayML will show a "Docker Unavailable" message in the bottom status bar.</p>
</div>

?> **Increase Docker's Memory Limit:** Several models require a significant amount of memory in order to run properly. By default, Docker allocates a maximum of 2 GB of memory to run models. Some RunwayML models exceed that, which may lead to errors. Without enough memory models, may misbehave or fail silently without a helpful error message. To prevent that, you need to increase Docker's memory limit. Follow the steps in this related technical support article: [Docker Errors. Having trouble with Docker? Here are few tips.](https://support.runwayml.com/en/articles/3069033-docker-errors)

---
Related Technical Support Resources:
* [Changing Where Local Models are Downloaded](https://support.runwayml.com/en/articles/3203817-changing-where-local-models-are-downloaded)
* [Deleting Local Models](https://support.runwayml.com/en/articles/3077861-deleting-local-models)
* [Docker Errors. Having trouble with Docker? Here are few tips.](https://support.runwayml.com/en/articles/3069033-docker-errors)



### Run Models with Local GPU (Linux Only)


---
Related Technical Support Resources: 
* [Local GPU](https://support.runwayml.com/en/articles/3140813-local-gpu)
* [Deleting Local Models](https://support.runwayml.com/en/articles/3077861-deleting-local-models)
* [Running Docker without sudo](https://support.runwayml.com/en/articles/3359183-running-docker-without-sudo)


### Run Models with Remote GPU
Running a model with remote GPU [uses credits](https://support.runwayml.com/credits-and-plans/how-much-does-runway-cost), but the model runs much faster than when using your computer's local CPU.

---
Related Technical Support Resources: 
* [Remote GPU](https://support.runwayml.com/en/articles/3059347-remote-gpu)
* [How Much Does RunwayML Cost?](https://support.runwayml.com/en/articles/3000086-how-much-does-runwayml-cost)
* [Adding Credits](https://support.runwayml.com/en/articles/2984968-adding-credits)
* [Redeeming Coupon Codes](https://support.runwayml.com/en/articles/3047429-redeeming-coupon-codes)


## Stop Models

---
Related Technical Support Resources: [Stopping Your Model](https://support.runwayml.com/en/articles/3037580-stopping-your-models)