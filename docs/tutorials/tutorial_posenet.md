# Tutorial: Skeleton tracking in Processing

Runway provides a simple visual interface for experimenting with a variety of machine learning models, but what happens when you want to use those models outside of Runway, in your own applications? This tutorial demonstrates how to perform skeleton tracking in a Processing sketch by communicating in real-time with a pose estimation model running inside Runway.

### Requirements

- Runway App
- [Processing](https://processing.org/download/)

### Step 1

In this tutorial, we will use PoseNet, which is based on the paper [Towards Accurate Multi-person Pose Estimation in the Wild](https://arxiv.org/abs/1701.01779) and a [Tensorflow.js](https://js.tensorflow.org/) implementation by [Dan Oved](https://www.danioved.com/). The first step is selecting the PoseNet model from the Model Directory.

![Skeleton tracking in Processing with Runway, step 1](assets/images/tutorials/tutorial_posenet/posenet01.jpg)

### Step 2

From the PoseNet model view, click on the right top dropdown menu and select **"Add to Workspace"** and then **"New Workspace"**. Create a new workspace by giving it any name you want.

![Skeleton tracking in Processing with Runway, step 1](assets/images/tutorials/tutorial_posenet/posenet02.jpg)

### Step 3

On the I/O, select the **Input** dropdown and click **Camera**. This will allow Runway to access your webcam stream.

![Skeleton tracking in Processing with Runway, step 3](assets/images/tutorials/tutorial_posenet//3_select_camera_input.png)


### Step 4

On the **Output** panel, click the dropdown menu and select **OSC**. OSC stands for Open Sound Control, and it is a protocol for networking computers. This will allow Runway to send data and for Processing to listen for incoming data.

![Skeleton tracking in Processing with Runway, step 4](assets/images/tutorials/tutorial_posenet//4_select_osc_output.png)

### Step 5

With the **Camera** and the **OSC** options selected, click **Run PoseNet** on the lower right side of the application.

![Skeleton tracking in Processing with Runway, step 5](assets/images/tutorials/tutorial_posenet//5_run_posenet.png)

### Step 6

Once the model is running, you will be able to see the output data in the **Format Type** panel. Every new frame being processed will show a progress bar under the camera input. This means the model is running and the data is being stream to an OSC server.

![Skeleton tracking in Processing with Runway, step 6](assets/images/tutorials/tutorial_posenet//6_posenet_running.png)

### Step 7

Install the [OSC-P5](http://www.sojamo.de/libraries/oscP5/) module (as it is not a standard Processing Library). In Processing go to: Sketch > Import Library > Add Library and type `OSCp5` then click `install`.

Nest, visit the [Runway+Processing](https://github.com/runwayml/processing) repository on GitHub and clone or download it. This repo contains a series of practical examples showing how to connect Runway with Processing.

Select the [PoseNet](https://github.com/runwayml/processing/blob/master/posenet/posenet.pde) example and run it with the Processing IDE.

![Skeleton tracking in Processing with Runway, step 7](assets/images/tutorials/tutorial_posenet//7_open_processing_sketch.png)

In that small Processing sketch, the following set of lines set up the connection with the OSC server:

```java
void setup () {
  // ...

  // Set up OSC client
  OscProperties properties = new OscProperties();
  properties.setRemoteAddress("127.0.0.1", 57200);
  properties.setListeningPort(57200);
  properties.setDatagramSize(99999999);
  properties.setSRSP(OscProperties.ON);
  oscP5 = new OscP5(this, properties);

  // Use the localhost and the port 57100 that we define in Runway
  myBroadcastLocation = new NetAddress(runwayHost, runwayPort);

  connect();

  // ...
}

void connect() {
  // Send message to subscribe to model updates
  OscMessage m = new OscMessage("/server/connect");
  oscP5.send(m, myBroadcastLocation);
}
```

And the following code receives and parses updates from the model:

```java
// OSC Event: listens to data coming from Runway
void oscEvent(OscMessage theOscMessage) {
  // The data is in a JSON string, so first we get the string value
  String dataString = theOscMessage.get(0).stringValue();

  // We then parse it as a JSONObject
  data = parseJSONObject(dataString);
}
```

### Step 8

Processing will now receive PoseNet data coming from Runway. Now go create something great in Processing using machine learning!

![Skeleton tracking in Processing with Runway, step  8](assets/images/tutorials/tutorial_posenet//8_voila.png)

### Summary

This tutorial shows how to use a pose estimation model, called PoseNet, to perform skeleton tracking on the webcam stream and send the results to a Processing sketch.
