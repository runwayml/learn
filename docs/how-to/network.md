# Interacting with Models over the Network

?> This document assumes the reader is comfortable with basic scripting and computer networking concepts.

In addition to interacting with models via the Runway App's UI, all Runway Models can also be controlled and manipulated with over the network. This is useful for getting data in and out of Runway, integrating Runway Models with other tools and workflows, or providing programmatic control of models through scripting. Each Runway Model exposes itself using three network ports on `localhost`: An **HTTP** port, a **Socket.IO** port, and a **OSC** port. All three servers are available for the duration of the time that the model is running. We've included support for these transport protocols to allow flexibility and convenience around how users interact with models; You are free to use any of these protocols as they all expose the same data and control capabilities.

### The Network UI Panel

![Network Panel](assets/images/how-to/network/network-panel-full.jpg)

You can access the network panel on the right side of the UI while a model is running. There you will see a tab for each protocol where you can find the address, endpoints, and input/output schema of each model server. The ports are configured each time you launch a model and may change between model runs or when you restart the app. This is something we are planning to change in the future, but for now you should expect the network ports to change frequently.

### Endpoints

Each model server exposes several endpoints that you can use to interact with the model. The method of triggering these endpoints varies depending on the protocol that you are using, however, the basic functionality provided by each endpoint remains the same. We'll describe the basics of these endpoints next and then describe how you can use them for each network protocol below.

There are four basic endpoints shared between all protocols:

* `query` (write): Send data to a running model
* `data` (read): Receive the output from a `query` if it succeeded
* `error` (read): Receive an error message from a `query` if it failed
* `info` (read): Get metadata about what type of data the running model is expecting as input and output

You'll notice that `query` is the only endpoint where data is sent to the model server (indicated above as "write"). All other endpoints are marked "read", meaning they output data back to the connected client instead of accepting input.

### Inputs (`query`)

In this guide, we'll use the `im2txt` model as an example. This model accepts an object with an `image` property containing a base-64 encoded image as input.

```json
{
   "image": "data:image/jpeg;base64,..."
}
```

?> Each model will expect a different type of input and produce a different type of output. You can see each model's data type specification in the Network Panel. Be sure you are sending and receiving the right type of data for each model you are interfacing with.

### Outputs (`data`)

When the `im2txt` model receives an input image via `query`, it processes it and outputs an array of image caption objects via the `data` endpoint. Each object in the output array contains a string value representing the caption itself as well as a float value representing the probability that caption is correct (out of `1.0`).

```json
{
   "results": [
      {
         "caption": "a young man riding a skateboard down the side of a ramp .",
         "probability": 0.0006727073
      },
      {
         "caption": "a man on a skateboard doing a trick .",
         "probability": 0.0006250201
      },
      {
         "caption": "a young man riding a skateboard down a ramp .",
         "probability": 0.0004850892
      }
   ]
}
```

### Errors (`error`)

The `error` endpoint can be monitored to receive errors from you model if and when they may occur.

```json
{
   "error": "Something went wrong"
}
```

### Data Types (`info`)

Each Runway Model accepts different types of inputs and outputs for each command it supports. If you're not sure what type of data your model is expecting, or would like your script to programmatically interpret a model's data types at runtime, you can use the `info` endpoint. This endpoint will return a JSON object illustrating the input and output data types the model expects.

```json
{
    "inputs": [
        {
            "description": "Input image",
            "name": "image",
            "type": "image"
        }
    ],
    "outputs": [
        {
            "name": "results",
            "type": [
                {
                    "description": "Output caption",
                    "name": "caption",
                    "type": "text"
                },
                {
                    "description": "Confidence in the result",
                    "name": "probability",
                    "type": "number"
                }
            ]
        }
    ]
}
```

### Protocols

You can begin communicating with a running model using all three network protocols as soon as the model is running; there is no need to enable this functionality. All three protocols give you access to the same endpoints for each model, with some slight but notable differences. The HTTP protocol is request/response based, while both Socket.IO and OSC are event based. We'll outline these differences below.

#### HTTP

HTTP is perhaps the simplest way to interact a model via the network. It stands out from the other two protocols in that you can use the `query` endpoint to both send data to a model _and_ receive its output in the same request. An HTTP `POST` request to `/query` provides input to the model and the response to that `POST` request provides either the model's output or an error. In this way, `/query` is the only endpoint you really need to use to interact with a model via HTTP. The `/data` and `/error` endpoints are useful for if you'd like some process to be aware of the _last_ output or error given by a model without actually providing it input data, but they are not required for normal model interaction like they are with `Socket.IO` or `OSC`.

* `POST /query`: This endpoint is used to send input data to a model and receive its output.
* `GET /data`: This endpoint can be used for polling the latest output of the model without sending new input. It will return the same value that the model server last responded to a `POST` to `/query` with. Polling this endpoint is not required to receive output from a `/query`, as the HTTP response to that query will provide the model's output itself.
* `GET /error`: This endpoint can be used for polling the latest error from the model. Behaves similarly to `/data` but for model errors instead of outputs.
* `GET /info`: Get metadata about what type of data the running model is expecting as input and output.

?> HTTP `POST` requests to the model server should send data in the body of the request as `Content-Type: application/json` and all `GET` requests should expect data to be returned in the same format.

#### Socket.IO

