# Tutorial: Contour Drawings with PhotoSketch

The [PhotoSketch model](https://arxiv.org/pdf/1901.00542.pdf) created by Li et al. allows you to infer contour drawings from images automatically.
In this tutorial, we will use Runway to run PhotoSketch to create a real-time contour outline of your webcam stream. We will then send the resulting image via HTTP network to a simple web app built with JavaScript and [p5.js](http://p5js.org/)

### Requirements
* Runway
* A webcam or built-in camera

### Step 1

Select the **PhotoSketch** model from the Model Directory.

![Select Model](assets/images/tutorials/tutorial_photosketch/01_select_model.png)

### Step 2

Add the model to a workspace using the drop-down list on the top right
side of the app.

![Add to Workspace](assets/images/tutorials/tutorial_photosketch/02_add_to_workspace.png)

### Step 3

Select **Input** > **Camera**

![Set Input](assets/images/tutorials/tutorial_photosketch/03_set_input.png)

### Step 4

Set the camera and image options.

![Settings](assets/images/tutorials/tutorial_photosketch/04_settings.png)

### Step 5

Select **Output** > **Network**, and click on **HTTP**.
Use the HTTP server and route to send the resulting image to an external app.

Choose to run the model locally or remotely on an external GPU. You
can enable the remote GPU by toggling the **Enable Remote GPU**
switch on. Click on **Run Remotely** when your app is ready.

![HTTP Output](assets/images/tutorials/tutorial_photosketch/05_http.png)

### Step 6

Our **ColoringBook** example for p5.js receives the PhotoSketch drawing from Runway and displays it on the canvas, where you can color or draw on it using the mouse cursor.

To get started, navigate to the [example repository](https://github.com/runwayml/p5js).

* To clone the repository (requires [git](https://git-scm.com/)), click on the right side button and copy the link. Open your terminal or command prompt, navigate to the folder where you would like to store the repository, and type:

```
$ git clone https://github.com/runwayml/p5js.git
```

* Alternatively, click on the right side button and select **Download ZIP** instead. Unzip the file to the desired location.

![Get Repository](assets/images/tutorials/tutorial_photosketch/06_repository.png)

Once the repository folder is ready, navigate to `PhotoSketch/ColoringBook/` and open `index.html` using your browser of choice (or a local web server).

### Step 7

Make sure PhotoSketch is running in Runway and check if the **Port** value matches Runway's HTTP Server from **Step 5** (e.g. `8001`). Press the PhotoSketch button until you receive an image you like.

![Success](assets/images/tutorials/tutorial_photosketch/07_success.png)

When you are done with your sketch, click on the
**Save** button to download the canvas as an image file.

### Summary

In this tutorial, we used the PhotoSketch model to generate live contour drawings from your webcam stream and use those as inputs to draw on a web app.
