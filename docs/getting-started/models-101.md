# Models 101

At the core of Runway you will find machine learning models. But exactly what do we mean by the term *model* and how can we use a model? Here we discuss what a model is and how to use it in Runway.

## What is a Model?

The term model often refers to the result of training a machine learning algorithm with a specific data set. This learning algorithm uses the data its provided to learn a series of rules that are encoded into what we call a model. We can then use the model, or the learned set of rules, for a variety of things.

For example, a model may learn how to detect a face in a video or image. For this to happen, someone has to train the learning algorithm with images containing the faces we want to detect. Once the algorithm has use the provided data to come up with a series of rules of what faces look like, we have a machine learning model. If trained properly, this model should be able to detect a face in an image or video.

When providing an algorithm data – such as images, text, or audio files - we refer to the data as *training data*. When the model is created and the algorithms have finished learning about the data, we can *test* the model to see if it was able to learn from the training data.

### Types of Models

There are many types of machine learning models. But in general, we can categorize models in three broad types. Models to Extract and Identify, Models to Generate, and Models to Transform.

- **Extract and Identify**: These are models that can extract and identify information from some form of input. For example, facial tracking models identify if a face exists in an image.
- **Generate**: These are models that can generate synthetic outputs based on the data it has been trained on. They can hallucinate new images, text, sound, and more.
- **Transform**: These are models that are able to transform and modify a given input. Think of automated translation from one language into another.

### Models in the world

People have trained and built models for many different purposes. Below are examples of what models can learn to do:

* **Extract and Identify**: Objects, people's body positions, animals, face expressions, types of music. Even carcinogenic cells and malaria.
* **Generate**: Photorealistic images, coherent text and music.
* **Transform**: Apply image stylization and colorization techniques.

Some trained models are ethically dubious and raise important questions about the social impact of algorithms and biases in our society such as models used to screen job applicants or predict crime. People build models in different programming languages, with different frameworks, and for different purposes.

## Using Models in Runway

In Runway, you can run and create a variety of machine learning models. Models can be used and run in Runway's cloud infrastructure or run locally on your computer. Find out more about [how to run your first model in Runway](tutorials/tutorial_t2i.md).

## Model Licenses, Attributions, and Publishers

It's important to note that every model in Runway is licensed for a specific type of use. Please do check before using them! Some of the model's outputs may be restricted to non-commercial purposes. You can learn more about the license of a model in its 'License' tab.

![Licensing](assets/images/model_101/licensing_attributes.png)
