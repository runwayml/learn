# Tutorial: Colorizing Black & White Video's

In this tutorial, we will colorize frames of a black and white video using the [Colorful Image Colorization](https://arxiv.org/abs/1603.08511) model by Zhang et al. This model uses a deep neural network to generate a colorized version of a greyscale image.

### Requirements

- Runway App
- Docker (If you don't have Docker installed, please follow the installation instructions [here](/getting-started/docker).)
- A grayscale MP4 video

### Step 1

The first step is to select the model **Automatic Colorization** from the Model Directory:

![Colorizing images with Runway, step 1](assets/images/tutorials/tutorial_colorizing_video/automatic01.png)

### Step 2

Next, add the model to a workspace from the top right side of the app.

![Colorizing images with Runway, step 2](assets/images/tutorials/tutorial_colorizing_video/automatic02.jpg)


### Step 3

If you haven't installed **Automatic Colorization**, the bottom right button will prompt you to install the model.  **You need to have Docker installed in order to continue.**

![Colorizing images with Runway, step 3](assets/images/tutorials/tutorial_colorizing_video/automatic03.jpg)


?> Some deep learning models might be large so please note that downloading the model might take a couple of minutes. In this case, **Automatic Colorization** might take **4 to 8 minutes** to download depending on your internet connection.

![Colorizing images with Runway, step 4](assets/images/tutorials/tutorial_colorizing_video/automatic04.jpg)


### Step 4

From the **Input** dropdown in the I/O View select the **File** option. Choose your black and white video. In this case, we are using the film [Man with a Movie Camera, 1929](https://www.youtube.com/watch?v=R2hJGcD_Tc0) by Dziga Vertov.

![Colorizing images with Runway, step 4](assets/images/tutorials/tutorial_colorizing_video/4_select_input_file.png)

### Step 5

On the I/O View select the **File** option in the **Output** dropdown. We will be creating a new video file of the colorized grayscaled video.

![Colorizing images with Runway, step 5](assets/images/tutorials/tutorial_colorizing_video/5_select_output_file.png)

### Step 6

Adjust the output settings. You can change the amount of frames per second (fps) and format of the output video.

?> Higher fps will mean more processing time!

![Colorizing images with Runway, step 6](assets/images/tutorials/tutorial_colorizing_video/6_change_settings.png)

### Step 7

Next, click the **Run Automatic Colorization** button on the bottom right corner.

![Colorizing images with Runway, step 7](assets/images/tutorials/tutorial_colorizing_video/7_run_model.png)

### Step 8

Once the model is running, click the **Start exporting** button to start processing the video frames.

![Colorizing images with Runway, step 8](assets/images/tutorials/tutorial_colorizing_video/8_click_start_exporting.png)

### Step 9

After processing all the frames, Runway will save the final video in your default export folder.

<p class="note"><b>NOTE:</b> Exports are stored by default in the following folders depending on your operating system: <code>\Users\USERNAME\Downloads</code> for Windows, <code>/Users/USERNAME/Downloads</code> for Mac, and <code>/home/USERNAME/Downloads</code> for Linux. You can change the destination path for your exports via the app's settings.

![Colorizing images with Runway, step 9](assets/images/tutorials/tutorial_colorizing_video/10_file_saved.png)

#### Results

<video width="320" height="240" controls>
  <source src="assets/images/tutorials/tutorial_colorizing_video/Man%20with%20a%20Movie%20Camera(Dziga%20Vertov,%201929).mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>

<video width="320" height="240" controls>
  <source src="assets/images/tutorials/tutorial_colorizing_video/1546968375020.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>


### Summary

In this tutorial we turned a colorized a grayscale video using the [Colorful Image Colorization](https://arxiv.org/abs/1603.08511) deep learning model by Zhang et al. and created a new video with colorized frames.
