# Tutorial: StyleGAN

In this tutorial, we will generate synthetic images using a StyleGan implementation from the paper ["A Style-Based Generator Architecture for Generative Adversarial Networks"](https://arxiv.org/pdf/1812.04948.pdf). This model has different checkpoints we can use to generate and create synthetic images.

### Step 1

Let's begin selecting our model. For this tutorial we are going to use Style Gan.

![Select Model](assets/images/tutorials/tutorial_style_gan/01_selecting_model.png)

### Step 2

Let's add it to a new workspace.

![Add Model to Workspace](assets/images/how-to/run-locally/add-to-workspace.png)

### Step 3

Here we choose our inputs and outputs. Let's select **Vector** for input and **Preview** for output.

![IO](assets/images/tutorials/tutorial_style_gan/03_workspace.png)

### Step 4

For this model, we select a checkpoint we want to use, from our options. Here we select **Flickr Faces**

![io](assets/images/tutorials/tutorial_style_gan/04_io.png)

### Step 5

In order to run your model, ensure the toggle is switched on in the lower left hand corner. Let's click **Run Remotely** which will now start your model running in the cloud. 

![Remote GPU](assets/images/how-to/run-locally/running-remotely.png)

### Summary

Now you should have some generated faces on your screen! Remember in order to run your model, ensure the toggle is selected to **Enable GPU** and click on **Run Remotely**.
