
# Tutorial: Realistic Textures (ESRGAN)

RunwayML incorporates the ESRGAN model to enable image super-resolution. This tutorial shows how to enhance low-resolution images to generate a high-resolution texture without unpleasant artifacts.

### Requirements
* [RunwayML](https://runwayml.com/)
* A folder with multiple low-resolution image files (such as the ones found in this [wiki](https://wiki.minetest.net/Low_resolution_texture_packs))


### Step 1

Select the **ESRGAN** model from the Model Directory.

![Select Model](assets/images/tutorials/tutorial_esrgan/01_select_model.png)

### Step 2

Add the model to a workspace using the drop-down list on the top right
side of the app.

![Add to Workspace](assets/images/tutorials/tutorial_esrgan/02_add_to_workspace.png)

### Step 3

Select **Input** > **File**, and click on **Open Folder** to select
your image folder.
Select **Output** > **Local**.

![Set Input/Output](assets/images/tutorials/tutorial_esrgan/03_set_io.png)

### Step 4

Choose to run the model locally or remotely on an external GPU. You can enable the remote GPU by toggling the Enable Remote GPU switch on. Next, click on Run Remotely.

![Run the Model](assets/images/tutorials/tutorial_esrgan/04_start.png)

### Step 5

Click on each image to generate and display the enhanced texture, which can be stored using the **Save Image** button.
Alternatively, you may select **File** as output to export these images locally, or **Network** to send them to an external app.

![Success](assets/images/tutorials/tutorial_esrgan/05_success.png)

### Summary

This tutorial demonstrates how to enhance low-resolution images to generate realistic textures using ESRGAN.
