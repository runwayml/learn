# Tutorial: Skeleton tracking in P5.js

In this tutorial we will use the Posenet model in RunwayML, and connect it to a sketch in [p5.js](https://p5js.org/). Posenet allows for accurate skeleton tracking. p5.js is a creative coding library in Javascript. In this tutorial, we'll use websockets to connect p5.js to RunwayML. Websockets are a great way to work with any input/output communication between RunwayML and the browser. This script continuously sends over an image from a browser base web camera input. That input is queried on the model and the output is sent back to the browser. We'll then be able to work with th skeleton points in p5.js for creative output!

### Requirements

- Runway
- [P5.js](https://p5js.org/download/)

### Step 1

![Skeleton tracking in P5.js with Runway, step 1](assets/images/tutorials/tutorial_p5_posenet/selection.png)

Search for Posenet in RunwayML. Posenet should be under the 'Motion Capture' section of the interface. Select it.

### Step 2

![Skeleton tracking in P5.js with Runway, step 2](assets/images/tutorials/tutorial_p5_posenet/info.png)

You should see a page with further information about the model. In the upper right hand corner, select the button **Add To Workspace** and then **New Workspace**. Create a new workspace by giving it any name you want.

### Step 3

![Skeleton tracking in P5.js with Runway, step 3](assets/images/tutorials/tutorial_p5_posenet/interface.png)

You should then see an interface like the one pictured above. We'll be using the socket.io library to communicate with RunwayML. Posenet can be run locally and does not require a GPU. In the bottom right hand corner of the interface, click **Run Locally** to start the model.

### Step 4

![Skeleton tracking in P5.js with Runway, step 4](assets/images/tutorials/tutorial_p5_posenet/port.png)

In the upper rigth hand corner, select **Network** and click on **Socket.io**. The most important step for this sketch is ensuring that the sketch is connecting to RunwayML and able to communicate with it. This communication happens via websockets. Be sure that the Socket.io server port in RunwayML matches the server port in the sketch. Here, we have set up RunwayML to communicate via port 3000 (image above), and have also specified port 3000 in our sketch. 

### Step 5

![Skeleton tracking in P5.js with Runway, step 5](assets/images/tutorials/tutorial_p5_posenet/code.png)

Next we'll want to run the code. The code can be found [at this link](https://github.com/runwayml/p5js/tree/master/PoseNet). To run the code from terminal,  `cd` into the folder and run `$ python -m SimpleHTTPServer`  for python2  or  `python3 -m http.server` if you are using python 3. Navigate to `localhost:8000` in your browser.

### Step 6

Lets take a look at the code to get a sense of whats going on. The code will be in `posenet.js` file inside of the root folder.

# The Code in Detail (HTML):
In your html, be sure to include the [p5.js library](https://p5js.org/download/), and the [Socket.io library](https://socket.io/). In this example, I have also included [Bootstrap](https://getbootstrap.com/) (optional) to make the layout a nicer. In the body of the `index.html` page, we've added two buttons, a 'Stop' and 'Start' button that will give us further control in our sketch. We've also included a paragraph tag with an ID of 'status' to keep track of our connection to RunwayML and give visual feedback. Further, we've included a div tag with an ID for our sketch. This will attach our future sketch to this div, so that its positioned well on the page. Lastly, we've included a script tag for our sketch.

# The Code in Detail (JS):
The javascript code is commented line by line for your reference, there are a few important parts to pay attention to. 

The most important step for this sketch is ensuring that the sketch is connecting to RunwayML and able to communicate with it. This communication happens via websockets. Be sure that the Socket.io server port in RunwayML matches the server port in the sketch. Here, we have set up RunwayML to communicated via port 3000, and have also specified port 3000 in our sketch.

```js
void setup () {
var socket = io.connect('http://127.0.0.1:3000/');
```

Here we set up a function 'sendImage' to send the image from the users webcam to RunwayML via websockets. We should particularly note the `socket.emit` function and the variables it uses. Socket.emit takes two arguments, an input event into RunwayML and the data we would like to send. Here we are sending the a JSON object where the key ('input') is an image from the webcam. If we look at the RunwayML input specifications (image above) under the 'Network' tab and 'socket.io', we can see that Runway is expecting the key to be call 'input' and is expecting a 'base 64 image' for it's value.

```js
   ...
  // Get the current frame and send it to Runway using the Canvas API
  function sendImage() {
    ctx.drawImage(video, 0, 0, 300, 280);
    // Send to Runway the current element in the canvas
    socket.emit('query', {
       image: canvas.toDataURL('image/jpeg'),
    });
  }
```

Below, we'll also set up a `newDrawing` funciton. This funciton will read in the results from RunwayML. These results will be in json format, and we'll expect a json object with two key value pairs, one for the number of poses, and another with the array of keypoints for each pose. Below, we'll parse the json, and get the keypoints. Then we'll loop over all of the keypoints for the pose, and draw an ellipse for each x and y value for each keypoint.

```js
function newDrawing(data){
  background(0)
    //create title
  textSize(20);
  fill(255);
  textAlign(CENTER);
  text("PoseNet Demo: Sending Images via p5.js to Runway.", width/2, 40);
  //if there is data
  if (data != null) {
    //get the poses
    humans = data["poses"];
    //for every pose
    for(let h = 0; h < humans.length; h++) {
        human = humans[h];
        //get the keypoints
        keypoints = human.keypoints;
      // for the list of keypoints, draw the body parts
      for (let k = 0; k < keypoints.length; k++) {
          body_part = keypoints[k];
          positions = body_part["position"];
        // Body parts are relative to width and weight of the input
         posx = positions.x;
         posy = positions.y;
         //console log to the browser for inspection
         console.log(posy);
         //fill each ellipse the color red
         fill(255, 0, 0);
         //draw an ellipse for each keypoint. Here I've shifted them to the center of the screen
         // with +500 and +300. 
         ellipse(posx+500, posy+300, 10, 10);
      }
    }
  }
}
```

### Step 7

![Skeleton tracking in Processing with Runway, step  8](assets/images/tutorials/tutorial_p5_posenet/header.png)

If all works well, your sketch should look something like the image above! 

### Summary

In this tutorial we reviewed how to set up PoseNet with p5.js, and communicate to RunwayML via websockets. There are plenty of ways to extend this sketch and make it your own. We're excited to see what you come up with!
