# Train Your Own Models

## Overview
In addition to publishing open source, pre-trained machine learning models in the RunwayML platform, you can now train your own models directly inside of the app! This guide will walk you through the steps of training a model, but first, here's a quick FAQ to provide some context to help you get started.

### What is a model and what does it mean to train one?
Generally speaking, a model is a machine learning algorithm that has learned patterns within a given dataset. Instead of being explicitly programmed, it develops its own parameters for how to represent—or model—those patterns to make predictions about new data (such as to detect objects in a video) or generate completely new content that mimics the original data on which it was trained (such as synthesizing images from a collection of paintings). 

Training is the process of providing a machine learning algorithm with data to learn patterns in the form of features. RunwayML makes training very easy: all you need to do is to supply your own dataset (although we have some available for you to try) and determine the number of steps the algorithm should take to learn the features. During each step, the algorithm adjusts its values to output better results. For a technical demonstration of the visual patterns a machine learning model might learn, watch Gene Kogan's quick video on [What Convolutional Neural Networks See](https://experiments.withgoogle.com/what-neural-nets-see).

### What kind of model can I train?
Model training is an experimental feature 🧪in RunwayML, and at the time of this writing (November 2019), you can only train a generative model for synthesizing images. Support for additional model types will be added in the future. 

### What kind of dataset do I need?
To train a generative image model, you need a collection of images. Suggestions for the amount, as well as considerations for how to source and prepare those images are below. RunwayML also provides some public datasets to try.

### How long will it take to train my model?
The time it takes to train a model depends on a combination of many factors, including but not limited to the type of machine learning algorithm (there are algorithms of varying complexity for working with images, words, or sounds) and the number of training steps. 

