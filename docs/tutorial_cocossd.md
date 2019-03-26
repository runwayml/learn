
# Tutorial: Object localization with COCO-SSD

Runway facilitates object detection and identification in images and video. 
In this tutorial, we will use COCO-SSD to find and label the elements shown in a movie.

### Requirements
* Runway Beta
* Docker (If you don't have Docker installed, please follow the
  installation instructions [here](https://docs.runwayapp.ai/#/installation?id=download-docker))
* A video that features everyday items.

### Step 1

Select the **COCO-SSD** model from the Model Directory.

![Select Model](images/tutorial_cocossd/01_select_model.png)

### Step 2

Add the model to a workspace using the drop-down list on the top right
side of the app.

![Add to Workspace](images/tutorial_cocossd/02_add_to_workspace.png)

### Step 3

Select **Input** > **File**, and click on **Open File** to select
your movie file.
Select **Output** > **Local**.

![Set Input/Output](images/tutorial_cocossd/03_set_io.png)

### Step 4

You can change the model and image settings. Once you are ready, click on the button on the bottom right side of the app to run
the model locally.  

![Run the Model](images/tutorial_cocossd/04_start.png)

### Step 5

Play and navigate the movie using Runway's built-in player. The output
will show bounding boxes and labels for each detected object. Other
**File** and **Network** outputs allow you to export the output data
for external use.

![Success](images/tutorial_cocossd/05_success.png)

### Summary

This tutorial shows how to use COCO-SSD for object detection and
identification in a movie file.