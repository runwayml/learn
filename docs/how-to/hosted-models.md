# Hosted Models

Hosted Models allow you to create and deploy models as permanent URLs on the web. They provide you with a unique API endpoint that you can use to interact with them via HTTP anytime, anywhere, without requiring the Runway app to be open, or even installed!

All RunwayML models can now be controlled and manipulated over the internet as Hosted Models. This is useful for getting data in and out of RunwayML programmatically, integrating models with other tools and workflows, and providing control of models through scripting. Each Hosted Model is exposed via an HTTP API and is available to service requests at anytime.

* [What's new with Hosted Models](#whats-new-with-hosted-models)
* [Example](#example)
* [Hosted Models API](#hosted-models-api)
* [Asleep, Awakening, and Awake states](#asleep-awakening-and-awake-states)
* [Pricing](#pricing)
* [Security and Access Control](#security-and-access-control)

## What's new with Hosted Models

We've provided programmatic access to models for a while now via the [Localhost Network API](how-to/network). Hosted Models takes this feature a huge leap forward by providing several exciting and notable changes.

* Hosted Models are always available on the web. No need to start or stop the model, it will always be there waiting for you when you make an HTTP request.
* Hosted Models are charged by request and always run remotely. [Localhost Network API](how-to/network) models that run remotely are charged by the minute for as long as they are running.
* Hosted Models are private by default, with the option to make them public as well. `Authorization: Bearer <token>` headers are used to protect private models.
* Hosted Models introduce the concept of "asleep", "awakening", and "awake" model states. When no requests are made to a Hosted Model for an extended period of time, the model will enter a dormant state until the next request is made (see [Asleep, Awakening, and Awake states](#asleep-awakening-and-awake-states)).
* Hosted Models provide a versioned namespace (e.g. `/v1/`), so that the code you write can be guaranteed to continue to work with, even as we make improvements and change APIs in the future.
* Hosted Models use HTTP only. We've dropped support for OSC and Socket.io, however you can still use these protocols via the [Localhost Network API](how-to/network).
* Hosted Models are simple! Each model exposes the same three HTTP routes (see [Hosted Models API](#hosted-models-api)).

We'll continue to support the [Localhost Network API](how-to/network) for the forseeable future, but we recommend moving to using Hosted Models for any new projects and updates.

## Example

```javascript
// TODO: Come back here and make this a GPT-2 infinite loop sampler example
const inputs = {
  "prompt": "Finish my sentence",
  "max_characters": 512,
};

fetch("https://example-text-generator.hosted-models.stage.runwayml.cloud/v1/", {
  method: "POST",
  headers: {
    "Accept": "application/json",
    "Content-Type": "application/json",
    "Authorization": "Bearer <token>", // replace <token> with your endpoint's authorization token
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

## Hosted Models API

We've designed the Hosted Models API to be a simplified subset of the HTTP version of the [Localhost Network API](how-to/network). Each Hosted Model exposes only three routes to interface with all Runway models.

* GET `/v1/` returns metadata about the Hosted Model
* GET `/v1/info` returns the input/output spec of `/v1/query`
* POST `/v1/query` is used to run the model on input and produce output

The GET `/v1` endpoint for each model will always return results quickly. The GET `/v1/info` and POST `/v1/query` have a timeout limit of 10 minutes and can take quite a while to return if the model is waking up (see below), or if the model is taking a while to process the input provided to it.

?> Notably, the `/data` and `/error` routes have been removed from the [Localhost Network API](how-to/network). All model interaction functionality is now provided via the single `/v1/query`.

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

You'll notice the `dataRoute` and `errorRoute` are `null` as these routes are available in the Localhost Network API but have removed in `v1` of the Hosted Models API.

?> Note: The `Authorization: Bearer <token>` header is only required if the Hosted Model is private. Public Hosted Models do not require an `Authorization` header.

### GET `/v1/info`

The GET `/v1/info` route provides metadata describing the inputs and outputs expected from a POST to `/query`. You can use this information at a human level to understand how to craft well-formed POST requests, or at a machine level to auto-generate UI/UX interfaces for your Hosted Models.

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

Hosted Models are designed to always be available to service HTTP requests. In order to provide this functionality at a low cost to you, Hosted Models have three states which have different affects on request latency.

* **Asleep**: The Hosted Model hasn't received any requests for a while and has gone into a dormant state. The next request will wake it up, but take a bit longer to process.
* **Awakening**: The Hosted Model is transitioning from the dormant asleep state into the awake state. Requests processed during this time may have long response times, until the model is awake.
* **Awake**: The Hosted Model is up and running and requests should be processed quickly.

No matter which state the Hosted Model is currently in, it will always be able to satisfy any request you make to it. The only difference from your perspective is that requests to `/v1/info` anf `/v1/query` may take longer to complete if the model is asleep or awakening.

If the increased latency from the wake up process poses a UI challenge for your project, you can choose to poll the `/v1` endpoint and read the `status` property it returns. If the status is `"starting"`, you can expect requests to `/v1/info` and `/v1/query` to experience longer timeouts. If the `status` is `"running"` the model is awake and you can expect low latency from all routes associated with the Hosted Model.

?> Note: Hosted Models are configured to have a 10-minute max timeout for all HTTP requests. This is a worst case scenario value, and you can expect >99% of requests to be processed well within this time window, even if the model is asleep. However, some browsers and HTTP clients enforce lower max timeout values for HTTP requests, so request timeouts may be possible depending on your client configuration.

## Pricing

Hosted Models are charged at $0.001 (1/10th of a cent) per-request. This cost is accrued to the Hosted Model owner for all routes (`/v1/`, `/v1/info`, `/v1/query`) and response status codes. All charges consume Runway credits which can be purchased via the [account](https://account.runwayml.com/) page.

## Security and Access Control

Because Hosted Models accrue a cost to their owner, limiting access to the Hosted Model is important to keep unwanted requests from being serviced and charge. All Hosted Models are private by default and can be optionally made public if cost and public access is not a concern.

Private models are protected from unauthorized use by including a secret token in the Authorization header of all requests. Requests to private models that don't include a header in the format `Authorization: Bearer <token>`, or include the wrong `<token>` value, will receive a 401 Unauthorized response.

?> WARNING: Take care to protect the token associated with each endpoint. Including code that interacts with a private Hosted Model in the JavaScript source of a static web page is not sufficient to protect the model from unauthorized use. The only way to protect your private Hosted Models is to protect the secret token, usually by writing a server-side component which can safeguard the token and proxy authorized requests on behalf of the browser to the Hosted Model API in the case of a web page.

<!--
## Going Further
-->