RunwayML greatly reduces the amount of training time needed to train your own generative image model by using using a technique called Transfer Learning. With this technique, an existing pre-trained model called [StyleGAN](https://open-app.runwayml.com/?model=runway/StyleGAN), is retrained on your dataset. StyleGAN was trained on a massive amount of images (70,000!), and Transfer Learning leverages all of the features it learned from the original data to speed up the process of learning features in your image dataset. Not only does this greatly reduce training time, it also reduces the number of images that you need to train your own model. You can learn more about StyleGAN and how it was orginally trained from the links posted on the model's [overview page](https://open-app.runwayml.com/?model=runway/StyleGAN). 

Even with Transfer Learning, it's not unusual for training to last at least several hours. 

### What can I do with my newly-trained model?
During training, your model learns to produce new images that look like the ones in your dataset. When training is complete, the model can be used to generate an infinite number of synethetic images that appear as if they came from the dataset itself. 

Because your model is the result of retraining the StyleGAN model using the Transfer Learning technique (see above), your model will appear under the list of checkpoints when you add StyleGAN to a workspace. The space of all possible new images that your model can create is called the latent space, which you can explore when you select your model's checkpoint and [run StyleGAN](https://learn.runwayml.com/#/how-to/use-models?id=step-7-run-the-model). Happy image making!

Here are the steps to get started...

## Step 1: Create a Dataset
To train your own generative image model, you need to create a dataset from a collection of images in a folder on your computer. Images similar in content and style will produce a model that is better able to synthesize images that are reminiscent of the originals. This offers great potential for augmenting and extending creative work, especially as a tool for iterating on visual ideas. A model trained from a varied collection of images that you never deleted from your mobile phone, however, is not likely to perform as well.

### How much? 
RunwayML Training Experiments will accept individual datasets that total less than 5GB in combined file size and less than 25K images in total number. That's a lot, we know. Generally, the more data you collect, the better your model will be at generating synthetic images that look like they came from your original dataset, but a starting recommendation is to gather around 500-5,000 images. Some users, however, have been pleased with the results of a model trained on as few as 300 images.

### From where?
Are you an illustrator, painter, photographer, architect, graphic designer, fashion designer, textile artist, [asemic writer](https://en.wikipedia.org/wiki/Asemic_writing), musician who reads sheet music, or someone who works with visual marks in some form? Then you likely already have a good amount of visual material on which to train a generative image model.

Here are some strategies* for creating (or inflating) datasets from existing bodies of work:
* If you don't have digital copies, take photographs of your work!
* Duplicate and rotate the images.
* Flip images horizontally and vertically.
* Create new images that are zoomed out and zoomed in.
* Generate images from frames of your videos.
* If you're comfortable with creative coding tools like [Processing](https://processing.org/) or [p5.js](https://p5js.org/) for example (there are many others, too!), can you automatically generate images? 
* Those comfortable with programming might also use tools for scraping (automatically extracting) images from websites.

*A model will learn all the visual features of the given dataset. If you create a dataset of dogs and some of them are upsidedown, then expect that your model might generate upsidedown dogs or dog-like creatures with a combination of both upsidedown and rightsideup characteristics. You may or may not want that.

?>If you source images from online, be sure to consider the following questions:<br>
• What are the images' terms of use? <br>
• If you intend to scrape images, is that technique in keeping with the website's terms of service? <br>
• If the images contain people, were the individuals notified about how their images would be used and did they give consent? <br>
• Do the images adhere to RunwayML's [Code of Conduct](https://runwayml.com/coc)?

If you're just curious to try the training process, RunwayML also provides some public datasets to use when you create a Training Experiment.

### How should I prepare my dataset?
Once you have a dataset of hundreds or thousands of images, here are some additional items to note:

* Are any images corrupted? On indication might be that an image is all black, glitched, or cannot be opened.
* To train an generative image model, the images in your dataset must be square. This is a constraint of StyleGAN, the pre-trained model on which your model will be trained (see above). RunwayML provides an option to automatically crop your images when you start a Training Experiment (see Step 4).


## Step 2: Create a Training Experiment
Launch RunwayML and click **Train a Model** from the splash screen. The training directory is also available from the left navigation. 

Currently, Training Experiments are only available with the StyleGAN model. Click to **Start Experiment**, give it a title, and then click **Create**.

<< insert GIF here! >>


## Step 3: Select the Dataset
Select one of the public datasets or, to use your own data, simply click the + button or drag your folder of images onto the app. Your dataset will then be compressed and uploaded (this can take a while). When this finishes, click **Next**.

<< insert GIF here! >>


## Step 4: Select Training Options
There are several options to set before you begin training your model. 

### Pick a Pre-Trained Model
First, select a Pre-Trained Model on which to train your own model. Training your model retrains the [StyleGAN](https://open-app.runwayml.com/?model=runway/StyleGAN) model on your own dataset using a technique called Transfer Learning (see above). Not only does this greatly reduce training time, it also reduces the number of images that you need to train your own model. 

StyleGAN was originally trained on 70,000 images of faces from Flickr, which is why Flickr Faces HQ is listed as the first option. StyleGAN has been retrained on a number of other datasets, and these additional Pre-Trained Models, also known as Checkpoints, are available for you to select as an alternative starting point. (You can learn more about StyleGAN and how it was trained from the links posted on the model's [overview page](https://open-app.runwayml.com/?model=runway/StyleGAN).)


Your choice of a Pre-Trained Model from which to start your training will impact the following:
* **Content**: If you are training a model on a dataset of fantastical cartoon characters, you might select a Pre-Trained Model of cats or dogs as opposed to bedrooms or cars to create a model that generates images with more cohesive forms and greater fidelity. Or not! Have fun exploring the options for different outcomes. In general, the more similar the Pre-Trained Model’s images are to the images in your dataset, the faster it will train. But there are can be interesting outcomes from training a model that is significantly different than your dataset, especially midway through the training process.
* **Output Size**: The Pre-Trained Models generate images at 1024x1024 pixels, 512x512 pixels, or 256x256 pixels, and the one you choose will impact the size of the images that your model will make once training is complete. The default Pre-Trained model option, Flickr Faces HQ, is the only model that outputs images at 1024x1024 pixels. (If you prefer to pick Pre-Trained Model for the content, but the output size is too small, know that RunwayML provides several models to quickly [upscale image size](https://learn.runwayml.com/#/create-with-runwayml/transform?id=upscale-images), and you can [chain](https://learn.runwayml.com/#/how-to/chain-models-together) your newly-trained model to one of those.)
* **Training Time**: Using Pre-Trained Models that generate larger image sizes will take significantly more time than using models that produces smaller images sizes. Estimated training time will update according to a combination of the Pre-Trained Model you select and the number of Training Steps (learn more below). If your account does not have enough credits, your Training Experiment might stop before training completes.

To view all the Pre-Trained Model options, click **Change**:


<< insert GIF here! >>

### Choose a Crop Option 
Images must be in square format. This is a constraint of StyleGAN, that model that will be retrained on your image dataset to create your new model.

If your images are not square, these are your options:
* No crop: Each image will be resized to fit the 1:1 square aspect ratio and black borders will be added accordingly. 
* Center: This is a good choice if the subject of your images usually appears in the center.
* Random: This is a good choice if the subject of your images can appear anywhere in the frame.

<< insert GIF here! >>

### Set the Training Steps
During each Training Step, the model learns a little bit more about the visual patterns, or features, it finds in the dataset. 

Determining an effective number of training steps is a bit of a moving target. Too few and your model might not be able to synthesize images with coherent visual forms that are reminiscent of those in the original dataset. Too many and your model will stop improving, not learning anything new, and possibly produce worse images.

The maximum number of Training Steps you can set is 25,000, but a good starting point is 5,000 steps. After training completes, you can review the model's learning progress at various steps. 

The higher the number of Training Steps, the longer it will take to train your model. Estimated training time will update according to a combination of the Pre-Trained Model you select and the number of Training Steps. If your account does not have enough credits, your Training Experiment might stop before training completes.

Click **Start Training** to continue.

<< insert image here! >>


## Step 5: Train Your Model
At the start of the training process, all your images will be pre-processed, cropped and resized. After this completes, an estimated amount of training time will post under the ETA status on the right. 

The actual training process occurs on a Remote GPU in RunwayML's cloud infrastructure and it's not unsual for the process to take several hours. During this time, it's okay to use other features in RunwayML, close the application, or even turn off your computer and check back later. 

Versions of your model will be saved every 500 Training Steps, also known as Checkpoints. 


## Step 6: Use Your Model
When training completes, you can review the progress at various Training Steps. 

Click Next 

Add your Model to a Workspace
When you do, the StyleGAN model will be added to a Workspace. To use your particular model, select in the list of Checklists from options in right pane of the app, and click Run Remotely << notes about cost, including links to subscription plan options >>. 

All the possible images that you model can create will appear in the top window pane. 

<< Watch this vide from Gene Kogan to learn more about the archicture of a generative model like this and how it works blah blah blah >> 


 to augment and extend the style and subject matter of your creative practice