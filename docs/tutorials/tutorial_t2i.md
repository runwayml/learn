# Tutorial: Text to Image (AttnGAN)

Runway allows you to use and experiment with machine learning models without typing a single line of code. In this tutorial we will be using a model called [AttnGAN: Fine-Grained Text to Image Generation with Attentional Generative Adversarial Networks](https://github.com/taoxugit/AttnGAN/) by Tao Xu et al. to generate images based on text.

?> This tutorial was updated as of Runway v0.6.2. It may fall slightly out of date as new versions of Runway are published.

### Requirements
- [Runway](https://runwayml.com/)

### Select the AttnGAN Model from the Model Directory

Open the Runway app and select the **runway/AttnGAN** model from the Model Directory page. You can search "AttnGAN" if you don't see the model right away.

![GAN, AttnGAN with Runway, step 1](assets/images/tutorials/tutorial_t2i/01_model.jpg)

### Add the AttnGAN to a New Workspace

Add the model to a new workspace by selecting **Add to Workspace** and then **New Workspace** from the top right side of the app. This will create a new workspace that you can add multiple models to. In Runway, a workspace is a collection of models that you are using. A workspace can be thought of as a place to sketch out ideas or build out entire projects.

![GAN, AttnGAN with Runway, step 2](assets/images/tutorials/tutorial_t2i/02_select.jpg)

### Run the Model

Click the **Run Remotely** button on the bottom right of the workspace view to start the model. The model should launch within a few seconds, but may take up to two or three minutes depending on server load. While the model is starting you should see the button throb and display the text: **Starting (click to stop)**. Once the text on the button changes to **Stop**, the model is running.

![GAN, AttnGAN with Runway, step 3](assets/images/tutorials/tutorial_t2i/attn01.jpg)

?> Most models can be run remotely using a cloud GPU or locally by downloading and running them on your own computer (this happens behind the scenes using Docker). In this tutorial, we'll run the model remotely. This [uses credits](https://support.runwayml.com/credits-and-plans/how-much-does-runway-cost) but the model runs much faster, and we don't have to wait for several minutes for it to download.

### Select an Input and an Output

Now that the model is running, you need to select an input and an output format. The workspace view displays inputs at the top and outputs at the bottom. Different models will have different input formats but all will have the ability to **Preview** or **Export** the output to disk.

AttnGAN transforms text to image, so select the **Text** button at the top as the input and the **Preview** button near the middle to choose the output.

### Generate Some Images

Type some text into the input box. As soon as you finish typing or making a change to the text, AttnGAN should process the input and generate a synthetic image. Think of the input text as a label for an image that doesn't exist yet.

![GAN, AttnGAN with Runway, step 5](assets/images/tutorials/tutorial_t2i/attn02.jpg)

### Summary

This tutorial shows how to use [AttnGAN](https://github.com/taoxugit/AttnGAN/), a Generative Adversarial Neural Network (GAN) that was trained to generate images from text.
