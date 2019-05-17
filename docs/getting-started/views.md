## My Workspace

You can use and group models in a workspace. Inside a workspace, you can interact with your model. Let's walk through the layout of how to interact with a model.

![Input/Output View](assets/images/views/workspace-annotated.png)

1) **Workspaces and Models**: Here we see all of our workspaces and models. The highlighted workspace is what we are currently viewing.

2) **Input**: This is where we you can specify the type of input we want for the model. Supported inputs include:


| Input      | Supported Types | Description                                       |
|------------|-----------------|---------------------------------------------------|
| Camera     | image           | Use frames from the webcam stream as input        |
| Text       | text            | Free-from text input                              |
| File       | all types       | Use a supported file type                         |
| HTTP       | all types       | Query and receive results via an HTTP requests    |
| Socket.IO  | all types       | Query and receive results via a Socket.IO message |
| OSC        | all types       | Query and receive results using OSC over UDP      |


3) **Output**: Once a model is running, you will be able to see it's output in this panel. Some models will allow you to select the type of output you want. Supported outputs include:


| Output     | Description                                       
|------------|---------------------------------------------------------------------|
| Local      | Preview the model output inside Runway                              |
| File       | Stream the model output into a file using supported formats         |
| HTTP       | Query and receive results via an HTTP requests                      |
| Socket.IO  | Query and receive results via a Socket.IO message                   |
| OSC        | Query and receive results using OSC over UDP                        |


4) **Options**: Each model has a set of options, you can change and tweak. These are often known as hyperparameters.

5) **Run/Stop & Install**: This button will allow you to start and stop your models. Learn more about [running a model](how-to/run-a-model.md)


### Understanding Workspaces

Runway is logically organized in a hierarchy of **Workspaces** and [**Models**](getting-started/model-101.md). **Workspaces** provide a way to logically group models used into the same project. For example, a creator working on an interactive dance performance may create a workspace containing two models that she would like to use for her piece: OpenPose for detecting the dancers’ movements and WaveNet for generating a score for the dance.

A **Workspace** is a collection of models. In a **Workspace** you can organize your models by theme, hierarchy, or however else you like.

?> **Remember:** A Workspace is a collection of AI models. By grouping models together you can experiment and create with models in a way that's logical to you.

## Model View

Every model in Runway has its own view. From here, you can learn more about the model, authors, specifications and characteristics, examples and license.

![Input/Output View](assets/images/views/model-view-annotated.png)

1) **Information**: Here we provide a short summary of the model itself and what we can do with it. We can also see the authors and the licensing information. Read more about models in [**Model 101**](getting-started/model-101.md)

2) **Use (add to Workspace)**: This allows is to add a model to a new or existing workspacee.

3) **Characteristics**: Here we find the researchers of the model, original paper and Github repo, where the models code is.
