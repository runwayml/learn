# Rotoscoping with Green Screen

<img src="assets/images/video-tools/green-screen/banner.png" alt="Banner image of Green Screen">

?> Click [here]() for a video walk-through of Green Screen.

## What is Green Screen? 

Green Screen is the first of our video tools centered around cutting out
objects from videos, known as rotoscoping. This is the bread-and-butter of video manipulation. 
Once you have a cutout of your video, you can swap out the background,
display text behind it, or even selectively apply visual effects to the region.

<img src="assets/images/video-tools/green-screen/composite.gif" alt="Sample motion graphics ouptut">

Most tools for rotoscoping involve painstakingly going frame-by-frame
and highlighting the border of objects. There's a lot of subtle tricks needed
to get a good result. We think this should be a lot easier. Here are the steps
to get started...

## Step 1: Clip selection

Open Green Screen by clicking on **Video Tools** under the media sidebar. Now
select an asset by opening the **Assets** sidebar. All of your exports from
other Runway tools appear here. If you want to use an asset from your computer
or external software, you can simply drag and drop onto the interface to get
started.

<img src="assets/images/video-tools/green-screen/clip-selection.gif" alt="Gif opening the assets bar">

?> Our tool is designed to track individual objects throughout a scene. If you
have lots of footage to cut, it's best to trim into clips with relatively
consistent camera angles and lighting conditions, and then edit each one with
Green Screen individually. If you want to track two separate objects in the
same video, we recommend you use Green Screen twice to track them separately.

## Step 2: Creating keyframes, previewing, and refining

To start off the process we're, seek to an initial frame which contains
the desired object in clear view. Using clicks you can indicate which parts of
the frame contain the target. The toolbar above the timeline allows you to
switch between **Include** clicks which expand the mask to the clicked location
and **Exclude** clicks which retract the mask. 

Now that you have an initial mask, by clicking on **Preview**, you can see what
would happen if you were to propagte the mask to the rest of the video.  You
can also click on the timeline or use the arrow keys to check the results on a
frame-by-frame basis.

<img src="assets/images/video-tools/green-screen/click-and-propagate.gif" alt="Gif clicking to generate initial mask and then propagating">

?> You'll notice that there are regions of video where masking can be improved.
The goal is to create a set of keyframes from which Green Screen can estimate
the mask for the whole video. A new keyframe is usually neded when the target
changes apperance (e.g. a dancer turns around or a body part appears for the
first time in the video).

Now you rinse-and-repeat, creating keyframes where the current results are
lacking, and then previewing the updated results. Depending on the amount of
movement and background complexity, Green Screen may need just a pair of
keyframes or one every couple of seconds.

## Step 3: Exporting the result

Once you're satisfied with the mask, click **Export** to output a video file.
You can change the name of the video, and select a chroma-key background.

<img src="assets/images/video-tools/green-screen/export.gif" alt="Gif showing the export process">

The output will appear in your **Assets**, from which you can export the file
into other software to add visual effects.

## Bonus: compositing with Premiere

Using our exported file in any video editor or compositor is quite easy. Here
we use Adobe Premiere, but similar effects are doable across most software.
