# Train Your Own Models

requesting feedback:
even though this is written at a high level, look for clarity and technical accuracy
subscription information (what's the final plan?)
resulting checkpoints will only be visible to the user, yes? What if people don't want theirs to be public? e.g Helena Sarin
* somethings are repeated because I don't expect everyone to read this document straight through

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
The time to train a model depends on a combination of many factors, including but not limited to the type of data (in this case, you'll be using images as opposed to words or sounds), the amount of training data, the size of the data files, and the number of training steps. 

To train your own generative image model, RunwayML greatly reduces the amount of training time by using using a technique called Transfer Learning. With this technique, your model will be trained on top of another generative image model called [StyleGAN](https://open-app.runwayml.com/?model=runway/StyleGAN). StyleGAN was trained on a massive amount of images (70K!), and transfer learning leverages all of the features it learned from the original data to speed up the process of learning new patterns from your image dataset. Not only does this greatly reduce the amount of training time, it also lowers the amount of images that you need to train your own model. You can learn more about StyleGAN and how it was trained from the links posted on model's [overview page](https://open-app.runwayml.com/?model=runway/StyleGAN). 

Even with Transfer Learning, it's not unusual for training to last at least several hours. 

### What can I do with my newly-trained model?
During training, your model learns an incredible amount of new visual features that now can be combined to generate an seemingly infinite number of new images. Because it was trained on top of the StyleGAN model using the Transfer Learning technique (see above), your model will appear under the list of Checkpoints when you add StyleGAN to a workspace. The space of all possible new images that your model can create is called the latent space, which you can explore when you run StyleGAN with your model's checkpoint selected. Happy image making!

Here are the steps to get started...

## Step 1: Create a Dataset
To train your own generative image model, you need to create a dataset of images in a folder on your computer.

<< Add note on content, consistency, variety >>

**How much?** RunwayML Training Experiments will accept individual datasets that total less than 5GB in combined file size and less than 25K images in total number. That's a lot, we know. Generally, the more data you collect, the more your model might generate a greater variety of visual outcomes, but a starting recommendation is to gather around 500-5000K images. Some users, however, have been pleased with the results of a model trained on as few as 200 images.

**From where?** Are you a painter, photographer, doodler, architect, graphic designer, [asemic writer](https://en.wikipedia.org/wiki/Asemic_writing), musician who reads sheet music, or someone who works with visual marks in some form? Then you likely already have a good amount of visual material on which to train a generative image model.

Here are some strategies* for creating and inflating datasets from existing bodies of work:
* If you don't have digital copies, take photographs of your work
* Duplicate and rotate the images
* Flip images horizontally and vertically
* Create new images that are zoomed out and zoomed in
* Generate images from frames of your videos
* << What else...? >>

*A model will learn all the visual features of the given dataset. If you create a dataset of dogs and some of them are upsidedown, then expect that your model might generate upsidedown dogs or dog-like creatures with a combination of both upsidedown and rightsideup characteristics. You may or may not want that.

If you source images from online, be sure to consider the following questions:
* Are the images copyright-protected? What are the terms of use?
* If the images contain people, were the individuals notified about how their images would be used and did they give consent? 
* Do the images adhere to RunwayML's [Code of Conduct](https://runwayml.com/coc)?

If you're just curious to try the training process, RunwayML also provides some public datasets to use when you set up a Training Experiment. Skip ahead to Step 3.


## Step 2: Prepare the Dataset
Now that you have a dataset of hundreds or thousands of images, here are some additional items to note:

* To train an generative image model, the images in your dataset must be square. This is a constraint of StyleGAN, the pre-trained model on which your model will be trained. This technique is called Transfer Learning (link to abbove).


* Do you have any images that are corrupted? On indication might that an image is all black or glitched.




RunwayML provides an option to automatically crop your images


Crop happens because you select it
Choose crop
Then resizing happens

Ideally if square that would be better



## Step 3: Start Training Experiment
Launch RunwayML and click either “Browse Models” or “Open Workspaces” to dismiss the starting screen << what is this window called? >> and select **Training Experiments** on the far left navigation.

<< insert GIF here! >>

Currently, Training Experiments are only available with the StyleGAN model. Click to Start Experiment, name the experiment, and click Create.

<< insert GIF here! >>


## Step 4: Select a Dataset
Select one of the public datasets << if they're public, then we should be good digital citizens and list their sources  >> or, to use your own data, simply click the + button or drag your folder of images onto the app. When the data finishes uploading, click Next.

<< insert GIF here! >>


## Step 5: Choose Training Options
There are several options to set before you begin training your model. 

### Choose a starting model
First, you will be prompted to select a Pre-Trained Model on which to train your own model. Your model will be trained on top of another generative image model called [StyleGAN](https://open-app.runwayml.com/?model=runway/StyleGAN) using a technique called Transfer Learning (link to above). Not only does this greatly reduce the amount of training time, it also lowers the amount of images that you need to train your own model. 

StyleGAN was originally trained on 70K images of faces from Flickr, which is why Flickr Faces HQ is listed as the first option. This is not the original StyleGAN dataset; this is the model that resulted from learning all the features in the Flickr dataset. (You can learn more about StyleGAN and how it was trained from the links posted on model's [overview page](https://open-app.runwayml.com/?model=runway/StyleGAN).)

Additional models have already been trained on top of the Flickr Faces HQ, and these Pre-Trained models, also known as Checkpoints, are available for you to select as an alternative starting point. 

Your choice of a Pre-Trained model from which to start your training will impact the following:
* Output Size: The size of the images your model can make (1024 x 1024 pixels, 512 x 512, 256 x 256 << <-- do we have any that create 256x256? ALSO, how will users know which models are which?? >> RunwayML provides several models to upscale the size of images (link to these).
* Speed: Using pre-trained models that generate larger image sizes will take more time than starting with one of the other models. 
* Content: If you are training a model on a dataset of fantastical cartoon characters, you might choose start with pre-trained model of cats or dogs as opposed to bedrooms or cars to create a model that generates images with more cohesive forms and greater fidelity. Or not! Explre the options for different outcomes. 

To view all the pre-trained model options, click Change:
<< again, will all of the models previously trained show up? what if users do not want theirs to be available to the entire community? E.g. If was Helena Sarin, I might not want others to use my artwork / models. >>

<< insert GIF here! >>

### Choose a Crop Option 
Images must be in square format. This is a constraint of StyleGAN, the pre-trained model on which your model will be trained. 

If your images are not square, your options:
* No crop: Each image will be resized to fit the 1:1 square aspect ratio and black borders will be added accordingly. 
* Center: Each image will be cropped to a square, starting at the center with a height that extends to the top and bottom edges.
* Random: Each image will be cropped to a square with random origin point with a height that extends from the top to the bottom edges.

<< insert GIF here! >>

## Set the Number of Training Steps
A good starting point is 5000, but you 

more steps = is likedly to yield a model that can synthesis images with more definitive visual forms

After training completesk you will have a change to review the progress 

Click Start Training.

## Step 6: Train Your Model

estimated wait time
time of training depends on a combination of several factors
checkpoints saved every 500 Training Steps.

## Step 7: Review
When training completes, you can review the progress over the number of Training Steps. 

Click Next 

## Step 8: Use Your Model!
When trainin

Add your Model to a Workspace
When you do, the StyleGAN model will be added to a Workspace. To use your particular model, select in the list of Checklists from options in right pane of the app, and click Run Remotely << notes about cost, including links to subscription plan options >>. 

All the possible images that you model can create will appear in the top window pane. 

<< Watch this vide from Gene Kogan to learn more about the archicture of a generative model like this and how it works blah blah blah >> 



 to augment and extend the style and subject matter of your creative practice