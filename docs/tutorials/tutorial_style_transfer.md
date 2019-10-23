# Tutorial: Image Style Transfer (Adaptive Style Transfer)

In this tutorial, we will use the ["A Style-Aware Content Loss for Real-time HD Style Transfer"](https://arxiv.org/pdf/1807.10201.pdf) model to transfer the particular style of a painter to an image of our choosing. This model captures the subtle style and nature of an artist by training on multiple paintings rather than on a single one.

### Requirements

- [RunwayML](https://runwayml.com/)
- An image file  

### Step 1

The first step is to select the model **Adaptive Style Transfer** from the Model Directory:

![Adaptive Style Transfer with RunwayML, step 1](assets/images/tutorials/tutorial_style_transfer/select_model_01.png)

### Step 2

Next, add the model to a workspace from the top right side of the app.

![Adaptive Style Transfer with RunwayML, step 2](assets/images/tutorials/tutorial_style_transfer/styletransfer02.png)


### Step 3

If you haven't installed **Adaptive Style Transfer**, the bottom right button will prompt you to install the model.  **You need to have Docker installed in order to continue.**


![Adaptive Style Transfer with RunwayML, step 3](assets/images/tutorials/tutorial_style_transfer/styletransfer03.jpg)

?> Some models might be large so please note that downloading the model might take a couple of minutes. In this case, **Adaptive Style Transfer**  might take **4 to 8 minutes** to download depending on your internet connection.

![Adaptive Style Transfer with RunwayML, step 4](assets/images/tutorials/tutorial_style_transfer/styletransfer04.jpg)


### Step 4

To run **Adaptive Style Transfer** you will need download a `Checkpoint` for every style. `Checkpoints` are specific `Artifacts` that contain the information needed to apply a specific type of style to an image.

Search for the **Style Checkpoint** dropdown and pick the `Checkpoint` you want to use. In this case we will download and use the Van Gogh `Checkpoint`.

![Adaptive Style Transfer with RunwayML, step 5](assets/images/tutorials/tutorial_style_transfer/styletransfer05.jpg)

![Adaptive Style Transfer with RunwayML, step 6](assets/images/tutorials/tutorial_style_transfer/styletransfer06.jpg)


### Step 5

From the **Input** dropdown in the I/O View select the **File** option and choose an image. In this case, we will use a photo of a landscape by [Bailey Zindel](https://unsplash.com/photos/NRQV-hBF10M).

?> If you are running the model locally, we recommend to use reduce the size of the image for faster results.

![Adaptive Style Transfer with RunwayML, step 7](assets/images/tutorials/tutorial_style_transfer/styletransfer07.jpg)


### Step 6

On the I/O View select the **Local** option in the **Output** dropdown.

![Adaptive Style Transfer with RunwayML, step 8](assets/images/tutorials/tutorial_style_transfer/styletransfer08.jpg)


### Step 7

Next, click the **Run Adaptive Style Transfer** button on the bottom right corner.

![Adaptive Style Transfer with RunwayML, step 9](assets/images/tutorials/tutorial_style_transfer/styletransfer09.jpg)


### Step 8

After processing the image, RunwayML will show the result at the local view panel.

![Adaptive Style Transfer with RunwayML, step 10](assets/images/tutorials/tutorial_style_transfer/styletransfer10.jpg)


#### Result

![Adaptive Style Transfer with RunwayML, step 11](assets/images/tutorials/tutorial_style_transfer/styletransfer11.jpg)

#### Original

![Adaptive Style Transfer with RunwayML, step 12](assets/images/tutorials/tutorial_style_transfer/styletransfer12.jpg)
Photo by [Bailey Zindel](https://unsplash.com/photos/NRQV-hBF10M).
