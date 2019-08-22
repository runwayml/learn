# Machine Learning Models

Runway is a platform for publishing open source, pre-trained machine learning models. What do we mean by the term **model**, and how can we use one in Runway?

### What is a Model?

The term model refers to the result of training a machine learning algorithm with a dataset. The algorithm finds patterns within the data and develops its own rules for how to represent—or model—those patterns to perform a specific task. These rules are not designed by humans, they are learned from the data on which the model is trained. 

For example, a model may learn to detect a face in a video or image. In order to recognize faces, it needs to be trained on a dataset of many different types of faces. Once trained, it should be able to recognize faces from pictures or videos it has never seen before. In reality the process is complex: it involves collecting a large number of data points, creating multiple datasets (for training, validation, and testing), designing the model architecture, selecting the right hyperparameters, and then training the model using high-performance dedicated hardware, such as a graphics processing unit (GPU).

People build models in different programming languages, with different frameworks, and for different purposes, such as to recognize emotions, objects, people, body positions, hot-dogs, spam email, and unique sounds. There are models that generate photorealistic faces, captions, streets, building facades, human voices, and videos of airplanes morphing into cats. Some models detect cancer, malaria, and HIV. 

It is important to note that models are trained on the data given to them, which means that they incoporate the biases of that data. Some trained models are ethically dubious and raise important questions about the social impact of algorithms in our society, such as models used to screen job applicants or to predict crime. 

Reality is complex, and a model will never completely mimic real phenomena. But models can capture and reproduce the broad strokes of generalizable behavior. As you venture down the exciting path of machine learning, keep in mind the famous words of the great statistician George Box: "All models are wrong, but some are useful".

### Types of Models

There are many types of machine learning models. To start, we can categorize models in three broad types:

- **Extract and Identify**: These models extract and identify information from some form of input. For example, facial tracking models identify if a face exists in an image. Other examples include detecting objects, body positions, animals, facial expressions, types of music, and even carcinogenic cells and malaria.
- **Generate**: These models generate synthetic outputs based its training data, such as photorealistic images, coherent text, and music.
- **Transform**: These models transform or modify a given input and some examples include automatic language translation as well as image stylization and colorization techniques.

### Using Models in Runway

Depending on the model, there are two ways to run models in Runway: locally, using your computer's CPU, or with a remote GPU in Runway's cloud infrastructure. To run a model on your computer, you'll need to download it and also install Docker. Visit our guide to learn how to [Run Models Locally (With Docker)](how-to/run-models-locally.md). Running a model with remote GPU [uses credits](https://support.runwayml.com/credits-and-plans/how-much-does-runway-cost), but the model runs much faster (and we don't have to wait several minutes for it to download).

Try running your first model in Runway [here](tutorials/tutorial_t2i.md)!

You can also import your own machine learning models for your creative projects. Visit our [model importing guide](how-to/import-models.md) to learn more.

### Model Licenses, Attributions, and Publishers

Every model in Runway is licensed for a specific type of use. Please do check before using them! Some of the models' outputs may be restricted to non-commercial purposes. You can learn more about the license on a model's overview page in its 'License' tab.

![Licensing](assets/images/model_101/licensing_attributes.png)
