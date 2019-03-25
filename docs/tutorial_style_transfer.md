# Tutorial: Applying Style-Aware Content (Style Transfer) to an image. 

In this tutorial, we will the ["A Style-Aware Content Loss for Real-time HD Style Transfer"](https://arxiv.org/pdf/1807.10201.pdf) model to transfer the particular style of a painter to any image we want. This model is able to capture the more subtle style and nature of an artist by training on multiple paintings rather than a single one.

### Requirements

- Runway Beta
- Docker (If you don't have Docker installed, please follow the installation instructions [here](/installation?id=download-docker).)
- An image file.  

### Step 1

The first step is to select the model **Adaptive Style Transfer** from the Model Directory:

![Adaptive Style Transfer with Runway, step 1](https://runway.nyc3.digitaloceanspaces.com/documentation/0.2.0/styletransfer01.jpg)

### Step 2

Next, add the model to a workspace from the top right side of the app.

![Adaptive Style Transfer with Runway, step 2](https://runway.nyc3.digitaloceanspaces.com/documentation/0.2.0/styletransfer02.jpg)


### Step 3 

If you haven't installed **Adaptive Style Transfer**, the bottom right button will prompt you to install the model.  **You need to have Docker installed in order to continue.**


![Adaptive Style Transfer with Runway, step 3](https://runway.nyc3.digitaloceanspaces.com/documentation/0.2.0/styletransfer03.jpg)

?> Some models might be large so please note that downloading the model might take a couple of minutes. In this case, **Adaptive Style Transfer**  might take **4 to 8 minutes** to download depending on your internet connection.

![Adaptive Style Transfer with Runway, step 4](https://runway.nyc3.digitaloceanspaces.com/documentation/0.2.0/styletransfer04.jpg)


### Step 4

To run **Adaptive Style Transfer** you will need download a `Checkpoint` for every style. `Checkpoints` are specific `Artifacts` that contains the information needed to apply a specific type of style to an image. 

Search for the **Style Checkpoint** dropdown and pick the `Checkpoint` you want to use. In this case we will download and use the Van Gogh `Checkpoint`. 

![Adaptive Style Transfer with Runway, step 5](https://runway.nyc3.digitaloceanspaces.com/documentation/0.2.0/styletransfer05.jpg)

![Adaptive Style Transfer with Runway, step 6](https://runway.nyc3.digitaloceanspaces.com/documentation/0.2.0/styletransfer06.jpg)


### Step 5

From the **Input** dropdown in the I/O View select the **File** option and choose an image. In this case, we will use a photo of a landscape by [Bailey Zindel](https://unsplash.com/photos/NRQV-hBF10M).

?> If you are running the model locally, we recommend to use reduce the size of the image for faster results.

![Adaptive Style Transfer with Runway, step 7](https://runway.nyc3.digitaloceanspaces.com/documentation/0.2.0/styletransfer07.jpg)


### Step 6

On the I/O View select the **Local** option in the **Output** dropdown.

![Adaptive Style Transfer with Runway, step 8](https://runway.nyc3.digitaloceanspaces.com/documentation/0.2.0/styletransfer08.jpg)


### Step 7

Next, click the **Run Adaptive Style Transfer** button on the bottom right corner.

![Adaptive Style Transfer with Runway, step 9](https://runway.nyc3.digitaloceanspaces.com/documentation/0.2.0/styletransfer09.jpg)


### Step 8

After processing the image, Runway will show the result at the local view panel. 

![Adaptive Style Transfer with Runway, step 10](https://runway.nyc3.digitaloceanspaces.com/documentation/0.2.0/styletransfer10.jpg)


#### Result

![Adaptive Style Transfer with Runway, step 11](https://runway.nyc3.digitaloceanspaces.com/documentation/0.2.0/styletransfer11.jpg)

#### Original

![Adaptive Style Transfer with Runway, step 12](https://runway.nyc3.digitaloceanspaces.com/documentation/0.2.0/styletransfer12.jpg)
Photo by [Bailey Zindel](https://unsplash.com/photos/NRQV-hBF10M).