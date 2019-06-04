# Overview

In this quick overview, we will help you get familiar with Runway, will explain how the interface works and how you can start using powerful machine learning models with a few simple clicks!

## Start Screen

Every time you open Runway you will see the **Start Screen**. From here, you can choose to **Browse Models** or restore a previous **Workspace** from another session. (Read more on workspaces [here](getting-started/views.md)).

![Runway Welcome View](assets/images/views/start-screen.png)

## Models Directory

Runway's Models Directory is a unique place to search, discover, publish and install machine learning models. You can search for models with specific attributes, input types, creator, functionality or by date.

![Models Directory](assets/images/views/model-directory.png)

## Model View

Every model in Runway has its own view. Inside a model view you can learn more about the model, authors, specifications and characteristics, examples, license, and more.

![versions](assets/images/views/model.png)

Each model view is compromised of two main sections:

1) **Tabs Section**

The Tabs Sections allows you to quickly switch between different elements of a model. If you port a model to Runway, you'll have access to sections that are private ( 🔒) and not public to other users. The current Tabs Sections include:

<!-- tabs:start -->

#### **Overview**

The Overview tabs provides you with a quick overview and description of the model. This is a place to specify and learn more about what the model does and how it works. If you are the owner of the model you are able to edit this information directly from the view.

#### **Versions 🔒**

When you add models to Runway via our [GitHub integration](/how-to/importing?id=connect-to-github) and push updates to your repository, Runway builds a new version of your model every time. In this version tab, you can see a list of all your versions, switch between different version of the model and select your default version.

Take a look at the [Model SDK](https://sdk.runwayml.com/en/latest/) to learn more about model versioning.

#### **Files 🔒 **

You can associate checkpoints, files, and other related files relating a model, such as models weights. In order to activate the Files tab, you'll need to define a `category` type in the `runway_model.py`, ie: `category(choices=["day", "night"])`. [Check the category type in the SDK](https://sdk.runwayml.com/en/latest/data_types.html?highlight=choices#data-types) for more information.

#### **Gallery**

A image gallery where you can associate images to your model.


#### **Templates **

A quick start template guide for models. (Coming soon!)


#### **License**

The model license.


#### **Settings 🔒 **

Settings for the model.

<!-- tabs:end -->

2) **Model Side Bar:** The model side-bar provides you further information.

<!-- tabs:start -->

#### **Publishers**

The user who added the model to Runway.

#### **Attributions**

The designers, developers, researchers and institutions that created the model.

#### **Characteristics**

A resume table with information about the model.

#### **Keywords**

Keywords describing the model.

#### **Performance Notes**

How the model performs (inference time, etc).

#### **Code, Paper and More**

Links to external sites.

<!-- tabs:end -->

## Workspaces

Runway is logically organized in a hierarchy of **Workspaces** and [**Models**](getting-started/model-101.md). **Workspaces** provides a way to logically group models used into the same project. For example, a creator working on an interactive dance performance may create a workspace containing two models that she would like to use for her piece: OpenPose for detecting the dancers’ movements and WaveNet for generating a score for the dance.

A **Workspace** is a collection of models. In a **Workspace** you can organize your models by theme, hierarchy, or however else you like.

?> **Remember:** A Workspace is a collection of AI models. By grouping models together you can experiment and create with models in a way that's logical to you.

![Input/Output View](assets/images/views/io.png)

1) **Workspaces and Models**: This sidebar contains and list all current workspaces and models in use.

2) **Input**: The Input section allows you to change the type of input used for a specific model. Supported inputs include:

| Input      | Supported Types | Description                                       |
|------------|-----------------|---------------------------------------------------|
| Camera     | image           | Use frames from the webcam stream as input        |
| Text       | text            | Free-from text input                              |
| File       | all types       | Use a supported file type                         |

3) **Output**: The Output section allows you to change the type of input used for a specific model. Supported outputs include:

| Output     | Description
|------------|---------------------------------------------------------------------|
| Local      | Preview the model output inside Runway                              |
| File       | Stream the model output into a file using supported formats         |


4) **Options**: Each model has a set of options that you can change and update. These are often known as hyperparameters.

5) **Run/Stop & Install**: This button will allow you to start and stop your models. Learn more about [running a model](how-to/run-a-model.md)

## Settings

The **Settings** view has your account details, remaining credits, locally installed models and checkpoints as well and information about Runway.

![Input/Output View](assets/images/views/settings.png)