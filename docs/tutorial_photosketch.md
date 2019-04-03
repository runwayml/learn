
# Tutorial: Creating Contour Drawings with PhotoSketch

Runway allows you to generate contour drawings from images automatically.
In this tutorial, we will use PhotoSketch to create an outline from your camera input. Then, we will output the resulting image via HTTP for external use.

## Requirements
* Runway Beta
* Docker to run the model locally, or enough credits to use a remote GPU (To install Docker, please follow the installation instructions [here](https://docs.runwayapp.ai/#/installation?id=download-docker))
* A webcam or built-in camera

## Step 1

Select the **PhotoSketch** model from the Model Directory.

![Select Model](01_select_model.png)

## Step 2

Add the model to a workspace using the drop-down list on the top right
side of the app.

![Add to Workspace](02_add_to_workspace.png)

## Step 3

Select **Input** > **Camera**

![Set Input](03_set_input.png)

## Step 4

Set the camera and image options.

![Settings](04_settings.png)

## Step 5

Select **Output** > **Network**, and click on **HTTP**.
Use the HTTP server and route to send the resulting image to an external app.

To use a remote GPU, make sure you have available credits, toggle the **Enable Remote GPU** switch on, and click on **Run Remotely**.

Alternatively, you may run the model locally. Toggle the remote GPU off, and make sure Docker is running. Click on the button on the bottom right to download the model and run it locally.

![HTTP Output](05_http.png)

## Step 6

In the external app, make sure Runway's server and routes match to receive the output as a base 64 image.

![Success](06_success.png)

## Summary

This tutorial uses PhotoSketch to generate contour drawings from your camera input.
