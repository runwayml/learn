# Train Your Own Models

## Overview
In addition to publishing open source, pre-trained machine learning models in the RunwayML platform, now you can you train your own models directly inside of the app! This guide will walk you through the steps, but first, here's a quick FAQ to provide some context. 

### What's a model?
Generally speaking, a model is a network of machine learning algorithms that has learned patterns within a given dataset. Instead of being explicitly programmed, it develops its own parameters for how to represent--or model--those patterns to make predictions about new data (such as to detect objects in a video) or generate completely new content that mimics the original data on which it was trained (such as synthesize images from a collection of paintings). 

### What does it mean to train a model?
Training is the process of providing a machine learning algorithm with data and creating the conditions for the algorithms to learn patterns, also known as features, within that data. RunwayML makes training very easy: all you need to do is to supply your own data (although we have some available for you to try) and determine the number of steps the algorithm should take to learn the features. For a technical demonstration of the visual patterns a machine learning model might learn, watch Gene Kogan's video, [What Convolutional Neural Networks See](https://experiments.withgoogle.com/what-neural-nets-see).

### What kind of model can I train in RunwayML?
Model training is an experimental feature 🧪in RunwayML, and at the time of this writing (November 2019), you can only train a generative model for synthesizing brand new images. Support for additional model types will be added in the future. 

### What kind of data do I need?
To train a generative image model, you need a collection of images. Suggestions for the amount, as well as considerations for how to source and prepare those images are below.

### How long will it take to train my model?
The time to train a model depends on a combination of many factors, including but not limited to the type of data (in this case, you'll be using images as opposed to words or audio), the amount of training data, and the number of training steps. 

To train your own generative image model, RunwayML greatly reduces the amount of training time by using using a technique called Transfer Learning. With this technique, your model will be trained on top of another generative image model called [StyleGAN](https://open-app.runwayml.com/?model=runway/StyleGAN). StyleGAN was trained on a massive amount of images, and transfer learning leverages all of the features it learned from the original data to speed up the process of learning new patterns in your image dataset. Not only does this greatly reduce the amount of training time, it also lowers the amount of images that you need to train your own model. You can learn more about StyleGAN and how it was trained from the links posted on model's [overview page](https://open-app.runwayml.com/?model=runway/StyleGAN).

### What can I do with my newly-trained model?
During training, your model learned an incredible amount of new visual features that now can be combined to generate new images. Because it was trained on top of StyleGAN using the Transfer Learning technique, your model will appear under the list of Checkpoints when you add the StyleGAN model to a workspace. The space of all potential new images that your model can create is called the latent space, and even though this is an extremely high dimensional space, you can explore a 2D representation of it when you run your model's checkpoint. Happy exploring and image making!

Now here are the steps to get started...

## Step 1: Collect Data


## Step 2: Prepare Data

Recommended quantity
No corrupted images, like all black
Automatically resizing 


Crop happens because you select it
Choose crop
Then resizing happens

Ideally if square that would be better


Time length:
Size
Number of images —> maybe not: Variety of images? 
Starting model
Steps


Give examples for what will happen with different kinds of sizes uploaded



## Step 3: Start Training Experiment
Launch RunwayML and click either “Browse Models” or “Open Workspaces” to dismiss the starting window and access the far left navigation bar and select “Training Experiments”

< insert GIF >

Currently, training experiments are only available with the StyleGAN model. Click to Start Experiment, give the experiment a name, and click Create.


Step 1: 


Free plan 3 hours at once



## Step 4: Add Data


## Step 5: Select a Starting Point

Starting from a pre-trained model will be faster
    it’s faster
    mix two models to make your own model
Why would you want to start with a particular model for this transfer learning process?

## Step 6: Choose Settings


## Step 7: Train



## Step 8: Use Your Model!
