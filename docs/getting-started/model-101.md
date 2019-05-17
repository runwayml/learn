# Models 101

At the core of Runway, we have machine learning models. But what do mean by the term model and how do we use a model? Here we discuss what a model is and why we need it within Runway.

## What is a Model? How is a Model Created?

We use the term model as a high-level representation of AI logic.  Models contains a series parameters and soft rules that can be both decided by both humans and machine intelligence. For example, a model may itself learn how to detect a face in a video or image. A researcher has given the model images containing faces and over time, the model has learned what a face looks like. Now the model can detect a face in an image or video. We often this for granted, as we learnt as a child how to identify people and inanimate objects. But imagine how tricky it is for a computer to learn and recognize!

When the research gives a model data such as images, text, video, this is what we call *training data*. When it's finished learning, the researcher then *tests* the model, to see if it's been able to learn. The model has learned if we find it's output is relevant. For example, Is the model now able to identify a human in an image?

### Types of Models

We can categorise models as three types: Extract, Generate and Transform.

- **Extract** - can extract information from some form of input. For example, facial tracking allows us to extract if a face exists in an image.
- **Generate** - the model generates synthetic output based on the data it has been trained on. For example, if a child is only taught about [Picasso](https://www.pablopicasso.org/), they are likely to try and produce artwork in Picasso's style. Hence a generative model trained on Picasso will create synthetic work based on Picasso's style.
- **Transform** - the model transforms the input that it is given. For example. A model can apply stylisation to a photograph, so it looks like an artistic painting by Vincent Van Gogh.

### ML Models in the world

People have trained and built models for many different purposes. Below are examples of what models can do:

* Extract: emotions, objects, people's body positions, cancer detection, malaria detection and HIV detection
* Generate: photorealistic faces, captions, streets, facades and voices and videos of airplanes morphing into cats
* Transform: image stylisation and colorization

Some trained models are ethically dubious and raise important questions about the social impact of algorithms and biases in our society such as models used to screen job applicants or predict crime. People build models in different programming languages, with different frameworks and for different purposes.

## Where to find models?

On Runway, you can easily browse different types of models and search according to your needs. Please check out our guide on [browsing models on Runway](how-to/browse-model-directory).


## Staff Picks: top models to try

Currently on Runway we provided a short list of the team's favorite models to get started with! Below are some recommendations, or checkout our tutorial on [browsing models on Runway](how-to/browse-model-directory).

![Top Models](assets/images/model_101/recommended_models.png)


## Running Models Locally vs. The Cloud

Most models can run in Runway's cloud infrastructure. We do this, as sometimes our machines are not powerful enough. Find out [how to run your first model](how-to/run-a-model.md)

In order to run your model in the cloud with the help of GPU, use the toggle switch within your workspace. This allows you to choose if you want to run on your machine or run in the cloud.

![Remote GPU](assets/images/model_101/running_remotely.png)

Some models are able to run locally. In order to know if a model runs remotely, we can look at the model's characteristics inside the model's overview page. For example, we can see this model, has GPU support, but not CPU support. If a model has CPU support, we can run it on our computer. Read more about how you can run a model on your computer [how to run your first model](how-to/docker.md)

![characteristics](assets/images/model_101/model-characteristics.png)


## Current Support on Runway

Runway currently supports Cloud GPU and Local CPU. Read more about [running models on Cloud GPU](how-to/run-a-model.md) and [running models on Local CPU](how-to/docker.md)


## Model Licenses, Attributions and Publishers

It's important to note, that each model comes with a license. Please do check before using them! Some of the model's outputs may be restricted to non-commercial purposes. You can learn more about the license of a model in the 'License' tab of every model.

![Licensing](assets/images/model_101/licensing_attributes.png)
