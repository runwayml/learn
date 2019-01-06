# Overview

## Models Directory

![Models Directory](https://runway.nyc3.cdn.digitaloceanspaces.com/documentation/models_directory_annotated.png)

## Input/Output View

![Input/Output View](https://runway.nyc3.cdn.digitaloceanspaces.com/documentation/io_view_annotated.png)

### Inputs

| Input      | Supported Types | Description                                       |
|------------|-----------------|---------------------------------------------------|
| Camera     | image           | Use frames from the webcam stream as input        |
| Microphone | audio           | Audio segments from microphone as input           |
| Text       | text            | Free-from text input                              |
| File       | all types       | Use a supported file type                         |
| HTTP       | all types       | Query and receive results via an HTTP requests    |
| Socket.IO  | all types       | Query and receive results via a Socket.IO message |
| OSC        | all types       | Query and receive results using OSC over UDP      |

### Outputs

| Output     | Description                                       
|------------|---------------------------------------------------------------------|
| Local      | Preview the model output inside Runway                              |
| File       | Stream the model output into a file using supported formats         |
| HTTP       | Query and receive results via an HTTP requests                      |
| Socket.IO  | Query and receive results via a Socket.IO message                   |
| OSC        | Query and receive results using OSC over UDP                        |


## Coming Soon...

* __Cloud GPU__: Run models powered with GPUs from a variety of cloud providers.
* __Training__: Train models on your own datasets.
