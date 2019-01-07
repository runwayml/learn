# Tutorial: Skeleton tracking in Processing

Runway provides a simple visual interface for experimenting with a variety of machine learning models, but what happens when you want to use those models outside of Runway, in your own applications? This tutorial demonstrates how to perform skeleton tracking in a Processing sketch by communicating in real-time with a pose estimation model running inside Runway.

### Step 1

In this tutorial, we will use PoseNet, which is based on the paper [Towards Accurate Multi-person Pose Estimation in the Wild](https://arxiv.org/abs/1701.01779) and a [Tensorflow.js](https://js.tensorflow.org/) implementation by [Dan Oved](https://www.danioved.com/). The first step is selecting the PoseNet model from the Model Directory.

![step 1](https://runway.nyc3.cdn.digitaloceanspaces.com/documentation/tutorial_posenet_processing/1_select_posenet.png)

### Step 2

![step 2](https://runway.nyc3.cdn.digitaloceanspaces.com/documentation/tutorial_posenet_processing/2_add_posenet_to_workspace.png)

### Step 3

![step 3](https://runway.nyc3.cdn.digitaloceanspaces.com/documentation/tutorial_posenet_processing/3_select_camera_input.png)


### Step 4

![step 4](https://runway.nyc3.cdn.digitaloceanspaces.com/documentation/tutorial_posenet_processing/4_select_osc_output.png)

### Step 5

![step 5](https://runway.nyc3.cdn.digitaloceanspaces.com/documentation/tutorial_posenet_processing/5_run_posenet.png)

### Step 6

![step 6](https://runway.nyc3.cdn.digitaloceanspaces.com/documentation/tutorial_posenet_processing/6_posenet_running.png)

### Step 7

![step 7](https://runway.nyc3.cdn.digitaloceanspaces.com/documentation/tutorial_posenet_processing/7_open_processing_sketch.png)

### Step 8

![step 8](https://runway.nyc3.cdn.digitaloceanspaces.com/documentation/tutorial_posenet_processing/8_voila.png)

### Summary

This tutorial shows how to use a pose estimation model, called PoseNet, to perform pose estimation on the webcam stream and send the results to a Processing sketch.