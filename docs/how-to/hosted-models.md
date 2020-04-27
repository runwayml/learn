# Hosted Models

Hosted Models allow you to create and deploy models as permanent URLs on the web. They provide you with a unique API endpoint that you can use to interact with them anytime, anywhere, without requiring RunwayML to be open!

All RunwayML models can now be controlled and used over the internet as **Hosted Models**. This is useful for getting data in and out of RunwayML programmatically, integrating models with other tools and workflows, and providing control of models through scripting. Each Hosted Model is exposed via an API URL and is available to service requests at anytime.

- [Hosted Models](#hosted-models)
  - [What's new with Hosted Models](#whats-new-with-hosted-models)
  - [Creating a Hosted Model](#creating-a-hosted-model)
  - [Example Code](#example-code)
  - [HTTP API](#http-api)
    - [GET `/v1`](#get-v1)
    - [GET `/v1/info`](#get-v1info)
    - [POST `/v1/query`](#post-v1query)
  - [Asleep, Awakening, and Awake states](#asleep-awakening-and-awake-states)
  - [Pricing](#pricing)
  - [Security and Access Control](#security-and-access-control)

## What's new with Hosted Models

Hosted Models are...

* Always available on the web! No need to start or stop the model, it will always be there waiting for you when you make a request.
* Simple! Each model exposes the same HTTP routes (see [Hosted Models API](#hosted-models-api)).
* Private by default, with the option to make them public as well (see [Security and Access Control](#security-and-access-control).
* Ready when you need them! Hosted Models introduce the concept of "asleep", "awakening", and "awake" model states. When no requests are made to a Hosted Model for an extended period of time, the model will enter a dormant state until the next request is made (see [Asleep, Awakening, and Awake states](#asleep-awakening-and-awake-states)).
* Hosted Models are charged by request and always run remotely.

## Creating a Hosted Model

Hosted Models can be created from several places in RunwayML. The first is from the "Model Info" view of any model.

<img src="assets/images/how-to/hosted-models/create-from-model-info.png" alt="Create Hosted Model from Model Info page">

Hosted Models can also be created from the Network > HTTP tab of a model that is in a Workspace.

<img src="assets/images/how-to/hosted-models/create-from-workspace.png" alt="Create Hosted Model from Workspace">

A screen like the one below will appear once you've chosen to host a model. Here you can configure the parameters of your Hosted Model, and give it a unique subdomain. Hosted Model subdomains must be unique across all Runway users, so try a few variations if you find the subdomain you enter is already taken.

<img src="assets/images/how-to/hosted-models/create-modal.png" alt="Create Hosted Model Modal">

Hosted Models will appear in the "Hosted Models" tab once they are created. Here you can manage all of your Hosted Models and view usage statistics. Hosted Models are activated by default and they can begin receiving requests immediately after creation. Click the `</>` icon on the right side of the table to view an example code snippet and get starting using your Hosted Model in your project right away.

<img src="assets/images/how-to/hosted-models/hosted-models-tab.png" alt="Hosted Model tab">

## Example Code

The example code snippet below demonstrates how JavaScript can be used to query a GPT-2 text generation Hosted Model at `https://example-text-generator.hosted-models.stage.runwayml.cloud/v1/`.

```javascript
const inputs = {
  "prompt": "Finish my sentence",
  "max_characters": 512,
};

// Replace this Hosted Model URL with your own
fetch("https://example-text-generator.hosted-models.stage.runwayml.cloud/v1/", {
  method: "POST",
  headers: {
    "Accept": "application/json",
    "Content-Type": "application/json",
    "Authorization": "Bearer <token>", // Replace <token> with your Hosted Models's authorization token
  },
  body: JSON.stringify(inputs)
})
.then(response => response.json())
.then(outputs => {
  const { generated_text, encountered_end } = outputs;
  // use the outputs in your project
  console.log(`The model responded to the prompt like so: ${generated_text}`)
  if (encountered_end) {
    console.log(`The model produced the end of text character, so it thinks its job is done`)
  }
})
```

?> You can interface with Hosted Models using any programming language you'd like, so long as your environment can make HTTP requests.

## HTTP API

All Hosted Models expose three simple HTTP routes to interface with all RunwayML models:

1. GET `/v1/` returns metadata about the Hosted Model
1. GET `/v1/info` returns the input/output spec of `/v1/query`
1. POST `/v1/query` is used to run the model on input and produce output

?> Note: The GET `/v1` route for each model will always return results quickly. The GET `/v1/info` and POST `/v1/query` have a timeout limit of 10 minutes and can take quite a while to respond if the model is waking up (see [Asleep, Awakening, and Awake states](#asleep-awakening-and-awake-states)), or is taking a while to process the input provided to it.

### GET `/v1`

The GET `/v1` route returns basic metadata and status information about the Hosted Model.

```bash
curl -H "Authorization: Bearer <token>" \
  https://example-text-generator.hosted-models.runwayml.cloud/v1
```

```json
{
  "status": "starting",
  "queryRoute": "/v1/query",
  "dataRoute": null,
  "errorRoute": null
}
```

Most importantly, the `status` field will report `"running"` if the model is awake and responding to queries quickly, and `"starting"` if the model is waking up and responses may be delayed. See the [Asleep, Awakening, and Awake states](#asleep-awakening-and-awake-states) section for more info.

?> Note: The `Authorization: Bearer <token>` header is only required if the Hosted Model is private. Public Hosted Models do not require an `Authorization` header.

### GET `/v1/info`

The GET `/v1/info` route provides metadata describing the inputs and outputs expected from a POST to `/query`.

```bash
curl -H "Authorization: Bearer <token>" \
curl https://example-text-generator.hosted-models.runwayml.cloud/v1/info
```

```json
{
  "description": "Generate text conditioned on prompt",
  "inputs": [
    {
      "default": "",
      "description": null,
      "minLength": 0,
      "name": "prompt",
      "type": "text"
    },
    {
      "default": 64,
      "description": "The maximum number of characters to generate.",
      "max": 1024,
      "min": 8,
      "name": "max_characters",
      "step": 1,
      "type": "number"
    },
    {
      "default": 0.9,
      "description": "Keep only the token sequences with a cumulative probability above this number. Lower values lead to higher quality but less surprising results.",
      "max": 1,
      "min": 0.1,
      "name": "top_p",
      "step": 0.1,
      "type": "number"
    },
    {
      "default": 1000,
      "description": "Random seed. Change this number to generate different outputs.",
      "max": 1000,
      "min": 0,
      "name": "seed",
      "step": 1,
      "type": "number"
    }
  ],
  "name": "generate_batch",
  "outputs": [
    {
      "default": "",
      "description": null,
      "minLength": 0,
      "name": "generated_text",
      "type": "text"
    },
    {
      "default": false,
      "description": null,
      "name": "encountered_end",
      "type": "boolean"
    }
  ]
}
```

The object returned by GET `/v1/info` contains four properties:

* A `name` for the model command that was chosen when configuring the Hosted Model
* A `description` brief description for what the command does
* An `inputs` array describing expected input parameters to be presented in the body of the POST `/v1/query` request
* An `outputs` array describing expected outputs from a well formed POST to `/v1/query`

### POST `/v1/query`

The POST `/v1/query` route is how you actually use a model! POSTing input values in the body of the request will trigger model inference and produce output values in the body of the response.

```bash
curl \
  -X POST \
  -H "Authorization: Bearer <token>" \
  -d '{ "prompt": "Finish my sentence" }' \
  https://example-text-generator.hosted-models.runwayml.cloud/v1/query
```

## Asleep, Awakening, and Awake states

Hosted Models may go to sleep after 5 minutes if they are not used. A model can be in one of one of three states:

* **Asleep**: The Hosted Model hasn't received any requests for a while and has gone to sleep. The next request will wake it up.
* **Awakening**: The Hosted Model is transitioning from the dormant asleep state into the awake state.
* **Awake**: The Hosted Model is up and running and requests should be processed quickly.

No matter which state the Hosted Model is currently in, it will always be able to satisfy any request you make to it. The only difference from your perspective is that requests to `/v1/info` and `/v1/query` may take longer to complete if the model is asleep or awakening.

## Pricing

Pricing information for Hosted Models can be found in [this support article](https://support.runwayml.com/en/articles/3967783-hosted-model-pricing).

## Security and Access Control

All Hosted Models are private by default and can optionally be made public.

Private models are protected from unauthorized use by including a secret token in the `Authorization` header of all requests. Requests to private models that don't include a header in the format `Authorization: Bearer <token>`, or include the wrong `<token>` value, will receive a 401 Unauthorized response.

?> Note: Take care to protect the token associated with each Hosted Model. Including code that interacts with a private Hosted Model in the JavaScript source of a static web page is not sufficient to protect the model from unauthorized use!


<!--
## Going Further
-->
