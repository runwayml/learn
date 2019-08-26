
# Tutorial: Generate Text (GPT2 and Processing)

![Header](assets/images/tutorials/tutorial_processing_gpt2/header.png)

This post covers how to create an interface in [Processing](https://processing.org/), and use that interface to interact with a GPT-2 model in Runway. 

### Requirements
- [Runway](https://runwayml.com/)
- [Processing](https://processing.org/download/)

### Code
Find the code for this tutorial [here](https://github.com/runwayml/processing/tree/master/GPT2).

### GPT-2
GPT-2 is a model for generating long paragraphs of text. With GPT-2, one can condition the output of the model on some input text. The output from the model will then continue the text. For instance, if you prime the model with 'My name is Matt and' the model will output something like 'I am a software developer...' etc.

### The Network
GPT-2 is a transformer model. Transformers are a new state-of-the-art network for a wide array of natural language understanding problems, including reading comprehension, question answering, summarization, and translation. Here, we'll be using it for text generation.

### Start the Model
To set up the GPT-2 model in Runway, click on the **Browse Model** button on the upper-left corner of the interface. Search for GPT-2 in the searchbar at the top of the interface, and select it. This will take you to a page with further information about the model. 

![Select Model](assets/images/tutorials/tutorial_processing_gpt2/selection.png)

From there we can click the **Add to Workspace** button in the upper right hand corner and select **New Workspace**. Runway will suggest a name for your workspace. Feel free to change the name or use the one provided and click **Create**. 

![Model Info](assets/images/tutorials/tutorial_processing_gpt2/info.png)

In the workspace, click the **Run Remotely** button, ensuring that the **Remote GPU Enabled** toggle is turned on. Keep in mind that this model will require a GPU to run, and will cost credits. Click **Preview** for the Output Source.


![Add to Workspace](assets/images/tutorials/tutorial_processing_gpt2/interface.png)

### What the Code Does
We'll be  using [Processing](https://processing.org/) to communicate with Runway. Processing is a creative coding environment and language written in Java. We'll create this communication through the use of [Open Sound Control](http://opensoundcontrol.org/introduction-osc) (OSC). 

### How the Code Works
OSC is a messaging protocol much like MIDI. It allows the user to pipe messages to and from Runway. This sketch uses the processing OSC library to create a connection between Runway and Processing. We'll be sending over the start of a sentence, and well let our GPT-2 model generate the rest of the paragraph.

### The Code in Detail (Setup)
To run the code, we'll need to include the Processing OSC library in our sketch. This can be done by going under tools in the navbar, and selecting **Add Tool...**. From there an interface should open. Under the **Libraries** tab, search for the **oscP5** library and click **Install** in the bottom right. 

![Port Address](assets/images/tutorials/tutorial_processing_gpt2/oscp5.png)

We'll also need to install the controlP5 library. To install this library, follow the same steps above and search for **controlP5**. Click **Install** to install the library. 

![Port Address](assets/images/tutorials/tutorial_processing_gpt2/controlp5.png)

### The Code in Detail (Processing)

#### Part 1

![Port Address](assets/images/tutorials/tutorial_processing_gpt2/port.png)

The most important step for this sketch is ensuring that the sketch is connecting to Runway and able to communicate with it. We'll make sure Runway is expecting OSC messages on port 57100 (the default port). In our processing sketch, we'll setup the sketch to communicate with Runway via this port. 

```java
// Runway Host
String runwayHost = "127.0.0.1";
// Runway Port
int runwayPort = 57100;

// Use the localhost and the port 57100 that we define in Runway
myBroadcastLocation = new NetAddress(runwayHost, runwayPort);
```

#### Part 2

Next, we'll define the port for our sketch to listen to. To receive the text back from Runway, we'll define `port 57200` to listen to as a remote address.
```java
  //define OSC properties
  OscProperties properties = new OscProperties();
  //define remote port. We'll be recieving OSC on this port
  properties.setRemoteAddress("127.0.0.1", 57200);
  properties.setListeningPort(57200);
  properties.setDatagramSize(99999999);
  properties.setSRSP(OscProperties.ON);
  oscP5 = new OscP5(this, properties);

  // Use the localhost and the port 57100 that we define in Runway
  myBroadcastLocation = new NetAddress(runwayHost, runwayPort);

```


#### Part 3
![Input Requirements](assets/images/tutorials/tutorial_processing_gpt2/input.png)

Next, we'll setup up a function so that our sketch can send the input of the text box to Runway. Runway is expecting JSON with a prompt (the text we're sending) and a seed number. Here, we set the address that Runway will receive the message on to `query`. We'll then create a new JSON object and add the text from our text field to the JSON object. The GPT-2 model also requires a seed number. The seed will determine how "creative" the text is (how closely it aligns to the training data), with 1 being the most creative and 0.01 the least creative. after `json_message.setString("prompt", theText);` and  `json_message.setInt("seed", 1);` we should have a JSON object that looks like this `{"prompt" : "the text you input", "seed" : "1" }`. We'll convert the JSON object to a string and send it to Runway via `oscP5.send(myMessage, myBroadcastLocation); `

```java
//send the text from ou interface to Runway
void input(String theText) {
  //ensure the message is sent to "query" channel
  OscMessage myMessage = new OscMessage("/query");
  //create JSON object
  json_message = new JSONObject();
  
  //add the text from the textfield and seed
  json_message.setString("prompt", theText);
  json_message.setInt("seed", 1);
  print(json_message);
  json_output = json_message.toString();

  myMessage.add(json_output);
  
  //send the message to Runway
  oscP5.send(myMessage, myBroadcastLocation); 
}

```
  
#### Part 4

![Output Requirements](assets/images/tutorials/tutorial_processing_gpt2/output.png)

We**ll also need a function to read the JSON data back into our sketch (pictured above). We should be expecting the message to be coming from Runway in JSON format from the `data` channel. With `if(theOscMessage.checkAddrPattern("/data")==true)`, we'll create receive the oscMessage and check that the channel is, infact `data`. Next we'll get the string value from the data and parse the JSON object for the `text` key. 

```java  
//receive the message from Runway
void oscEvent(OscMessage theOscMessage) {  
  //ensure the message is coming from the "data" channel
  if(theOscMessage.checkAddrPattern("/data")==true) {
    String dataString = theOscMessage.get(0).stringValue();
     print(dataString);
     
    //parse the JSON 
    data = parseJSONObject(dataString);
    //get the value of the "text" key
    text_output = data.getString("text");
    return;
  } 
  println("### received an osc message. with address pattern "+theOscMessage.addrPattern());
}
```

### Running the Sketch
The last part is displaying the text in the draw function! From here, you should be able to change the draw function to display the text in interesting ways! Click the **Run** arrow in the upper lefthand corner of the processing interface. The interface should appear. Enter some text and hit **Return**. There are plenty of ways to extend this example! We're excited to see what you create!
