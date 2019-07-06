
# Using P5 with CycleGAN

![Header](assets/images/tutorials/tutorial_p5_cyclegan/header.png)

This post covers how to create an interface in [p5.js](https://p5js.org/download/), and use that interface to interact with a CycleGAN Model in RunwayML. 

# CycleGAN:
CycleGAN is a type of conditional Generative Adversarial Network. Much like Pix2Pix or Photosketch, the goal of CycleGAN is to produce synthetic images. Like Pix2Pix, CycleGAN takes in two sets of images, an example set and a target set. The output of CycleGAN is to create images that look like the target set from examples from the example set. For instance, let's say we want to create a model that turns pictures of horses into pictures of zebras. CycleGAN will learn the probability distrobution of both sets of images to make this transformation possible. We can then query the model with pictures of horses, and get out the same picture but with th horse in the style of a zebra.

# The Network:
Learning the probability distribution of the generated data distribution from the input data is  done by setting up two distinct neural network. The generator network (G) is trying to generate images that look like they are from the training set, while the discriminator (D) network is attempting to determine whether a given image was produced by the generator, or from the training set. The discriminator will determine whether the output of the generator is real or fake and generating a 1 (real) or 0 (fake) a probability of whether it is real or fake. This game plays out over a series of epochs. At fist, neither the generator or discriminator perform well. As learning progresses and the gradients are passed back to each network, both improve their performance. The probability distributions for the fake image start to take shape in relation to the distribution of the real images over a series of epochs. 

# The Details:
Where CycleGAN differs from Pix2Pix or other conditional GANs is that it doesn't require a 1 to 1 mapping between images. If you look at Pix2Pix examples, you'll see that the model requires a strictly similar representation between the image pairs. With CycleGAN however, we can just feed in a bunch of pictures of zebras and horses in no particular order and the network will "learn" the translation. No image pairs are needed. This is done through the use of a cycle consisten loss function used in the network.

# How to start the model:
To set up the CycleGAN model in RunwayML, click on the 'Browse Model' button on the upper-left corner of the interface. Search for CycleGAN in the searchbar at the top of the interface, and select it. This will take you to a page with further information about the model. 

![Select Model](assets/images/tutorials/tutorial_p5_cyclegan/selection.png)

From there we can click the 'Add to Workspace' button in the upper right hand corner and select 'New Workspace'. Runway will suggest a name for your workspace. Feel free to change the name or use the one provided and click 'Create'. 

![Model Info](assets/images/tutorials/tutorial_p5_cyclegan/info.png)

In the workspace, click the 'Run Remotely' button, ensuring that the 'Remote GPU Enabled' toggle is turned on. Keep in mind that this model will require a GPU to run, and will cost credits. Click 'Preview' for the Output Source. We do not need to choose an Input Source, as we'll be sending images straight from our browser! In this tutorial, well be using HTTP to connect our P5js sketch with RunwayML. 


![Add to Workspace](assets/images/tutorials/tutorial_p5_cyclegan/interface.png)

# What the code does:
Well be using [P5.js](https://p5js.org) to communicate to RunwayML. P5.js is a Javascript based creative coding framework. By bringing the output into the browser and the P5.js ecosystem, it will give us the flexibility to use the output from the model for other creative purposes. In this example we'll use the HTTP to connect with RunwayML. 

# How the code works:
HTTP are one of the many ways we can transfer data from our code into RunwayML. In this tutorial, we'll be posting an image as an input via a `POST` request. That input is queried on the model and the output is sent back to the browser.

# The Code in Detail (HTML):
In your html, be sure to include the [p5.js library](https://p5js.org/download/) and [p5.js dom library](https://p5js.org/reference/#/libraries/p5.dom). In this example, I have also included [Bootstrap](https://getbootstrap.com/) (optional) to make the layout a little nicer. In the body of the `index.html` page we'll add a button to allow our sketch to post the image to RunwayML. Further, we'll include a div tag with an ID for our sketch. This will attach our future sketch to this div, so that its positioned well on the page. Lastly, we'll include a script tag for our sketch.

# The Code in Detail (JS):
The javascript code is commented line by line for your reference, there are 3 important parts to pay attention to.  

## Part 1

![Port Address](assets/images/tutorials/tutorial_p5_cyclegan/port.png)


The most important step for this sketch is ensuring that the sketch is connecting to RunwayML and able to communicate with it. Here, we have set up RunwayML to communicated via port 8000 (image above), and specify port 8000 in our sketch.

```js
let url = 'http://localhost:8000/query';
```

## Part 2

Next, we'll need some way to load an image into our interface. We'll use the [p5.js DOM library] to do this. In setup, we'll create a file input using the `createFileInput` function. This function takes a callback function. Here we'll create a fucntion called `handleInput`. This `handleInput` function will check to see if the file is an image, and if so, will load the image into our `img` variable.
```js
input_image = createFileInput(handleFile);
...

...
function handleFile(file) {
  if (file.type === 'image') {
    img = loadImage(file.data);
  } else {
    img = null;
  }
}
```


## Part 3
![Input Requirements](assets/images/tutorials/tutorial_p5_cyclegan/input.png)

We'll set up a function that makes a post request to RunwayML, with the image that we've selected. First we'll load the pixels of our image with 'loadPixels' and then we'll convert the image to a base64 image with `img.canvas.toDataURL`. RunwayML is expecting data in JSON format, where the key is 'image' and the value is the data of the image we'd like to send. We'll make a variable `postData` with these specifications. Lastly, P5.js has a function 'httpPost' that allows us to make our post request to RunwayML. We'll use the url specified above, and pass in the JSON data to be posted. The returned data will call our `newDrawing` function, overviewed in the next section.
```js
function sendImage() {
    img.loadPixels();
    post_image = img.canvas.toDataURL('image/jpeg'),

    postData = { image: post_image};

  httpPost(url, 'json', postData, function(result) {
    newDrawing(result)
  });
}
```
  
## Part 4

![Output Requirements](assets/images/tutorials/tutorial_p5_photosketch/output.png)

Now that we've posted out data to RunwayML and recieved a response, we'll need to take that data and convert it into an image. We'll create a function called `newDrawing` that takes in this data. Next we'll say "if there is data, and that data has an key called 'image', created an image out of that data with `createImg`". The `createImg` function is part of the p5.js DOM library. Please be sure not to confuse `createImg` with `createImage`, as they do different things. The `createImg` function will create an image out of our data and put that image on the DOM with an <img> html tag. We can specify the height, width and position of our image with the `attribute` and `position` functions below.

```js  
function newDrawing(data){
    if(data && data.image) {
      newimg = createImg(data.image);
      newimg.attribute('width', 400)
      newimg.attribute('height', 400)
      newimg.position(700, 30);
    }
}
```


# Moving Foward:
This tutorial worked with P5.js and HTTP communicate to RunwayML. How could we extend it!? Try using different image/model combinations to see what you can come up with. What happens if you send over your own drawings rather than images? While we use CycleGAN in the tutorial, every other model in RunwayML takes in data via HTTP. Try changing the input/output keys in the code and then running this code with Pix2Pix, Photosketch, Style Transfer, or any other model in Runway!