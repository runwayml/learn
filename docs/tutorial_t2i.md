# Experimenting with GANs: Playing with Text to Image

Runway allows you to use and experiment with state of the art machine learning models without typing a single line of code. In this tutorial we will be using an model called [AttnGAN: Fine-Grained Text to Image Generation with Attentional Generative Adversarial Networks](https://github.com/taoxugit/AttnGAN/) by Tao Xu et al. to **generate images based on text.** This is the same model you can find in the interactive web experiment [Text2Image](https://t2i.cvalenzuelab.com/).


### Requirements

- Runway Beta
- Docker (If you don't have Docker installed, please follow the installation instructions [here](/installation?id=download-docker).)


### Step 1

The first step is to select the model **AttnGAN** from the Model Directory:

![GAN, AttnGAN with Runway, step 1](https://runway.nyc3.digitaloceanspaces.com/documentation/tutorial_attngan_local/1_select_attngan.png)

### Step 2

Next, click the install button the top right side of the app.

![GAN, AttnGAN with Runway, step 2](https://runway.nyc3.digitaloceanspaces.com/documentation/tutorial_attngan_local/2_click_install.png)

This will prompt you to install the model. **You need to have Docker installed in order to continue.**

?> Some deep learning models might be large so please note that downloading the model might take a couple of minutes. In this case, AttnGAN might take **4 to 8 minutes** to download depending on your internet connection.

![GAN, AttnGAN with Runway, step 3](https://runway.nyc3.digitaloceanspaces.com/documentation/tutorial_attngan_local/4_popup_downloading.png)

### Step 3

Once the model is installed, you will be able to add it to a Workspace. Click on the dropdown menu and create a new workspace.

![GAN, AttnGAN with Runway, step 3](https://runway.nyc3.digitaloceanspaces.com/documentation/tutorial_attngan_local/5_model_installed.png)

### Step 4

From the **Input** dropdown in the I/O View select the **Text** option.

![GAN, AttnGAN with Runway, step 4](https://runway.nyc3.digitaloceanspaces.com/documentation/tutorial_attngan_local/6_select_input_text.png)

### Step 5

On the I/O View select the **Local** option in the **Output** dropdown.

![GAN, AttnGAN with Runway, step 5](https://runway.nyc3.digitaloceanspaces.com/documentation/tutorial_attngan_local/7_select_output_local.png)

### Step 6

Next, click the **Run AttnGAN** button on the bottom right corner.

![GAN, AttnGAN with Runway, step 5](https://runway.nyc3.digitaloceanspaces.com/documentation/tutorial_attngan_local/8_run_model.png)

### Step 7

Once the model is running, you will be able to type anything in the **Text** input box and generate your own A.I based images based on your text!

![GAN, AttnGAN with Runway, step 5](https://runway.nyc3.digitaloceanspaces.com/documentation/tutorial_attngan_local/9_image_generated.png)

### Summary

This tutorial shows how to use [AttnGAN](https://github.com/taoxugit/AttnGAN/), a Generative Adversarial Neural Network (GAN) that was trained to generate images from text.