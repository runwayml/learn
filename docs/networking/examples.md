# Networking Examples

You can interact with models in RunwayML from creative coding and design applications through three networking protocols: HTTP, WebSockets (using Socket.IO), and Open Sound Control (OSC). Here's an [overview](https://learn.runwayml.com/#/how-to/network) of how it works. 

This page provides tutorials and code examples to help you get started with your own machine learning projects using these networking protocols. Visit [Projects Made with RunwayML](https://runwayml.com/madewith/) for more inspiration. Additional projects, tutorials, and code examples are welcome!

🎉Community Contribution


## Arduino
**HTTP**

| Model | Description | Type | Source
| :--- | :---| :--- | :--- |
| AttnGAN | [Send Text to Create Images from a Feather Huzzah (ESP8266)](https://github.com/runwayml/arduino/tree/master/Feather_Huzzah/send_text_attnGan) | Tutorial | [Bérenger Recoules](http://b2renger.github.io/) 🎉 | 
| BigGAN | [Send Vectors from a Feather Huzzah (ESP8266)](https://github.com/runwayml/arduino/tree/master/Feather_Huzzah/send_vector_BigGan) |Tutorial | [Bérenger Recoules](http://b2renger.github.io/) 🎉 | 
| VAE-Lagging-Encoder-Poetry |[Receive Data to a Feather Huzzah (ESP8266)](https://github.com/runwayml/arduino/tree/master/Feather_Huzzah/receive_text_vae_lagging_encoder_poetry)  | Tutorial | [Bérenger Recoules](http://b2renger.github.io/) 🎉 | 

[RunwayML + Arduino Code Repository](https://github.com/runwayml/arduino)<br>
[Learn Arduino](https://www.arduino.cc/)



## JavaScript
**HTTP**

| Model | Description | Type | Source
| :--- | :---| :--- | :--- |
| SPADE-COCO | [Noise2D Image Synthesizer](https://github.com/runwayml/javascript/tree/master/SPADE-COCO/Noise2DSynth) | Example | [JP Yepez](https://www.jpyepez.com) 🎉 | 


**Socket.IO**

| Model | Description | Type | Source
| :--- | :---| :--- | :--- |
| im2txt | [Generate Text from Webcam Images](https://github.com/runwayml/javascript/tree/master/im2txt/sendWebcam) | Example | RunwayML | 
| im2txt | [Receive Text from im2txt](https://github.com/runwayml/javascript/tree/master/im2txt/receivesOnly) | Example |  RunwayML  | 

[RunwayML + JavaScript Code Repository](https://github.com/runwayml/javascript)


## Max/MSP
**OSC**

| Model | Description | Type | Source
| :--- | :---| :--- | :--- |
| im2txt | [Receive Text](https://github.com/runwayml/maxmsp/tree/master/im2txt/receiveCamera) | Example | [Aarón Montoya-Moraga](montoyamoraga.io) 🎉 | 


[RunwayML + Max/MSP Code Repository](https://github.com/runwayml/maxmsp)<br>
[Learn Max/MSP](https://cycling74.com)


## openFrameworks
**HTTP**

| Model | Description | Type | Source
| :--- | :---| :--- | :--- |
| [Multiple Models](https://github.com/genekogan/ofxRunway) | ofxRunway Addon (v1)  | Addon  | [Gene Kogan](https://genekogan.com) 🎉 | 
| [Multiple Models](https://github.com/runwayml/ofxRunway) | ofxRunway Addon (v2)  | Addon  | [Roy Macdonald](https://github.com/roymacdonald/) 🎉 | 


**OSC**

| Model | Description | Type | Source
| :--- | :---| :--- | :--- |
| im2txt | [Generate Text from Images](https://github.com/runwayml/openFrameworks/tree/master/im2txt) | Example | [George Profenza](http://sensori.al/) 🎉 | 
 

[RunwayML + openFrameworks Code Repository](https://github.com/runwayml/openFrameworks)<br>
[Learn openFrameworks](https://openframeworks.cc)



## OpenRNDR
**Socket.IO**

| Model | Description | Type | Source
| :--- | :---| :--- | :--- |
| Face-Landmarks | [Face Tracking](https://github.com/runwayml/OpenRNDR/blob/master/src/main/kotlin/facedetect.kt) | Example | [Ryan Bateman](http://boat.horse/) 🎉 | 
| PoseNet | [Skeleton Tracking](https://github.com/runwayml/OpenRNDR/blob/master/src/main/kotlin/posenet.kt) | Example |[Ryan Bateman](http://boat.horse/) 🎉  |


[RunwayML + OpenRNDR Code Repository](https://github.com/runwayml/OpenRNDR)<br>
[Learn OpenRNDR](https://openrndr.org)



## p5.js
**HTTP**

| Model | Description | Type | Source
| :--- | :---| :--- | :--- |
| AttnGAN | [Generate Images from Text](tutorials/tutorial_p5_attngan.md) | Tutorial |[Matthew Kenney](http://matthewkenney.site/) 🎉  |
| CycleGAN | [Image Translation](tutorials/tutorial_p5_cyclegan.md) | Tutorial | [Matthew Kenney](http://matthewkenney.site/) 🎉 |
| GPT-2 | [Generate Text](https://github.com/runwayml/p5js/tree/master/GPT2) | Example | [Matthew Kenney](http://matthewkenney.site/) 🎉 |
| im2text | [Generate Text from Images](https://github.com/runwayml/p5js/tree/master/im2txt) | Example | [Yining Shi](https://1023.io) 🎉 |
| PhotoSketch | [Create Contour Drawings I with PhotoSketch](tutorials/tutorial_photosketch.md) | Tutorial  |  [JP Yepez](https://www.jpyepez.com) 🎉 |
| StyleGAN | [Create Animated Image Transitions](https://heartbeat.fritz.ai/animated-stylegan-image-transitions-with-runwayml-57a2e20db80f) |  Tutorial | [Mike Heavers](https://mikeheavers.com/) 🎉  |
| StyleGAN | [Generate AI Rainbows](tutorials/tutorial_stylegan.md) | Tutorial  |  [Daniel Shiffman](https://www.youtube.com/channel/UCvjgXvBlbQiydffZU7m1_aw) 🎉 |


**Socket.IO**

| Model | Description | Type | Source
| :--- | :---| :--- | :--- |
| CycleGAN  | [Image Translation](https://github.com/runwayml/p5js/tree/master/CycleGAN/CycleGAN_Websockets) | Example | [Matthew Kenney](http://matthewkenney.site/) 🎉 |
| Fast Style Transfer | [Video from Webcam](https://github.com/runwayml/p5js/tree/master/FastStyleTransfer) | Example | [Matthew Kenney](http://matthewkenney.site/) 🎉 | 
| PhotoSketch | [Create Contour Drawings II](tutorials/tutorial_p5_photosketch.md) | Tutorial | [Matthew Kenney](http://matthewkenney.site/) 🎉 | 


[RunwayML + p5.js Code Repository](https://github.com/runwayml/p5js/blob/master/README.md)<br>
[Learn p5.js](https://p5js.org/)



## Processing

📽 [Watch How to Install and Use the RunwayML Library for Processing](https://www.youtube.com/watch?v=zGdOKaLOjck&list=PLj598ZXODDO_oWYAiO5c0Ac05IyrPUG8t&index=6&t=0s)

**HTTP**

| Model | Description | Type | Source
| :--- | :---| :--- | :--- |
| [Multiple HTTP Examples](https://github.com/runwayml/processing-library/tree/master/examples/HTTP) | [RunwayML Library for Processing](https://github.com/runwayml/processing-library) | Examples  | [George Profenza](http://sensori.al/) 🎉 |
 

**OSC**

| Model | Description | Type | Source
| :--- | :---| :--- | :--- |
| GPT-2 | [Generate Text](tutorials/tutorial_processing_gpt2.md) | Tutorial | RunwayML | 
| [Multiple OSC Examples](https://github.com/runwayml/processing-library/tree/master/examples/OSC) | [RunwayML Library for Processing](https://github.com/runwayml/processing-library) | Examples | [George Profenza](http://sensori.al/) 🎉 | 
| PoseNet | [Skeleton Tracking](tutorials/tutorial_posenet.md) | Tutorials | RunwayML and [Daniel Shiffman](https://www.youtube.com/channel/UCvjgXvBlbQiydffZU7m1_aw) 🎉 | 


[RunwayML Library for Processing](https://github.com/runwayml/processing-library)<br>
[Learn Processing](https://processing.org/)


## Pure Data
**HTTP**

| Model | Description | Type | Source
| :--- | :---| :--- | :--- |
| PoseNet | [Skeleton Tracking](https://github.com/runwayml/puredata/tree/master/posenet) | Tutorial | [Joel Matthys](http://joel.matthysmusic.com) 🎉 | 

[RunwayML + Pure Data Code Repository](https://github.com/runwayml/puredata)<br>
[Learn Pure Data](https://puredata.info)



## TouchDesigner
**HTTP**

| Model | Description | Type | Source
| :--- | :---| :--- | :--- |
| ESRGAN | [Upscale Images and Enhance Textures](https://github.com/runwayml/touchDesigner/tree/master/ESRGAN/EnhanceTextures) | Example | [JP Yepez](https://www.jpyepez.com) 🎉| 
| MobileNet | [Image Classification](https://github.com/runwayml/touchDesigner/tree/master/MobileNet/TDClassifier) | Example | [JP Yepez](https://www.jpyepez.com) 🎉 | 


**OSC**

| Model | Description | Type | Source
| :--- | :---| :--- | :--- |
| PoseNet | [Face Tracking with PoseNet](https://github.com/BarakChamo/TD_PoseNet) | Example | [Barak Chamo](https://barakchamo.com/) 🎉| 

[RunwayML + TouchDesigner Code Repository](https://github.com/runwayml/touchDesigner)<br>
[Learn TouchDesigner](https://derivative.ca)
