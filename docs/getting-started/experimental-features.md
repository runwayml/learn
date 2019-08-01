# Experimental Features 🧪

Runway is currently in beta. This means that we are actively developing the application and things are constantly changing. But one of the cool things about being in beta is that you get to try new experimental features often!

This page contains descriptions of our current experimental features and details on how to use them.

## Active Experimental Features

- [Chaining](#chaining)
- [Local GPU](#local-gpu)

### Chaining

?> Chaining is available as of beta version 0.7.0

Model chaining is a functionality inside Runway that allows you to use the output of one model as the input of another one, effectively chaining them together. This becomes very helpful when you want to create a continuous pipeline of processing for a given input, allowing you to explore an even more extensive and comprehensive set of creative workflows.

##### Things to keep in mind 🧠

- Not all models can be connected to one another. Only models with matching input/output types can be chained together. For example, models that expects text as input can only be the downstream chains of models that produce text-based output.
- Be sure to run all models before expecting the final output!

##### Learn More 👇🏽

- [Check out a few quick experiments](https://docs.runwayml.com/#/how-to/chaining-models-together)
- [Check the release notes](https://runwayml.com/release-notes)
- [Check the support page](https://support.runwayml.com/en/articles/3140662-understanding-how-chaining-works)

### Local GPU

?> Local GPU is available as of beta version 0.8.0

If you are running Linux and have an NVIDIA graphics card that supports CUDA, you can now run models using your own GPU hardware. See the [support page](#) for a list of prerequisites required to get local GPU working and the [tutorial](https://docs.runwayml.com/#/how-to/local-gpu) to walk through installing them yourself if you don't already have them.

##### Learn More 👇🏽

- [Check out the Local GPU tutorial](https://docs.runwayml.com/#/how-to/local-gpu)
- [Check the release notes](https://runwayml.com/release-notes)
- [Check the support page](#)
