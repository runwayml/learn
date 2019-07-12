# Experimental Features 🧪

Runway is currently in beta. This means that we are actively developing the application and things are constantly changing. But one of the cool things about being in beta is that you get to try new experimental features often!

This page contains descriptions of our current experimental features and details on how to use them.

## Active Experimental Features

- ### Chaining (available as of beta version 0.6.11)

Model chaining is a functionality inside Runway that allows you to use the output of one model as the input of another one, effectively chaining them together. This becomes very helpful when you want to create a continuous pipeline of processing for a given input, allowing you to explore an even more extensive and comprehensive set of creative workflows.

##### Things to keep in mind 🧠
- Not all models can be connected to one another. Only models with matching input/output types can be chained together. For example, models that expects text as input can only be the downstream chains of models that produce text-based output.
- Be sure to run all models before expecting the final output!

##### Learn More 👇🏽
- Check out a few quick experiments
- Check the release notes
- Check the support page
