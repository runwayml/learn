# Overview

Welcome to Runway! Runway is a platform and community for you to create with AI. Runway allows provides you with a simple visual interface to use the latest AI techniques. We offer a creative platform where you can create and also allow easy connections to third party applications. Here, in our documentation, we aim to help you get up and running with Runway ML.

Runway is composed of two main parts:
- An desktop app with a simple and intuitive visual interface.
- A dev API to run a headless version of Runway. *Coming soon!*

Here, we will go over the desktop application. We will explain how the interface works and how you can start using state of the art artificial intelligence models with a few simple clicks!

The current beta version of Runway (*Release 0.1.0*) has three main views: I/O, Models Directory and Settings. You can switch between views clicking on the vertical menu on the left.

## 1) Start Screen

Every time you open Runway you will see the **Start Screen**. Here you can choose to **Start from a Model** or restore a previous **Workspace** (more on Workspaces below).

![Runway Welcome View](https://runway.nyc3.digitaloceanspaces.com/documentation/0.2.0/splash.jpg)

Once you select a model or load a Workspace, you will see the **Input/Output view**. This is Runway's main view; the place where you can interact with your models with a variety of input and output options described below.

![Input/Output View](https://runway.nyc3.digitaloceanspaces.com/documentation/0.2.0/io_annotated.jpg)

- 1) **Workspaces and Models**: All current Workspaces and Models will be visible in this panel. The Workspace and Model that's currently being used will be highlighted.
- 2) **Current Input Source**: Depending on the model you are working on, the input source will vary. Here is a list of current supported input values:

| Input      | Supported Types | Description                                       |
|------------|-----------------|---------------------------------------------------|
| Camera     | image           | Use frames from the webcam stream as input        |
| Microphone | audio           | Audio segments from microphone as input           |
| Text       | text            | Free-from text input                              |
| File       | all types       | Use a supported file type                         |
| HTTP       | all types       | Query and receive results via an HTTP requests    |
| Socket.IO  | all types       | Query and receive results via a Socket.IO message |
| OSC        | all types       | Query and receive results using OSC over UDP      |

- 3) **Change Input Source**: From this dropdown menu you can switch the type of input you want for the selected model.
- 4) **Model and Input Options**: Technically called *Hyperparameters*, this are the arguments and variables from where you can tweak and change the way the model works. Every model has it's own custom set of configurations and some might not have at all. Some inputs Options, like camare settings, might be configured here too.
- 5) **Output Data**: Once a model is running, you will be able to see its data output in this panel. For the most part, this will be a `JSON` data structure containing the current values created by passing the input through the model.
- 6) **Output View**: From this panel you can select the type of output for your model. Here is a list of current supported output options:

| Output     | Description                                       
|------------|---------------------------------------------------------------------|
| Local      | Preview the model output inside Runway                              |
| File       | Stream the model output into a file using supported formats         |
| HTTP       | Query and receive results via an HTTP requests                      |
| Socket.IO  | Query and receive results via a Socket.IO message                   |
| OSC        | Query and receive results using OSC over UDP                        |

- 7) **Change Output Option**: From this dropdown menu you can switch the type of output you want for the selected model.
- 8) **Run/Stop & Install**: This button will allow you to start and stop your models. As of release 0.2.0 models can only be run locally. Uninstalled models will prompt here to install them before first use.

<p class='note'>
  Upcoming updates will include: <br>
  <b>Cloud GPU:</b> Run models powered with GPUs from a variety of cloud providers. <br>
  <b>Training:</b> Train models on your own datasets.
</p>

### Understanding Workspaces

Runway is logically organized in a hierarchy of **Workspaces** and **Models** (check [the intro to A.I](getting-started/intro-to-ai.md) for a definition of a model). **Workspaces** provide a way to logically group models used in the same project together. For example, a user working an interactive dance performance may create a workspace containing two models that she would like to use for her piece: OpenPose for detecting the dancers’ movements and WaveNet for generating a score for the dance.

A **Workspace** is a collection of models. In a **Workspace** you can organize your models by theme, hierarchy, or however else you like.

?> **Remember:** A Workspace is a collection of A.I models. By grouping models together you can experiment and create with artificial intelligence models in a way that's logical to you.

## 2) Models Directory

Runway's **Models Directory** is a unique place to search, discover, publish, install new models. You can search for models with specific attributes, input types, creator, functionality or date. Runway comes with a pre-packed set of models that are ready to use right out of the box, but you will need to download and install other models.

![Models Directory](https://runway.nyc3.digitaloceanspaces.com/documentation/0.2.0/models_directory_annotated.jpg)

- 1) **Your Models**: This panel gives you quick access to already installed models.
- 2) **Import Model**: This button will allow you to import models into Runway. Check how to import models [here](how-to/importing.md).
- 3) **Model Box**: This model box contains a brief information of a model. Clicking it will take you to the model page where you can use it inside a Workspace.

## 3) Model Information

Every model in Runway has its own view. From here, you can learn more about the model, authors, specifications and characteristics, examples and license.

![Input/Output View](https://runway.nyc3.digitaloceanspaces.com/documentation/0.2.0/models_info_annotated.jpg)

- 1) **Information**: Name, authors, gallery, description and license of the model.
- 2) **Use (add to Workspace)**: Add this model to a workspace.
- 3) **Characteristics**: A summary table with the main characteristics of the model.

## 4) Settings

The settings view has your account details and basic information about the app.

![Input/Output View](https://runway.nyc3.cdn.digitaloceanspaces.com/documentation/settings_view.png)

<p class='next'>
  <b><a href="/#/getting-started/intro-to-ai">
   Read Next: A Brief Introduction to Artificial Intelligence (A.I)
  </b></a>
  <br/>
  Understand how A.I works and how can you use it in Runway
</p>
