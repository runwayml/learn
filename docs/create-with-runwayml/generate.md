# Generate Media

You can use models directly of inside the RunwayML app or interact with models through [network protocols](https://learn.runwayml.com/#/how-to/network). The pre-trained models in this category generate synthetic outputs based on specific training data, such as photorealistic images and coherent text. Visit [RunwayML Experiments](https://runwayml.com/madewith/) for ideas about how to use these models.


?> Models are added to the RunwayML app often, and this page does not necessarily respresent the full list. Contributions, demos, and tutorials are welcome!

## Generate Images from Text
| Model | Description | Networking Examples |
| :--- | :---| :--- |
| [AttnGAN](https://open-app.runwayml.com/?model=runway/AttnGAN) | Turn text descriptions of scenes into synthesized images ([Tutorial](tutorials/tutorial_t2i.md), [Interactive Example](https://experiments.runwayml.com/generative_engine/)) | [Arduino](networking/examples?id=arduino), [p5.js](networking/examples?id=p5js), [Processing](networking/examples?id=processing) |


## Generate Text from Images
| Model | Description | Networking Examples |
| :--- | :---| :--- |
| [im2txt](https://open-app.runwayml.com/?model=runway/im2txt) | Generate sentence descriptions of images ([Tutorial](tutorials/tutorial_im2txt.md)) | [JavaScript](networking/examples?id=JavaScript), [Max/MSP](networking/examples?id=maxmsp), [openFrameworks](networking/examples?id=openFrameworks), [p5.js](networking/examples?id=p5js), [Processing](networking/examples?id=processing) |


## Generate Text
| Model | Description | Networking Examples |
| :--- | :---| :--- |
| [GPT-2](https://open-app.runwayml.com/?model=runway/GPT-2) | Generate paragraphs of text from a prompt |[p5.js](networking/examples?id=p5js), [Processing](networking/examples?id=processing) |
| [OpenGPT-2](https://open-app.runwayml.com/?model=runway/OpenGPT-2) | Replication effort of GPT-2's largest model (1.5B parameters) |[Processing](networking/examples?id=processing) |
| [universal-sentence-encoder-xling-runway](https://open-app.runwayml.com/?model=aparrish/universal-sentence-encoder-xling-runway) | Encodes sentences to fixed-length vectors | |
| [vae-lagging-encoder-poetry](https://open-app.runwayml.com/?model=aparrish/vae-lagging-encoder-poetry) | Gutenberg Poetry Variational Autoencoder | [Arduino](networking/examples?id=arduino) |


## Synthesize Images
| Model | Description | Networking Examples |
| :--- | :---| :--- |
| [BigGAN](https://open-app.runwayml.com/?model=runway/BigGAN) | Generate images from 1,000 different categories | [Arduino](networking/examples?id=arduino), [Processing](networking/examples?id=processing) |
| [BigBiGAN](https://open-app.runwayml.com/?model=sree_harsha/BigBiGAN) | Generate Images using the BiGAN Encoder based on BigGAN for Unsupervised Representation Learning for Images | |
| [DeepPrivacy](https://open-app.runwayml.com/?model=anastasis/DeepPrivacy) | DeepPrivacy: A Generative Adversarial Network for Face Anonymization | [Processing](networking/examples?id=processing)|
| [Few-Shot-Face-Translation-GAN](https://open-app.runwayml.com/?model=anastasis/Few-Shot-Face-Translation-GAN) | Face-swapping ([Interactive Example](https://experiments.runwayml.com/portrait_swap/)) | [Processing](networking/examples?id=processing)|
| [GLOW](https://open-app.runwayml.com/?model=genekogan/glow]) | Change facial expressions, hair color, smile, beard, age and more in images of faces | [openFrameworks Addon](networking/examples?id=openframeworks), [Processing](networking/examples?id=processing) |
| [Liquid-Warping-GAN](https://open-app.runwayml.com/?model=runway/Liquid-Warping-GAN) | A Unified Framework for Human Motion Imitation, Appearance Transfer and Novel View Synthesis | |
| [Progressive-Growing-of-GANs](https://open-app.runwayml.com/?model=cris/Progressive-Growing-of-GANs) | Generate faces | [openFrameworks Addon](networking/examples?id=openframeworks), [Processing](networking/examples?id=processing) |
| [StyleGAN](https://open-app.runwayml.com/?model=runway/StyleGAN) | Generate photorealistic images of faces, landscapes, and more ([Interactive Example I](https://experiments.runwayml.com/portrait_swap/), [Interactive Example II](https://experiments.runwayml.com/synthetic_postcard/)) | [openFrameworks Addon](networking/examples?id=openframeworks), [p5.js](networking/examples?id=p5js), [Processing](networking/examples?id=processing) |
