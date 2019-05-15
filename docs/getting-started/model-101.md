# Models 101

At the core of Runway, we have models. But what exactly is a model and how does it work? Here we discuss what a model is and why we need it within the Runway App.

## What is a Model? How is a Model Created?

We use the term model, as a high level representation of AI logic.  The model itself, contains a set of series and rules, that can be both decided and determined by humans and machine intelligence. For example, a model may itself learn how to recognise a face in a video or image. A researcher has given the model, images containing faces and over time, the model has learned what a face looks like. This is an example of a form of recognition. We often take recognition for granted, as we learnt how to recognise people and inanimate objects as we learned as a child. But imagine how tricky it is for a computer to learn and recognise!

When the researcher feeds the model by giving it some data such as images, text, video, this is what we call *training data*. When it's finished learning, the researcher then *tests* the model, to see if it's been able to learn. We see if the model has learned the data from if it's output is relevant, For example. can it recognise a face now it's seen so many images of faces?

### Types of Models

- **Extract** - can extract information from some form of input. For example, facial tracking allows us to extract if a face exists in an image.
- **Generate** - is where a model learns from its input to try and generate new. For example, if as a child we are only taught about the artist [Picasso](https://www.pablopicasso.org/), then will our art style be that of Picasso's? If we show a model all of Picasso's work, that is the only art style it knows. So a generative model will try to create new work based on Picasso's style.
- **Transform** - a model transforms the input that is given to it. For example. If we apply stylisation to an image, so it looks like it's been painted by Vincent van Gogh.

## Endless possibilities of Models

Now you know more about Models, what can models do? People have trained and built models for many different purposes. Below are some of the models we have detected:

* Recognition: emotions, objects, people body positions, hot-dogs, spam and sounds
* Generate: photorealistic faces, captions, streets, facades, voices and videos of airplanes morphing into cats
* Detect: models to detect cancer, malaria and HIV

Some trained models are ethically dubious and raise important questions about the social impact of algorithms and biases in our society such as models used to screen job applicants or predict crime. People build models in different programming languages, with different frameworks and for different purposes.

## Where to find models?

On the Runway app you can browse through a selection of models and search according to your needs. Do check out our guide on [browsing models on Runway](how-to/browse-model-directory). The models we show in Runway, are all based on researchers work whom kindly share their work on [Github](https://github.com/).

When researchers have finished working on a making a model, often they share this on a platform called [Github](https://github.com/). If you are familiar with Github, then look into our [Importing Models into Runway](how-to/importing) tutorial.


## Our Top Models to try out

Currently on Runway we provided a short list of the teams favorite models to get started with! Below are some recommendations, or checkout our tutorial on [browsing models on Runway](how-to/browse-model-directory).

![Top Models](assets/images/model_101/recommended_models.png)


## Running Models Locally vs. The Cloud

Some of the models you may wish to run remotely (on the 'cloud') as opposed to locally. We do this, as sometimes our machines are not powerful enough, nor have a GPU that will work for that specific model ([Read more about GPUs](getting-started/the-world-of-gpus)).

In order to run remotely, use the toggle switch within your workspace. This allows you to choose if you want to run on your machine or run in the cloud.

![Remote GPU](assets/images/model_101/running_remotely.png)

## Model Licenses, Attributions and Publishers

It's important to note, that each model comes with a license. Please do check before use! Some of the models outputs may be restricted to non-commercial purposes. You and the license on the models tab labelled 'License'

Equally, as important we aim to attribute and provide the publishers of the model. If you notice these to be in error, require additional information,

![Licensing](assets/images/model_101/licensing_attributes.png)
