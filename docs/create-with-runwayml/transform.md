# Transform

The pre-trained models in this category provide options to transform your original content in various ways. Though some models below are described with "generative" qualities, all models here modify input to produce a transformed output. Visit our [gallery of projects](https://runwayml.com/madewith/) for ideas about how to use these models.


> **Note**: models are added to the RunwayML app often, and this page does not necessarily respresent the full list. Contributions, demos, and tutorials are welcome here!

## Style Transfer
| Model | Description | [Networking Examples Available](https://learn.runwayml.com/#/networking/examples) |
| :--- | :---| :--- |
| [Adaptive Style Transfer](https://open-app.runwayml.com/?model=runway/Adaptive-Style-Transfer)  | Repaint images in the styles of famous painters ([Tutorial](tutorials/tutorial_style_transfer.md))|Processing |
| [AdaIN-Style-Transfer](https://open-app.runwayml.com/?model=reiinakano/AdaIN-Style-Transfer) | Real-time style transfer | Processing| 
| [Arbitrary-Style-Transfer](https://open-app.runwayml.com/?model=runway/Arbitrary-Image-Stylization) | Real-time style transfer |Processing  |
| [Fast Photo Style](https://open-app.runwayml.com/?model=reiinakano/FastPhotoStyle) | A Closed-form Solution to Photorealistic Image Stylization |Processing |
| [Fast-Style-Transfer](https://open-app.runwayml.com/?model=genekogan/Fast-Style-Transfer) | Stylize images in the styles of famous painters | openFrameworks Addon, p5.js, Processing |
| [Style2paints](https://open-app.runwayml.com/?model=zaid/style2paints) | Automatic Sketch Colorization |Processing |


## Image Translation
| Model | Description | [Networking Examples Available](https://learn.runwayml.com/#/networking/examples) |
| :--- | :---| :--- |
| [CycleGAN](https://open-app.runwayml.com/?model=reiinakano/CycleGAN) | Image-to-image translation without labeled data | p5.js, Processing|
| [Pix2Pix](https://open-app.runwayml.com/?model=reiinakano/Pix2Pix) | Image-to-image translation with labeled data | openFrameworks Addon, Processing|
| [Pix2PixHD-Facemarks2Portrait](https://open-app.runwayml.com/?model=yining/pix2pixHD-Facemarks2Portrait) | Generate a portrait image from a face landmarks image ([Interactive Example](https://experiments.runwayml.com/synthetic_postcard/)) |Processing |
| [UGATIT](https://open-app.runwayml.com/?model=runway/UGATIT) | Official Tensorflow implementation of U-GAT-IT: Unsupervised Generative Attentional Networks with Adaptive Layer-Instance Normalization for Image-to-Image Translation | Processing |


## Images → Semantic Image Maps
Semantic Image Segmentation

| Model | Description | [Networking Examples Available](https://learn.runwayml.com/#/networking/examples) |
| :--- | :---| :--- |
| [DeepLab](https://open-app.runwayml.com/?model=genekogan/deeplab) | Extract semantic maps from objects in images | Processing |
| [DeepLabV3](https://open-app.runwayml.com/?model=runway/DeepLabV3) | Deep labeling for semantic image segmentation | Processing |
| [Face-Parser](https://open-app.runwayml.com/?model=anastasis/Face-Parser) | A pretrained model for parsing facial components from an image | Processing |


## Semantic Image Maps → Images
Semantic Image Synthesis

| Model | Description | [Networking Examples Available](https://learn.runwayml.com/#/networking/examples) |
| :--- | :---| :--- |
| [SPADE-COCO](https://open-app.runwayml.com/?model=runway/spade-coco) | Transform semantic image maps into images | JavaScript, Processing |
| [SPADE-FACE](https://open-app.runwayml.com/?model=sree_harsha/spade-face) | Transform semantic image maps into images of faces| |
| [SPADE-Landmarks](https://open-app.runwayml.com/?model=genekogan/SPADE-Landscapes) | Transform semantic image maps into landscape images | Processing |


## Image Editing
| Model | Description | More |
| :--- | :---| :--- |
| [DeepFill](https://open-app.runwayml.com/?model=runway/DeepFill) | Remove objects from photos | Processing|
| [DeRaindrop](https://open-app.runwayml.com/?model=zaid/DeRaindrop) | Remove raindrops from photos| Processing|
| [Deep-Portrait-Image-Relighting](https://open-app.runwayml.com/?model=sree_harsha/Deep-Portrait-Image-Relighting) | Generate relighted image by using a single portrait image and a target lighting | |
| [Edge-connect](https://open-app.runwayml.com/?model=zaid/edge-connect) | Generative Image Inpainting with Adversarial Edge Learning | Processing |
| [Image-Inpainting-GMCMM](https://open-app.runwayml.com/?model=anastasis/Image-Inpainting-GMCNN) | Image Inpainting via Generative Multi-column Convolutional Neural Networks | Processing|
| [PhotoSketch](https://open-app.runwayml.com/?model=runway/PhotoSketch]) | Turn images into contour drawings | openFrameworks Addon, p5.js, Processing |


## Colorize B/W Media
| Model | Description | [Networking Examples Available](https://learn.runwayml.com/#/networking/examples) |
| :--- | :---| :--- |
| [Automatic-Colorization](https://open-app.runwayml.com/?model=runway/Automatic-Colorization)| Colorize black and white images and videos ([Tutorial](tutorials/tutorial_colorizing_video.md))| |
| [DeOldify](https://open-app.runwayml.com/?model=reiinakano/DeOldify) | Colorize and restore old images | Processing|


## Upscale Images
| Model | Description | [Networking Examples Available](https://learn.runwayml.com/#/networking/examples) |
| :--- | :---| :--- |
| [ESRGAN](https://open-app.runwayml.com/?model=runway/ESRGAN) | 4x ([Tutorial](tutorials/tutorial_esrgan.md))| openFrameworks Addon, Processing, TouchDesigner |
| [Image-Super-Resolution](https://open-app.runwayml.com/?model=runway/Image-Super-Resolution) | 2x |Processing |

## 2D Masking
| Model | Description | [Networking Examples Available](https://learn.runwayml.com/#/networking/examples) |
| :--- | :---| :--- |
| [MaskRCNN](https://open-app.runwayml.com/?model=runway/MaskRCNN) | Cut out objects from images |Processing |
| [Human-Segmentation](https://open-app.runwayml.com/?model=runway/Human-Segmentation) | Segment humans from images and videos | |


## 3D Modeling
| Model | Description | [Networking Examples Available](https://learn.runwayml.com/#/networking/examples) |
| :--- | :---| :--- |
| [3D Dense Face Alignment](https://open-app.runwayml.com/?model=matthewbay/3ddfa) | 3D face alignment | |
| [DenseDepth](https://open-app.runwayml.com/?model=runway/DenseDepth) | Predict depth from 2D images| Processing |
| [DensePose](https://open-app.runwayml.com/?model=runway/DensePose) | Detect humans in 2D images and turn them into 3D surface models | |




