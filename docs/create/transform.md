# Transform Content

You can use models directly of inside the RunwayML app or interact with models through [network protocols](https://learn.runwayml.com/#/how-to/network). The pre-trained models in this category provide options to transform your original content in various ways. Though some models are listed with *generative* attributes, all models here modify input to produce a transformed output. Visit [Projects Made with RunwayML](https://runwayml.com/madewith/) for ideas about how to use these models.

?> Models are added to the RunwayML app often, and this page does not necessarily respresent the full list. Contributions, demos, and tutorials are welcome!

## Style Transfer
📽 [Watch How Style Transfer Works](https://www.youtube.com/watch?v=TlHOwsYoIos)

| Model | Description | Networking Examples |
| :--- | :---| :--- |
| [Adaptive Style Transfer](https://open-app.runwayml.com/?model=runway/Adaptive-Style-Transfer)  | Repaint images in the styles of famous painters ([Tutorial](tutorials/tutorial_style_transfer.md))|[Processing](networking/examples?id=processing) |
| [AdaIN-Style-Transfer](https://open-app.runwayml.com/?model=reiinakano/AdaIN-Style-Transfer) | Real-time style transfer | [Processing](networking/examples?id=processing)| 
| [Arbitrary-Style-Transfer](https://open-app.runwayml.com/?model=runway/Arbitrary-Image-Stylization) | Real-time style transfer |[Processing](networking/examples?id=processing)  |
| [CartoonGAN](https://open-app.runwayml.com/?model=sree_harsha/CartoonGAN) | Transform photos of real-world scenes into cartoon style images | |
| [Dynamic-Style-Transfer](https://open-app.runwayml.com/?model=sree_harsha/Dynamic-Style-Transfer) | Tune style dynamically without re-training in real time | |
| [Fast-Style-Transfer](https://open-app.runwayml.com/?model=genekogan/Fast-Style-Transfer) | Stylize images in the styles of famous painters | [openFrameworks](networking/examples?id=openframeworks), [p5.js](networking/examples?id=p5js), [Processing](networking/examples?id=processing) |
| [Liquid-Warping-GAN](https://open-app.runwayml.com/?model=runway/Liquid-Warping-GAN) | Motion and appearance style transfer | |
| [Neural-Style](https://open-app.runwayml.com/?model=anastasis/Neural-Style) | Real-time style transfer | |
| [ShapeMatchingGAN](https://open-app.runwayml.com/?model=sree_harsha/ShapeMatchingGAN) | Controllable Artistic Text Style Transfer | |
| [Style2paints](https://open-app.runwayml.com/?model=zaid/style2paints) | Automatic Sketch Colorization |[Processing](networking/examples?id=processing) |


## Image Translation
| Model | Description | Networking Examples |
| :--- | :---| :--- |
| [CycleGAN](https://open-app.runwayml.com/?model=reiinakano/CycleGAN) | Image-to-image translation without labeled data | [p5.js](networking/examples?id=p5js), [Processing](networking/examples?id=processing)|
| [DeepDream](https://open-app.runwayml.com/?model=anastasis/DeepDream) | Enhance and hallucinate patterns in images | |
| [Pix2Pix](https://open-app.runwayml.com/?model=reiinakano/Pix2Pix) | Image-to-image translation with labeled data | [openFrameworks](networking/examples?id=openframeworks), [Processing](networking/examples?id=processing)|
| [Pix2PixHD-Facemarks2Portrait](https://open-app.runwayml.com/?model=yining/pix2pixHD-Facemarks2Portrait) | Generate a portrait image from a face landmarks image ([Interactive Example](https://experiments.runwayml.com/synthetic_postcard/)) |[Processing](networking/examples?id=processing) |
| [UGATIT](https://open-app.runwayml.com/?model=runway/UGATIT) | Official Tensorflow implementation of U-GAT-IT: Unsupervised Generative Attentional Networks with Adaptive Layer-Instance Normalization for Image-to-Image Translation | [Processing](networking/examples?id=processing) |


## Images → Semantic Image Maps
Semantic Image Segmentation

| Model | Description | Networking Examples |
| :--- | :---| :--- |
| [DeepLab](https://open-app.runwayml.com/?model=genekogan/deeplab) | Extract semantic maps from objects in images | [Processing](networking/examples?id=processing) |
| [DeepLabV3](https://open-app.runwayml.com/?model=runway/DeepLabV3) | Deep labeling for semantic image segmentation | [Processing](networking/examples?id=processing) |
| [Face-Parser](https://open-app.runwayml.com/?model=anastasis/Face-Parser) | A pretrained model for parsing facial components from an image | [Processing](networking/examples?id=processing) |
| [Unsupervised-Segmentation](https://open-app.runwayml.com/?model=anastasis/Unsupervised-Segmentation) | The model assigns labels to pixels that denote the cluster to which the pixel belongs, however no training images nor ground truth labels of pixels are given beforehand.  |  |


## Semantic Image Maps → Images
Semantic Image Synthesis

| Model | Description | Networking Examples |
| :--- | :---| :--- |
| [SPADE-COCO](https://open-app.runwayml.com/?model=runway/spade-coco) | Transform semantic image maps into images | [JavaScript](networking/examples?id=JavaScript), [Processing](networking/examples?id=processing) |
| [SPADE-FACE](https://open-app.runwayml.com/?model=sree_harsha/spade-face) | Transform semantic image maps into images of faces| |
| [SPADE-Landmarks](https://open-app.runwayml.com/?model=genekogan/SPADE-Landscapes) | Transform semantic image maps into landscape images | [Processing](networking/examples?id=processing) |


## Image Editing
| Model | Description | Networking Examples |
| :--- | :---| :--- |
| [BDCN](https://open-app.runwayml.com/?model=sree_harsha/BDCN) | An edge detection model that turns images into contour drawings | |
| [DeepFill](https://open-app.runwayml.com/?model=runway/DeepFill) | Remove objects from photos | [Processing](networking/examples?id=processing)|
| [DeRaindrop](https://open-app.runwayml.com/?model=zaid/DeRaindrop) | Remove raindrops from photos| [Processing](networking/examples?id=processing)|
| [Deep-Portrait-Image-Relighting](https://open-app.runwayml.com/?model=sree_harsha/Deep-Portrait-Image-Relighting) | Generate relighted image by using a single portrait image and a target lighting | |
| [Edge-connect](https://open-app.runwayml.com/?model=zaid/edge-connect) | Generative Image Inpainting with Adversarial Edge Learning | [Processing](networking/examples?id=processing) |
| [EnlightenGAN](https://open-app.runwayml.com/?model=sree_harsha/EnlightenGAN) | Enhance the lighting on your image | |
| [Image-Inpainting-GMCMM](https://open-app.runwayml.com/?model=anastasis/Image-Inpainting-GMCNN) | Image Inpainting via Generative Multi-column Convolutional Neural Networks | [Processing](networking/examples?id=processing)|
| [PhotoSketch](https://open-app.runwayml.com/?model=runway/PhotoSketch) | An edge detection model that turns images into contour drawings | [openFrameworks](networking/examples?id=openframeworks), [p5.js](networking/examples?id=p5js), [Processing](networking/examples?id=processing) |
| [RIDNet](https://open-app.runwayml.com/?model=sree_harsha/RIDNet) | A model for denoising photograghs | |
| [TF-A2RL](https://open-app.runwayml.com/?model=sree_harsha/TF-A2RL) | Aesthetic image cropping | |


## Colorize B/W Media
| Model | Description | Networking Examples |
| :--- | :---| :--- |
| [Automatic-Colorization](https://open-app.runwayml.com/?model=runway/Automatic-Colorization)| Colorize black and white images and videos ([Tutorial](tutorials/tutorial_colorizing_video.md))| |
| [DeOldify](https://open-app.runwayml.com/?model=reiinakano/DeOldify) | Colorize and restore old images | [Processing](networking/examples?id=processing)|


## Upscale Images
| Model | Description | Networking Examples |
| :--- | :---| :--- |
| [ESRGAN](https://open-app.runwayml.com/?model=runway/ESRGAN) | 4x ([Tutorial](tutorials/tutorial_esrgan.md))| [openFrameworks](networking/examples?id=openframeworks), [Processing](networking/examples?id=processing), [TouchDesigner](networking/examples?id=touchdesigner) |
| [Fast-SRGAN](https://open-app.runwayml.com/?model=anastasis/Fast-SRGAN) | Real-time Super Resolution | |  
| [Image-Super-Resolution](https://open-app.runwayml.com/?model=runway/Image-Super-Resolution) | 2x |[Processing](networking/examples?id=processing) |
| [SRFBN](https://open-app.runwayml.com/?model=sree_harsha/SRFBN) | 2x, 3x, and 4x | |  

## 2D Masking
| Model | Description | Networking Examples |
| :--- | :---| :--- |
| [MaskRCNN](https://open-app.runwayml.com/?model=runway/MaskRCNN) | Cut out objects from images |[Processing](networking/examples?id=processing) |
| [Human-Segmentation](https://open-app.runwayml.com/?model=runway/Human-Segmentation) | Segment humans from images and videos | |


## 3D Modeling
| Model | Description | Networking Examples |
| :--- | :---| :--- |
| [3D Dense Face Alignment](https://open-app.runwayml.com/?model=matthewbay/3ddfa) | 3D face alignment | |
| [DenseDepth](https://open-app.runwayml.com/?model=runway/DenseDepth) | Predict depth from 2D images| [Processing](networking/examples?id=processing) |
| [DensePose](https://open-app.runwayml.com/?model=runway/DensePose) | Detect humans in 2D images and turn them into 3D surface models | |




