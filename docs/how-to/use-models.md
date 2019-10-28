# Use Models in RunwayML

## Overview
RunwayML is a platform for publishing and creating with open source [machine learning models](/?id=what-is-machine-learning). There are many types of machine learning models. For creative purposes, we can start to categorize them into three broad types: models that identify objects and people, models that transform content, and models that generate new media from the training data. 

This guide will cover:
* How to find models in RunwayML 
* How to find their published attributes
* How to set them up, run them, and stop them 

<div id="video-container">
<iframe width="560" height="515" src="https://www.youtube.com/embed/J4FQGYI9gpQ" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

## Step 1: Find Models
Use RunwayML's **Model Directory** to search for and discover machine learning models with specific attributes, functionalities, or by the names of those who published the models on the platform. 

<div id="video-container">
<iframe width="560" height="515" src="https://www.youtube.com/embed/ePIRExcanjg" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>


## Step 2: Model Information
Models published on the RunwayML platform include the following information on their overview pages, accessible by clicking **Learn More** in the Model Directory. If you [add a model](how-to/import-models) to RunwayML, you have access to sections that are private ( 🔒) and not public to other users.

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


## Step 3: Add Models to Workspaces
A **Workspace**, pictured in the left sidebar below, is a place to collect and organize models. By adding models to workspaces and grouping them together, perhaps by project or theme, you can experiment and create in ways logical to you.

![Input/Output View](assets/images/views/io.jpg)


## Step 4: Set Inputs
When a model is running, it accepts input and produces an output. Different types of models accept different types of input. The Input section allows you to change the type of input used for a specific model. Supported inputs include:

| Input     | Supported Types | Description  |
|------------|-----------------| ------------------|
| Camera     | Image           | Use frames from the webcam stream (video) as input        |
| Text       | Text            | Free-from text input                              |
| File       | All Types       | Use a supported file type indicated i the app for that model                        |

## Step 5: Set Outputs
The Output section allows you to change the type of input used for a specific model. Different types of models produce different types of outpout. Supported outputs include:

| Output     | Description
|------------|---------------|
| Local      | Preview the output inside of the app                              |
| File       | Stream the output into a file using supported formats indicated in the app for that model        |

?> __Check the Model's License:__ Every model in RunwayML is licensed for a specific type of use.  Some of the models' outputs may be restricted to non-commercial purposes. Be sure to check the model's license on its overview page.

?> __Image Output Size:__ Currently, we don't offer control over the size of the images output from models. This is because each model imposes its own restrictions on image sizes. These restrictions are largely due to the current state-of-the-art algorithms that process images using machine learning. (But you can use the ESRGAN model to upscale images by 4X.)

Related Technical Support Resource: [Output Image Dimensions](https://support.runwayml.com/en/articles/3069430-output-image-dimensions)


## Step 6: Adjust Options
Each model has a set of options, located in the right sidebar, that you can modify. These options will vary depending on the model. Sometimes options must be set *before* selecting the type of model input.  


## Step 7: Run Models

<div id="video-container">
<iframe width="560" height="515" src="https://www.youtube.com/embed/db1USOwbRPQ" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

Depending on the model, there are several ways to run models in RunwayML:

### Run Models with Local CPU
To run models locally, you need to download and install them individually. Some **local** models require you to install Docker. Docker CE is a free and open-source software. Follow the steps in this guide to [Install Docker](how-to/run-models-locally.md) to run models locally.

?> __Note:__ You do not need Docker to run models remotely! 

Related Technical Support Resources:
* [Changing Where Local Models are Downloaded](https://support.runwayml.com/en/articles/3203817-changing-where-local-models-are-downloaded)
* [Deleting Local Models](https://support.runwayml.com/en/articles/3077861-deleting-local-models)
* [Docker Errors. Having trouble with Docker? Here are few tips.](https://support.runwayml.com/en/articles/3069033-docker-errors)



### Run Models with Local GPU (Linux Only)
If you are running RunwayML on Linux, follow this guide to [use your own GPU hardware](how-to/local-gpu). 

Related Technical Support Resources: 
* [Local GPU](https://support.runwayml.com/en/articles/3140813-local-gpu)
* [Deleting Local Models](https://support.runwayml.com/en/articles/3077861-deleting-local-models)
* [Running Docker without sudo](https://support.runwayml.com/en/articles/3359183-running-docker-without-sudo)


### Run Models with Remote GPU
Running a model with Remote GPU [uses credits](https://support.runwayml.com/credits-and-plans/how-much-does-runway-cost), but the model runs much faster than when using your computer's local CPU. Some models are only available for Remote GPU and not available to download locally.

Related Technical Support Resources: 
* [Remote GPU](https://support.runwayml.com/en/articles/3059347-remote-gpu)
* [How Much Does RunwayML Cost?](https://support.runwayml.com/en/articles/3000086-how-much-does-runwayml-cost)
* [Adding Credits](https://support.runwayml.com/en/articles/2984968-adding-credits)
* [Redeeming Coupon Codes](https://support.runwayml.com/en/articles/3047429-redeeming-coupon-codes)


## Step 8: Stop Models
**Manually Stop Models:** Click the **Stop button** in the bottom right corner of the app. 

**Automatic Stop:** Please note that we stop all running models after 10 minutes of inactivity. 

**Stop All Running Models in Your Settings:** If you're not able to stop a model with the Stop button, you can use the **Stop All Running Models** in your Settings view. 

**Quitting The App While Models Are Running:** If you quit RunwayML while a model is running, you will be prompted to confirm your action. You can then choose to continue running your models or quit the app and stop all running models. 

Related Technical Support Resource: [Stopping Your Model](https://support.runwayml.com/en/articles/3037580-stopping-your-models)