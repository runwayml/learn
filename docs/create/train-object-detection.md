### Train an Object Detection Model

An object detection model is a machine learning algorithm that has learned to recognize and locate objects in images and videos. Provided an input image, an object detection model can produce a collection of bounding boxes (rectangular regions of interest) for each identified object. 

Introduced in version 0.13.0, Object Detection Training allows you to create your own machine learning model to detect custom objects in images and videos. This guide will walk you through the process of training an object detection model.

 - [Step 1: Create your training experiment](#step-1-create-your-training-experiment)
 - [Step 2: Upload your dataset](#step-2-upload-your-dataset)
 - [Step 3: Annotate your dataset](#step-3-annotate-your-dataset)
 - [Step 4: Choose training options](#step-4-choose-training-options)


## Step 1: Create your training experiment

To create a new training experiment, open RunwayML and click on the "Train a model" option. 

<center><img src="assets/images/create/train-models/splashTrain.png" width=750 alt="Train a model"></center>

Click the "Object Detection" button, and type in a name for your training experiment.

<img src="assets/images/create/train-models/selectObjectDetection.png" alt="Select Object Detection">

## Step 2: Upload your dataset

In order to train an object detection model, you will need to prepare an image dataset containing examples of the objects that you'd like to teach your model to identify. You can create a new dataset by dropping an image folder into the collection of datasets, or clicking the "+" button.

?> **How many images should I use?** The ideal number of images for your dataset depends on how many categories of objects you'd like to train your model on. As a general principle, we recommend having at least 25 examples for each object category in your dataset. To improve the performance of your model, make sure to include examples for each object in as many different settings as possible. The more scales, rotations, and illumination conditions your model sees an object in during training, the better its generalization ability becomes, which means it is more likely to correctly identify the same object in images it has never seen before.

?> **Can I train my object detection model on a video?** Yes! You will first need to extract frames from the video by using a third-party tool such as [ffmpeg](https://superuser.com/questions/135117/how-to-extract-one-frame-of-a-video-every-n-seconds-to-an-image/729351). Then you can upload an image folder to RunwayML containing individual frames from your video.

?> **Are there any size limits for datasets I can upload?** Your dataset needs to be less than 5GB in combined file size and less than 25,000 images in total number. We can increase the limit upon request. Just send an email to [support@runwayml.com](mailto:support@runwayml.com).

After your dataset has been uploaded, select your dataset and click "Next" to reach the Annotation view.

<img src="assets/images/create/train-models/selectDataset.png" alt="Select dataset">

## Step 3: Annotate your dataset

Now that you've uploaded your dataset, it's time to annotate the objects in it that you'd like your model to identify. RunwayML provides a visual interface that makes annotating a large number of images quick and easy -- even fun! 

<img src="assets/images/create/train-models/annotationView.png" alt="Go to the Annotation View">

To get started, click "New Annotation Group." An annotation group is a collection of annotated examples for each object category you'd like to recognize. Once you have named your Annotation Group, you will be prompted to input the categories of objects you want to annotate. Type in at least one category to get started annotating - you can always add more categories later.

<center><img src="assets/images/create/train-models/initialCategories.png" alt="Select initial categories for your annotation group"></center>

?> **How many categories should I add?** The number of categories you should use depends on the dataset and use-case for the model. For example, if you want to locate birds in an image without needing to know the exact species of each bird, then you can have just one category that is "Bird." If you want to identify the kind of bird in the image in addition to locating it, then you can have a different category for each species. Keep in mind that we currently impose a maximum limit of 50 categories. We can increase the limit upon request. Just send an email to [support@runwayml.com](mailto:support@runwayml.com).

You can now get started annotating images in your dataset. There are a few different sections in this interface, so let's explore them one by one:

<img src="assets/images/create/train-models/annotationEditor.png" alt="Edit annotations">

1) **Title and Navigation**: Navigate back to the Annotation view when you've finished annotating or if you would like to continue annotating later. Before clicking "Close," make sure that your progress has been saved (you should see the "All your changes are saved" text to the "Close" button). If you have unsaved changes, either **Submit** the current bounding boxes or **Reset** them to the saved state.

2) **Files**: A list of all the image files present in the dataset, with an indication of whether they have been annotated or not. 

3) **Categories**: All the categories that you've added for this annotation group. Clicking on a category will make it the active category that will be used when drawing a new bounding box in the annotation area. You can rename or delete any of the categories at any time. *Note: Deleting a category also deletes all bounding boxes associated with that category.*

3) **Annotations in image**: View the current annotations for this image, with the ability to delete any of them with the "Trash" icon.

4) **Submit and Reset**: Submit (hotkey: Space) the annotations for the current image in the dataset, which will save all bounding boxes for this image remotely, or Reset (hotkey: Q) the local state to the bounding boxes since last submission.

5) **Annotation area**: Draw or edit bounding boxes for the currently selected image in the dataset.

?> **Any tips for drawing bounding boxes around the subjects?** The main thing to keep in mind is that the model will learn to generate bounding boxes similar to the ones that you've drawn during the annotation step. For example, if you've annotated your dataset with only bounding boxes of approximately square shape, then your trained model will only generate square or almost-square bounding boxes. Similarly, if you always draw bounding boxes that are slightly larger than the subjects you're annotating, the generated bounding boxes will also tend to be that way. In general, we recommend deciding on an annotation style early on and sticking with it, to ensure that your model's predictions will be consistent.

?> **Should I submit files without any bounding boxes?** Yes! If there are no objects to annotate in an image, you can still submit it to mark it as a negative example.


## Step 4: Choose training options

RunwayML greatly reduces the amount of time needed to train your own generative image model by using using a technique called [Transfer Learning](https://en.wikipedia.org/wiki/Transfer_learning). With this technique, an existing pre-trained neural network model called [YOLO](https://pjreddie.com/darknet/yolo/) (You Only Look Once) is re-trained on your dataset. RunwayML supports the following versions of YOLO:

* `YOLOv4`: The latest version of the YOLO neural network model. It is a state-of-the-art object detection model that balances speed and accuracy, and takes around 2 hours to train for 5,000 steps.

* `YOLOv3-Tiny`: A lightweight version of the YOLO architecture. This version is ideal for real-time applications and deployment in mobile applications. It is also twice as fast to train, taking around an hour for 5,000 steps.

If you're unsure which pre-trained model you should use, we recommend starting with the default `YOLOv4`. You can also select a pre-trained model from a previous training experiment as your starting model.

?> **How many steps should I train for?** The more steps you train your model for, the better it will become at predicting bounding boxes for objects in your images. As a general principle, it is recommended to train your model at least 5,000 steps, or at least 1,000 steps for each category that you’ve annotated, whichever number is greatest. You can always continue training your model after your training experiment has ended, or stop your training experiment before it has ended if you’re seeing good results earlier than you expected.

?> **How much does training cost?** Training an object detection model requires a subscription to the RunwayML Creator Plan. You can train your first model for free, and subsequent training experiments cost $0.005 per step. You can use the "Estimated Cost" option under the steps selector to determine exactly how much your training experiment will cost. You can find more information about RunwayML's pricing [here](https://support.runwayml.com/en/articles/3000086-how-much-does-runwayml-cost).
