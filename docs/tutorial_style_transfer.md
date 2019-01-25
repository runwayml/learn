# Tutorial: Applying Style Transfer to an image. 

In this tutorial, we will apply a style to an image using the [Adaptive Style Transfer](https://arxiv.org/pdf/1807.10201.pdf) model by Sanakoyeu et al. 

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

To run **Adaptive Style Transfer** you will need a Checkpoint ( we call them Artfacts ), which are the ones who contains the information you need to apply a specific type of style in this case. If you haven't intalled any checkpoint yet, you can do this at the Setup Options in the right panel of the app. 

Search for the **Style Checkpoint** dropdown and pick the Artifact you want to use. In this case we will download and use Van Gogh. 

![Adaptive Style Transfer with Runway, step 5](https://runway.nyc3.digitaloceanspaces.com/documentation/0.2.0/styletransfer05.jpg)

![Adaptive Style Transfer with Runway, step 6](https://runway.nyc3.digitaloceanspaces.com/documentation/0.2.0/styletransfer06.jpg)


### Step 5

You should now have the model and at least one artifact installed in your disk. 

From the **Input** dropdown in the I/O View select the **File** option and choose an image. In this case, we will use a photo of a landscape by [Bailey Zindel](https://unsplash.com/photos/NRQV-hBF10M) we found on [Unsplash](https://unsplash.com).

**If you are running the model locally, we recommend to use reduce the size of the image for faster results.**

![Adaptive Style Transfer with Runway, step 7](https://runway.nyc3.digitaloceanspaces.com/documentation/0.2.0/styletransfer07.jpg)


### Step 6

On the I/O View select the **Local** option in the **Output** dropdown. We will get the output on the local preview panel.

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