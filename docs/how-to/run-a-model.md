# Running a Model on Cloud GPU


When you are in your workspace, have your inputs and output selected, you can now run your model. Click **Run Remotely** which will now start your model running in the cloud.

![Remote GPU](assets/images/how-to/run-locally/running-remotely.png)

## What is Running Remotely?

Here we can run our models remotely. By running remotely it runs in the cloud, so not on your computer. Some advantages of running remotely are:

* You can use Runway with little processing power on your computer
* Get started quickly!
* No setup required
* Faster processing speeds by using our cloud GPUs

## Tutorial

In this tutorial, we will use the StyleGan model and run it on remote GPU. 

### Step 1

If this is the first time you are opening the app, then choose 'Start from Model'

![Intro Screen: Select Model](assets/images/views/intro-screen-new-model.png)

If you are already in the app, then you should be able to browse the models. If you are not on this view, then let's go ahead change navigation on the left hand tab. Now we are in browsing view.

![Home Screen](assets/images/views/home-screen-nav-bar.png)


### Step 2

Let's begin selecting our model. For this tutorial we are going to use Style Gan.

![Select Model](assets/images/tutorials/tutorial_style_gan/01_selecting_model.png)

### Step 3

Let's add it to a new workspace.

![Add Model to Workspace](assets/images/how-to/run-model/add-to-workspace.png)

### Step 4

Here we choose our inputs and outputs. Let's select **Vector** for input and **Preview** for output.

![IO](assets/images/tutorials/tutorial_style_gan/03_workspace.png)

### Step 5

For this model, we can select different checkpoint we want to use from our options panel. Here we select **Flickr Faces**

![io](assets/images/tutorials/tutorial_style_gan/04_io.png)

### Step 6

In order to run your model, ensure the GPU toggle is switched on in the lower left-hand corner. Let's click **Run Remotely** which will now start your model on cloud GPU.

![Remote GPU](assets/images/how-to/run-locally/running-remotely.png)

### Step 7

In order to run your model, ensure the toggle is switched on in the lower left hand corner. Let's click **Run Remotely** which will now start your model running in the cloud. Your model will now run, but give it some time to start producing output!

![Remote GPU](assets/images/tutorials/tutorial_style_gan/06_success.png)

### Summary

Now you should have some generated faces on your screen! Remember in order to run your model, ensure the toggle is selected to **Enable GPU** and click on **Run Remotely**.
