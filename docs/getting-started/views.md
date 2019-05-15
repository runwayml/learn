## My Workspace

Once you select a model you will see your workspace for this model. This is the place where you can interact with your model. Let's walk through the layout of our workspace.

![Input/Output View](assets/images/views/workspace-annotated.jpg)

1) **Workspaces and Models**: All current Workspaces and Models will be visible in this panel. The Workspace and Model that's currently being used will be highlighted.

2) **Current Input**: The input sources will update according to what your model supports for input. Currently Runway supports the following inputs:

| Input      | Supported Types | Description                                       |
|------------|-----------------|---------------------------------------------------|
| Camera     | image           | Use frames from the webcam stream as input        |
| Microphone | audio           | Audio segments from microphone as input           |
| Text       | text            | Free-from text input                              |
| File       | all types       | Use a supported file type                         |
| HTTP       | all types       | Query and receive results via an HTTP requests    |
| Socket.IO  | all types       | Query and receive results via a Socket.IO message |
| OSC        | all types       | Query and receive results using OSC over UDP      |

3) **Options**: Each model has a set of options, you can change and tweak. In AI terms, these are often known as hyperparameters.

4) **Output**: Once a model is running, you will be able to see it's output in this panel. Some models will allow you to select the type of output you want. Current output types are:

| Output     | Description                                       
|------------|---------------------------------------------------------------------|
| Local      | Preview the model output inside Runway                              |
| File       | Stream the model output into a file using supported formats         |
| HTTP       | Query and receive results via an HTTP requests                      |
| Socket.IO  | Query and receive results via a Socket.IO message                   |
| OSC        | Query and receive results using OSC over UDP                        |

5) **Change Output Option**: From this dropdown menu you can switch the type of output you want for the selected model.

6) **Run/Stop & Install**: This button will allow you to start and stop your models. As of release 0.2.0 models can only be run locally. Uninstalled models will prompt here to install them before first use.


### Understanding Workspaces

Runway is logically organized in a hierarchy of **Workspaces** and [**Models**](getting-started/model-101.md) for a definition of a model). **Workspaces** provide a way to logically group models used in the same project together. For example, a user working an interactive dance performance may create a workspace containing two models that she would like to use for her piece: OpenPose for detecting the dancers’ movements and WaveNet for generating a score for the dance.

A **Workspace** is a collection of models. In a **Workspace** you can organize your models by theme, hierarchy, or however else you like.

?> **Remember:** A Workspace is a collection of A.I models. By grouping models together you can experiment and create with artificial intelligence models in a way that's logical to you.

## Model View

Every model in Runway has its own view. From here, you can learn more about the model, authors, specifications and characteristics, examples and license.

![Input/Output View](assets/images/views/model-view-annotated.png)

1) **Information**: Name, authors, gallery, description and license of the model.

2) **Use (add to Workspace)**: Add this model to a workspace.

3) **Characteristics**: A summary table with the main characteristics of the model.
