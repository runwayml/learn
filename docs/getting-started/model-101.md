# Models 101

At the core of Runway, we have machine learning models. But what do mean by the term model and how do we use a model? Here we discuss what a model is and why we need it within Runway.

## What is a Model? How is a Model Created?

We use the term model as a high-level representation of AI logic.  Models contains a series parameters and soft rules that can be both decided by both humans and machine intelligence. For example, a model may itself learn how to recognize a face in a video or image. A researcher has given the model, images containing faces and over time, the model has learned what a face looks like. This is an example of a form of recognition. We often take recognition for granted, as we learned how to recognize people and inanimate objects as we learned as a child. But imagine how tricky it is for a computer to learn and recognize!

When the researcher feeds the model by giving it some data such as images, text, video, this is what we call *training data*. When it's finished learning, the researcher then *tests* the model, to see if it's been able to learn. We see if the model has learned the data if its output is relevant. For example, can it recognize a face now that it's seen so many images of faces?

### Types of Models

- **Extract** - can extract information from some form of input. For example, facial tracking allows us to extract if a face exists in an image.
- **Generate** - is where a model learns from its input to try and generate new. For example, if as a child we are only taught about the artist [Picasso](https://www.pablopicasso.org/), then will our art style be that of Picasso's? If we show a model all of Picasso's work, that is the only art style it knows. So a generative model will try to create new work based on Picasso's style.
- **Transform** - a model transforms the input that is given to it. For example. If we apply stylisation to an image, so it looks like it's been painted by Vincent van Gogh.

### ML Models in the world

Now you know more about Models, what can models do? People have trained and built models for many different purposes. Below are examples of what models can do:

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

Most models can run in Runway's cloud infrastructure. We do this, as sometimes our machines are not powerful enough, nor have a GPU that will work for that specific model. Find out [how to run your first model](how-to/run-a-model.md)

In order to run your model in the cloud with the help of GPU, use the toggle switch within your workspace. This allows you to choose if you want to run on your machine or run in the cloud.

![Remote GPU](assets/images/model_101/running_remotely.png)

Some models are able to run locally. In order to know if a model runs remotely, we can look at the model's characteristics inside the model's overview page. For example, we can see this model, has GPU support, but not CPU support. If a model has CPU support, we can run it on our computer. Read more about how you can run a model on your computer [how to run your first model](how-to/docker.md)

![characteristics](assets/images/model_101/model-characteristics.png)


## Current Support on Runway

Runway currently supports Cloud GPU and Local CPU. Read more about [running models on Cloud GPU](how-to/run-a-model.md) and [running models on Local CPU](how-to/docker.md)

## Model Licenses, Attributions and Publishers

It's important to note, that each model comes with a license. Please do check before using them! Some of the model's outputs may be restricted to non-commercial purposes. You can learn more about the license of a model in the 'License' tab of every model.

![Licensing](assets/images/model_101/licensing_attributes.png)
