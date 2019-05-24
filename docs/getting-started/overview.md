# Overview

In this quick overview, we will help you get familiar with Runway, will explain how the interface works and how you can start using powerful machine learning models with a few simple clicks!

## Start Screen

Every time you open Runway you will see the **Start Screen**. From here, you can choose to **Start from a Model** or restore a previous **Workspace** from another session. (Read more on workspaces [here](getting-started/views.md)).

![Runway Welcome View](assets/images/views/intro-screen.png)

## Models Directory

**Runway's Models Directory** is a unique place to search, discover, publish and install machine learning models. You can search for models with specific attributes, input types, creator, functionality or date.

![Models Directory](assets/images/views/home-screen.png)

This view is compromised of 3 main sections: Sidebar, New Model and a Model Box for every model listed.

![Models Directory](assets/images/views/home-screen-annotated.png)

1) **Sidebar**: This panel gives you quick access to already installed models

2) **New Model**: This button will allow you to import models into Runway. Check how to import models [here](how-to/importing.md).

3) **Model Box**: This model box contains brief information of a model. Clicking it will take you to the model page where you can use it inside a Workspace.

## Model View

Every model in Runway has its own view. From here, you can learn more about the model, authors, specifications and characteristics, examples, license, and more.


![versions](assets/images/views/model-view-annotated.png)



1) **Model Tabs**

<!-- tabs:start -->

#### **Overview**

Overview provides you with a tagline and a long description detailing what the model does.

![overview](assets/images/views/model-tab/overview.png)

#### **Versions**

Allows you to set what the default model is. You will only be able to do this on models that you have added to Runway.

![versions](assets/images/views/model-tab/versions.png)

#### **Files* **

Shows any pickles that are available for the model, also known as checkpoints.

![versions](assets/images/views/model-tab/files.png)

#### **Gallery**

This shows images of what the model does.

![versions](assets/images/views/model-tab/gallery.png)

#### **Templates* **

This is a quick-start way of using a model.

![versions](assets/images/views/model-tab/templates.png)

#### **License**

This is the license of the model to show what it can be used for, such as commercial purposes.

![versions](assets/images/views/model-tab/license.png)

#### **Settings* **

This is only available if you added the model to Runway. This allows you to rename and remove the model.

![versions](assets/images/views/model-tab/settings.png)

<!-- tabs:end -->

> __Note__: * These tabs are only available if you published the model to Runway

2) **Model Side Bar**

The model side-bar provides you further information.

<!-- tabs:start -->

#### **Publishers**

**Publishers** shows the user who published the model to Runway.

![publishers](assets/images/views/model-sidebar/publishers.png)

#### **Attributions**

**Attributions** show the research institutions and researchers who designed and created the model.

![attributions](assets/images/views/model-sidebar/attributions.png)

#### **Characteristics**

**Characteristics** informs you when the model was published, last updated and if it supports the CPU and/or GPU.

![characteristics](assets/images/views/model-sidebar/characteristics.png)

#### **Keywords**

![keywords](assets/images/views/model-sidebar/keywords.png)

#### **Performance Notes**

**Performance Notes** shows the user who published the model to Runway.

![performance-notes](assets/images/views/model-sidebar/performance-notes.png)

Here you can view the links to the model's code repository as well as research papers associated to the model.

#### **Code, Paper and More**

![versions](assets/images/views/model-sidebar/code-paper.png)

<!-- tabs:end -->

3) **Add to Workspace**

This button allows to add the current model in view to a new or existing workspace.

![add-to-workspace](assets/images/views/add-to-workspace.png)


## Workspaces

You can use and group models in a workspace. Inside a workspace, you can interact with your model. Let's walk through the layout of how to interact with a model.

![Input/Output View](assets/images/views/workspace-annotated.png)

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


### Understanding Workspaces

Runway is logically organized in a hierarchy of **Workspaces** and [**Models**](getting-started/model-101.md). **Workspaces** provides a way to logically group models used into the same project. For example, a creator working on an interactive dance performance may create a workspace containing two models that she would like to use for her piece: OpenPose for detecting the dancers’ movements and WaveNet for generating a score for the dance.

A **Workspace** is a collection of models. In a **Workspace** you can organize your models by theme, hierarchy, or however else you like.

?> **Remember:** A Workspace is a collection of AI models. By grouping models together you can experiment and create with models in a way that's logical to you.

## Settings

The **Settings** view has your account details and basic information about the app.

![Input/Output View](assets/images/views/settings.png)
