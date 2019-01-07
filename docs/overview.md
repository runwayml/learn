# Overview

> __Note__: Runway is beta software, so things are in flux! Expect features and documentation to change often.

Runway is a toolkit that enables creators of all kinds to use artificial intelligence in an intuitive way. Runway is composed of two main parts: 
- An desktop app with a simple and intuitive visual interface.
- A dev API to run a headless version of Runway. *Coming soon!*

In this quick overview, we will go over the desktop application, explain how the interface works and how you can start using state of the art artificial intelligence models with a few simple clicks!

The current beta version of Runway (*Release 0.0.4*) has three main views: I/O, Models Directory and Settings. You can switch between views clicking on the vertical menu on the left.

## 1) I/O View

The I/O (Input/Output) is the main view and the one that you will see when the app first starts. If there are no **Workspaces** created (more on Workspaces below) or Models running you will see the initial **Welcome Screen**. On the **Welcome Screen** you'll get information about the current release, links to documentation, new features and general information about your account.

![Runway Welcome View](https://runway.nyc3.digitaloceanspaces.com/documentation/welcome_view.png)

Whenever you open a new model or load a Workspace the I/O View will change to display the Input/Output screen. This is one of Runway's main view and the place where you will see your models run.

![Input/Output View](https://runway.nyc3.cdn.digitaloceanspaces.com/documentation/io_view_annotated.png)

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
- 4) **Model Options**: Technically called *Hyperparameters*, this are the arguments and variables from where you can tweak and change the way the model works. Every model has it's own custom set of configurations and some might not have at all.
- 5) **Output Data**: Once a model is running, you will be able to see it's data output in this panel. For the most part, this will be a `JSON` data structure containing the current values created by passing the input through the model.
- 6) **Output View**: From this panel you can select the type of output for your model. Here is a list of current supported output options:

| Output     | Description                                       
|------------|---------------------------------------------------------------------|
| Local      | Preview the model output inside Runway                              |
| File       | Stream the model output into a file using supported formats         |
| HTTP       | Query and receive results via an HTTP requests                      |
| Socket.IO  | Query and receive results via a Socket.IO message                   |
| OSC        | Query and receive results using OSC over UDP                        |

- 7) **Change Output Option**: From this dropdown menu you can switch the type of output you want for the selected model. 
- 8) **Run/Stop**: This button will allow you to start and stop your models. As of release 0.1.0 models can only be run locally.

<p class='note'>
  Upcoming updates will include: <br>
  <b>Cloud GPU:</b> Run models powered with GPUs from a variety of cloud providers. <br>
  <b>Training:</b> Train models on your own datasets. 
</p>

### Understanding Workspaces

Runway is logically organized in a hierarchy of **Workspaces** and **Models** (check [the intro to A.I](intro-to-ai.md) for a definition of a model). **Workspaces** provide a way to logically group models used in the same project together. For example, a user working an interactive dance performance may create a workspace containing two models that she would like to use for her piece: OpenPose for detecting the dancers’ movements and WaveNet for generating a score for the dance.

A **Workspace** is a collection of models. In a **Workspace** you can organize and group your models by theme, hierarchy, interest of whatever other reason you like.

?> **Remember:** A Workspace is a collection of A.I models. By grouping models together you can experiment and create with artificial intelligence models in a way that's logical to you.

## 2) Models Directory

Runway's **Models Directory** is a unique place to search, discover, publish, install new models, and then experiment with those models inside Runway or integrate them with other platforms. You can search for models with specific attributes, input types, creator, functionality or date. Runway comes with a pre-packed set of models that are ready to use right out of the box but you will need to install most models.

![Models Directory](https://runway.nyc3.cdn.digitaloceanspaces.com/documentation/models_directory_annotated.png)

- 1) **Your Models**: This panel will provide you with a quick overview and access to available and installed models.
- 2) **Import Model**: This button will allow you to import models into Runway. Check how to import models [here](importing.md).
- 3) **Model Box**: This model box contains a brief information of a model. Clicking it will take you to the model page where you can use it inside a Workspace.   x

## 3) Model

In Runway, every model has its own view and specification. From here, you learn more about the model, it's authors, specifications and characteristics.

![Input/Output View](https://runway.nyc3.cdn.digitaloceanspaces.com/documentation/model_view.png)

- 1) **Information**: Name, authors, description and license of the model.
- 2) **Install and Use**: Whenever you want to install and/or use a model you will need to go here. If the model is not installed, you will be able to install it.
- 3) **Characteristics**: A summary table with the model main characteristics.

## 4) Settings

The settings view has your account details and basic information about the app.

![Input/Output View](https://runway.nyc3.cdn.digitaloceanspaces.com/documentation/settings_view.png)

<p class='next'>
  <b><a href="/#/intro-to-ai">
   Read Next: A Brief Introduction to Artificial Intelligence (A.I)
  </b></a> 
  <br/> 
  Understand how A.I works and how can you use it in Runway
</p>