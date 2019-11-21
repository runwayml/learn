# Train Your Own Models
<br>

?>The feature to train your own models is currently available to small group of beta testers. Please [contact us](https://runwayml.com/training-access) if you are interested in testing and providing feedback on this new feature.

🚧 This page will be updated regularly as beta testers provide feedback on the training process. 

## Overview
In addition to publishing open source, pre-trained machine learning models in the RunwayML platform, you can now train your own models! This guide will walk you through the steps of training a model, but first, here's a quick FAQ to provide some context.

### What is a model and what does it mean to train one?
Generally speaking, a model is a machine learning algorithm that has learned patterns within a given dataset. Instead of being explicitly programmed, it develops its own parameters for how to represent—or model—those patterns to make predictions about new data (such as to detect objects in a video) or generate completely new content that mimics the original data on which it was trained (such as synthesize images from a collection of paintings). 

Training is the process of providing a machine learning algorithm with a dataset to learn patterns in the form of [features](https://en.wikipedia.org/wiki/Feature_(machine_learning)). RunwayML makes training very easy: all you need to do is to supply your own dataset (although we have some available for you to try) and determine the number of steps that the algorithm should take to learn the features. During each step, the model learns a little bit more about the features in your dataset. For a demonstration of the visual patterns a machine learning model might find, watch Gene Kogan's quick video on [What Convolutional Neural Networks See](https://experiments.withgoogle.com/what-neural-nets-see).

### What kind of model can I train?
Model training is an experimental feature 🧪in RunwayML, and at the time of this writing (November 2019), you can only train a generative model to synthesize images. Support for additional model types will be added in the future. 

### What kind of dataset do I need?
To train a generative image model, you need a collection of images. Suggestions for the amount, as well as considerations for how to source and prepare those images are below. RunwayML also provides some public datasets to try.

### How long will it take to train my model?
The time it takes to train a model depends on a combination of many factors, including but not limited to the type of machine learning algorithm (there are algorithms of varying complexity for working with images, words, or sounds) and the number of training steps. 

RunwayML greatly reduces the amount of time needed to train your own generative image model by using using a technique called [Transfer Learning](https://en.wikipedia.org/wiki/Transfer_learning). With this technique, an existing pre-trained model called [StyleGAN](https://open-app.runwayml.com/?model=runway/StyleGAN) is retrained on your dataset. StyleGAN was trained on a massive amount of images (70,000!), and Transfer Learning leverages all of the [image features](https://en.wikipedia.org/wiki/Feature_(computer_vision)) it learned from the original data to speed up the process of learning features in your image dataset. Not only does this greatly reduce training time, it also reduces the number of images that you need to train your own model. You can learn more about StyleGAN and how it was orginally trained from the links posted on the model's [overview page](https://open-app.runwayml.com/?model=runway/StyleGAN). 

Even with Transfer Learning, it's not unusual for training to take at least several hours. 

?> If you are a Training Experiments beta tester and you have a Free Plan, training time is limited to a total of five hours. **Subscribe to the Creator Plan** in the [RunwayML User Dashboard](https://account.runwayml.com/) for unlimited training access. With or without the Creator Plan, training time uses [credits](https://support.runwayml.com/en/articles/2984968-adding-credits). 

### What can I do with my newly-trained model?
During training, your model learns to produce new images that look like the ones in your dataset. When training is complete, the model will generate a seemingly infinite number of synthetic images that appear as if they came from the dataset itself. The space of all new possible images that your model can create is called the latent space, which you can explore when you [run your model](how-to/use-models?id=step-7-run-the-model). Happy image making!

Here are the steps to get started...

## Step 1: Create a Dataset

### Of what?
To train your own generative image model, you need to create a dataset from a collection of images in a folder on your computer. Images similar in content and style will produce a model that is better able to synthesize images that are reminiscent of those in the original dataset. This offers great potential for augmenting and extending creative work, especially as a tool for quickly iterating through visual ideas. A model trained from a varied collection of images that you never deleted from your mobile phone, however, is not likely to perform as well.

### How much? 
RunwayML Training Experiments will accept individual datasets that total less than 5GB in combined file size and less than 25,000 images in total number. That's a lot, we know. Generally, the more data you collect, the better your model will be at generating synthetic images that look like they came from your original dataset, but a starting recommendation is to gather around 500-5,000 images. Some users, however, have been pleased with the results of a model trained on as few as 300 images.

### From where?
Are you an illustrator, painter, photographer, architect, set designer, graphic designer, fashion designer, textile artist, [asemic writer](https://en.wikipedia.org/wiki/Asemic_writing), musician who reads sheet music, or someone who works with or is inspired by visible marks in some form? Then you likely already have a good amount of visual material on which to train a generative image model.

Here are some strategies* for creating (or inflating) datasets from existing bodies of work:
* If you don't have digital copies, take photographs of your work!
* Duplicate and rotate the images.
* Flip images horizontally and vertically.
* Create new images that are zoomed out and zoomed in.
* Generate images from frames of your videos.
* If you're comfortable with creative coding tools like [Processing](https://processing.org/) or [p5.js](https://p5js.org/) (there are many others, too!), can you automatically generate images? 
* If you're technically-inclined, there are also use tools for scraping (automatically extracting) images from websites.

*A model will learn all the visual features of the given dataset. If you create a dataset of dogs and some of them are upsidedown, then expect that your model might generate upsidedown dogs or dog-like creatures with a combination of both upsidedown and rightsideup characteristics. You may or may not want that.

?>If you source images from online, be sure to consider the following questions:<br>
• What are the images' terms of use? <br>
• If you intend to scrape images, is that technique in keeping with the website's terms of service? <br>
• If the images contain people, were the individuals notified about how their images would be used and did they give consent? <br>
• Do the images adhere to RunwayML's [Code of Conduct](https://runwayml.com/coc)?

If you're just curious to try the training process, RunwayML also provides some public datasets to use when you create a Training Experiment. The images in these datasets were sourced from Flickr and in the public domain.

### How should I prepare my dataset?
Once you have a dataset of hundreds or thousands of images, here are some additional items to note:

* Are any images corrupted? One indication might be that an image is all black, glitched, or cannot be opened.
* To train an generative image model, the images in your dataset must be square. This is a constraint of StyleGAN, the pre-trained model that will be used to train your model (see above). RunwayML provides an option to automatically crop your images when you start a Training Experiment (see Step 4).


## Step 2: Create a Training Experiment
Launch RunwayML and click **Train a Model** from the splash screen. The training directory is also available from the left navigation. 

Currently, Training Experiments are only available with the StyleGAN model. Click to **Start Training**, give it a title, and then click **Create**.

<img src="assets/images/create/train-models/startTrainingExperiment.gif" alt="screen recording showing how to start a training experiment">


## Step 3: Select the Dataset
Select one of the public datasets or, to use your own data, simply click the **+ button** or drag in your folder of images. 
Your dataset will then be compressed and uploaded. This can take a while, but click **Next** when it finishes. 

?> Any dataset you upload will be private to your account. 

<img src="assets/images/create/train-models/selectDataset.gif" alt="screen recording showing how to select a dataset">


## Step 4: Select Training Options
There are several options to consider before you begin training your model. 

### Pick a Pre-Trained Model
Start by selecting a Pre-Trained Model. Training your model actually retrains the [StyleGAN](https://open-app.runwayml.com/?model=runway/StyleGAN) model on your own dataset using a technique called Transfer Learning (see above). Not only does this greatly reduce training time, it also reduces the number of images that you need to train your own model. 

StyleGAN was originally trained on 70,000 images of faces from Flickr, which is why Flickr Faces HQ is listed as the first option. StyleGAN has been retrained on a number of other datasets, and these additional Pre-Trained Models, also known as Checkpoints, are available to select as an alternative starting point. (You can learn more about StyleGAN and how it was trained from the links posted on the model's [overview page](https://open-app.runwayml.com/?model=runway/StyleGAN).)


Your choice of a Pre-Trained Model from which to start your training will impact the following:
* **Content**: 
    * If you are training a model on a dataset of fantastical cartoon characters, you might select a Pre-Trained Model of cats or dogs as opposed to bedrooms or cars to create a model that generates images with more cohesive forms and greater fidelity. 
    * Or not! Have fun exploring the options for different results: there are can be unexpected visual outcomes from training a model that is significantly different from your dataset, especially midway through the training process.
* **Output Size**: 
    * The Pre-Trained Models generate images at 1024x1024 pixels, 512x512 pixels, or 256x256 pixels, and the one you choose will impact the size of the images that your model will make once training is complete. The default Pre-Trained model option, Flickr Faces HQ, is the only model that outputs images at 1024x1024 pixels. 
    * If you prefer to pick Pre-Trained Model for the content, but the output size is too small, know that RunwayML provides several models to quickly [upscale images](create/transform?id=upscale-images), and you can easily [chain](how-to/chain-models-together) your newly-trained model to one of those when you run it in a Workspace.
* **Training Time**: 
    * In general, the more similar the Pre-Trained Model’s images are to the images in your dataset, the faster it will train. 
    * In addition, using Pre-Trained Models that generate larger image sizes will take significantly more time than using models that produce smaller images sizes. The estimated training time will update according to a combination of the Pre-Trained Model you select and the number of Training Steps you set (learn more below). 
    
?> If you are a Training Experiments beta tester and you have a Free Plan, training time is limited to a total of five hours. **Subscribe to the Creator Plan** in the [RunwayML User Dashboard](https://account.runwayml.com/) for unlimited training access. With or without the Creator Plan, training time uses [credits](https://support.runwayml.com/en/articles/2984968-adding-credits). If your account does not have enough [credits](https://support.runwayml.com/en/articles/2984968-adding-credits), your Training Experiment will stop before training completes. 

To view all the Pre-Trained Model options, click **Change**:

<img src="assets/images/create/train-models/setPreTrainedModel.gif" alt="screen recording showing how to select a dataset">

### Choose a Crop Option 
Images must be in a square format. This is a constraint of StyleGAN, the pre-trained model that will be used to train your model.

If your images are not square, these are your options:
* **Center**: This is a good choice if the subject of your images usually appears in the center.
* **Random**: This is a good choice if the subject of your images can appear anywhere in the frame.
* **No crop**: Each image will be resized to fit the 1:1 square aspect ratio. 

<img src="assets/images/create/train-models/cropOptions.jpg" alt="screen grabs of three different crop options">

### Set the Training Steps
During each Training Step, the model learns a little bit more about the visual patterns, or features, it finds in your dataset. 

Determining an effective number of training steps is a bit of a moving target. Too few and your model might not be able to synthesize images with coherent visual forms that are reminiscent of those in the original dataset. Too many and your model will stop improving, not learning anything new, and possibly produce worse images or images look the same.

The maximum number of Training Steps is 25,000, but a good starting point is 3,000. During and after training, you can review the model's learning progress at various steps. 

The higher the number of Training Steps, the longer it will take to train your model. The estimated training time will update according to a combination of the Pre-Trained Model you select and the number of Training Steps you set. If your account does not have enough [credits](https://support.runwayml.com/en/articles/2984968-adding-credits), your Training Experiment will stop before training completes.

Enter the **number of Training Steps** and click **Start Training** to continue.

<img src="assets/images/create/train-models/trainingSteps.png" alt="screen grab of 3000 training steps" width=40%>


## Step 5: Train Your Model
At the start of the training process, all your images will be pre-processed and prepared for training. After this completes, an estimated amount of training time will post under the **ETA Approx** status on the right. Make sure that your account has enough [credits](https://support.runwayml.com/en/articles/2984968-adding-credits) for the estimated training time, otherwise your training experiment will stop.

?> The training process occurs on a Remote GPU in RunwayML's cloud infrastructure, and it's not unsual for the process to take several hours. During this time, it's okay to use other features in RunwayML, close the application, or even turn off your computer and check back later. 

?> If you are a Training Experiments beta tester and you have a Free Plan, training time is limited to a total of five hours. **Subscribe to the Creator Plan** in the [RunwayML User Dashboard](https://account.runwayml.com/) for unlimited training access. With or without the Creator Plan, training time uses [credits](https://support.runwayml.com/en/articles/2984968-adding-credits). If your account does not have enough [credits](https://support.runwayml.com/en/articles/2984968-adding-credits), your Training Experiment will stop before training completes. 

<img src="assets/images/create/train-models/trainingProcess.jpg" alt="screen grab from model training in progress">

During training and after it completes, you can review the progress at various Training Steps, save a sample image from a particular step, as well as export a progress video. Click **Next** to continue when the training process concludes. 

<img src="assets/images/create/train-models/trainingEnded.jpg" alt="screen grab showing when training has ended">

## Step 6: Use Your Model
Hooray! Your model is now ready to use. Click **Save to My Models**. 

<img src="assets/images/create/train-models/trainingSave.jpg" alt="screen grab showing training review">


You will be taken to your model's overview page. On the overview page, click **Settings** for options to **Make Model Public** on the RunwayML platform (this is permanent), **Rename Model**, or **Delete Model**. 

<img src="assets/images/create/train-models/modelOverview.jpg" alt="screen grab showing model settings">

To run your model, click **Add to Workspace**. A new Workspace will be created during this step if you do not already have one. Set the model's input to **Vector**, the output to **Preview**, and click **[Run Remotely](how-to/use-models?id=step-7-run-the-model)** to explore all the possible images it can generate. What will you discover?!

<img src="assets/images/create/train-models/runningModel.gif" alt="screen grab showing adding model to workdpace">

?> 📽 To learn more about how generative models work, including StyleGAN, watch this [quick video](https://www.youtube.com/watch?v=f-cCpVGoxhY) from Gene Kogan. 

?> 📽 To learn even more about StyleGAN, follow up with this [Coding Traing tutorial](https://www.youtube.com/watch?v=vEetoBuHj8g) from Daniel Shiffman.
