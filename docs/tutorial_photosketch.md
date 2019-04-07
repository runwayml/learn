
# Tutorial: Creating Contour Drawings with PhotoSketch

The [PhotoSketch model](https://arxiv.org/pdf/1901.00542.pdf) created by Li et al. allows you to infer contour drawings from images automatically.
In this tutorial, we will use Runway to run PhotoSketch to create a real-time contour outline of your webcam stream. We will then send the resulting image via HTTP network to a simple web app built with JavaScript and [p5.js](http://p5js.org/)

## Requirements
* Runway Beta
* Optional: Docker to run the model locally. (To install Docker, please follow the installation instructions [here](https://docs.runwayapp.ai/#/installation?id=download-docker))
* A webcam or built-in camera

## Step 1

Select the **PhotoSketch** model from the Model Directory.

![Select Model](images/tutorial_photosketch/01_select_model.png)

## Step 2

Add the model to a workspace using the drop-down list on the top right
side of the app.

![Add to Workspace](images/tutorial_photosketch/02_add_to_workspace.png)

## Step 3

Select **Input** > **Camera**

![Set Input](images/tutorial_photosketch/03_set_input.png)

## Step 4

Set the camera and image options.

![Settings](images/tutorial_photosketch/04_settings.png)

## Step 5

Select **Output** > **Network**, and click on **HTTP**.
Use the HTTP server and route to send the resulting image to an external app.

To use a remote GPU, make sure you have available credits, toggle the **Enable Remote GPU** switch on, and click on **Run Remotely**.

Alternatively, you may run the model locally. Toggle the remote GPU off, and make sure Docker is running. Click on the button on the bottom right to download the model and run it locally.

![HTTP Output](images/tutorial_photosketch/05_http.png)

## Step 6

In the external app, make sure Runway's server and routes match to receive the output as a base 64 image.

![Success](images/tutorial_photosketch/06_success.png)

## Summary

This tutorial uses PhotoSketch to generate contour drawings from your camera input.