[Socket.IO](https://socket.io/) is an event-based protocol that wraps WebSockets: a bidirectional data streaming protocol that allows servers to push data directly to clients without them having to request it. It's implemented in JavaScript with libraries available for both the Browser and Node.js (see the Socket.IO example code snippet below). The main difference between interacting with a model via Socket.IO vs HTTP is that `data` and `error` events are emitted after a `query` instead of returning the results of the query immediately via an HTTP response. This is useful if you'd like to monitor a model's output stream without necessarily sending it an input query: perhaps you are doing that manually via the Runway app or another script or Runway integration.

* `EMIT query`: This endpoint is used to send input data to a model. Because Socket.IO is an event-based protocol, you must listen to the `data` and `error` events to receive the results of a model query you've emitted the `query` event.
* `LISTEN data`: Receive the output generated by a `query` event if it was successful.
* `LISTEN error`: Receive the error generated by a `query` event if it was unsuccessful.
* `LISTEN info`: Get metadata about what type of data the running model is expecting as input and output. The Socket.IO `info` event is fired **only once right after the socket connection is established**.

```javascript
const io = require('socket.io-client')
const socket = io(`http://localhost:3000`)
// Here's an example of listening to a stream of output data coming from a model
socket.on('data', (output) => {
  // print the output of a model. You can trigger the model manually via the UI
  // or via a call to the 'query' endpoint using any protocol.
  console.log(output)
})
```

#### Open Sound Control (OSC)

[OSC](http://opensoundcontrol.org/spec-1_0) is an event-based protocol similar to Socket.IO. It's not as common as the other two protocols but it has achieved popularity with real-time creative software for processing sound, image, or other arbitrary data over a network. We have [a collection of examples](https://github.com/runwayml/processing) for integrating Runway with [Processing](https://processing.org/) that use the [oscP5 library](http://www.sojamo.de/libraries/oscP5/). OSC acts as a way to exchange data from one app or hardware instrument to another, similar to MIDI.

![OSC Example Screenshot](assets/images/how-to/network/osc-example.jpg)

Above is a screenshot illustrating Runway sending its output to a Processing sketch via OSC.

Every model will create, by default, an OSC server that you can connect to.

To connect to a model via OSC, you first need to create an OSC client and then send a message with the address `/server/connect` to Runway's OSC server at the port displayed within the app in order to start receiving data from Runway. Take a look at a working example with [PoseNet and Processing](https://github.com/runwayml/processing/blob/master/posenet/posenet.pde). Be sure to update the variable `runwayPort` to the port displayed in the app in your OSC code!

OSC events are addressed to the following endpoints:

* `SEND /query`: Send input data to a model.
* `RECEIVE /data`: Receive the error generated by a `query` event if it was unsuccessful.
* `RECEIVE /error`: Receive the error generated by a `query` event if it was unsuccessful.

At the time of this writing there is no support for the `info` endpoint using the OSC protocol.

?> All OSC endpoints expect or return a single JSON object as an OSC string datatype. This string should be parsed as JSON once its received before being further processed and JSON objects sent via OSC should first be converted to a string.

?> OSC uses UDP datagrams as a transport layer so its very efficient, but has a chance to deliver packets out of order or not at all.

### Code Examples

Below are a few code snippets to get you started querying a model using HTTP and Socket.IO. These examples assume a model is running on port `8000` for HTTP and `3000` for Socket.IO, so be sure to update the port numbers accordingly.

### BASH

```bash
# Query the model and receive its input immediately
curl -X POST -d '{ "image": "<base 64 image>" }' -H "Content-Type: application/json" http://localhost:8000/query
```

```bash
# Get the most recent output from the model, once per second
# (you may have to install `watch` via brew if you are on MacOS)
watch -n 1 curl http://localhost:8000/data
```

### JavaScript

#### HTTP

```javascript
const inputs = {
  "image": "<base 64 image>"
};

const modelPort = 8000
fetch(`http://localhost:${modelPort}/query`, {
  method: 'POST',
  headers: {
      Accept: 'application/json',
      'Content-Type': 'application/json',
  },
  body: JSON.stringify(inputs)
}).then(response => response.json())
  .then(output => {
    const { results } = output;
    // use the outputs in your project
  })
```

#### Socket.IO

```javascript
// Be sure socket.io is installed before including it:
//    `npm install --save socket.io`
const io = require('socket.io-client')
const fs = require('fs')

const modelPort = 3000
const socket = io(`http://localhost:${modelPort}`)

socket.on('data', (output) => {
  console.log('Received an data event containing the output of the query:')
  console.log(output)
})

socket.on('error', (error) => {
  console.error('Received an error event, something went wrong during the query:')
  console.error(error)
})

socket.on('info', (info) => {
  console.log('Received an info event once when the socket first connected')
  console.log('This is the type of data the model expects:')
  console.log(info)
})

socket.emit('query', {
  image: `data:image/jpeg;base64,${fs.readFileSync('some-image.jpg').toString('base64')}`
})
```

### Python

```python
import json
from http.client import HTTPConnection

data = { "image": "data:image/jpeg;base64,..." }

modelPort = 8000
conn = HTTPConnection("localhost:" + modelPort)
conn.request("POST", "/query", json.dumps(data),  { 'Content-type': 'application/json' })
response = conn.getresponse()

# use output in your project
output = json.loads(response.read())

print(response.status, response.reason)
# 200 OK

print(output)
# {
#    "results": [
#       {
#          "caption": "a young man riding a skateboard down the side of a ramp .",
#          "probability": 0.0006727073
#       }
#    ]
# }
```
