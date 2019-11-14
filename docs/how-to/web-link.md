# Link to Models in RunwayML

You can create simple web links that will open the RunwayML app to a specific model from a web browser. This is super useful when creating tutorials, workshops resources, embedding buttons on your website, and opening models directly from a GitHub repository.

This tutorial will teach you how to create those links and embed them in your website.

## Step 1: Create a Link

If you [ported your own model](/how-to/import-models) or want to link to an existing model in RunwayML, all you need is the **username** of the publisher and the **model name**. To create a web link just follow the format:

```
https://open-app.runwayml.com/?model=genekogan/spade-landscapes
```

Where `?model=genekogan/spade-landscapes` is the model to open. In this case, `genekogan` is the **username** and `spade-landscapes` is the **name of the model**.

If you omit the `?model=<username>/<model_name>` format in the web link, the RunwayML app will open to the models directory.

```
https://open-app.runwayml.com
```

## Step 2: Create a Badge

[![Open in RunwayML Badge](https://open-app.runwayml.com/gh-badge.svg)](https://open-app.runwayml.com/?model=genekogan/spade-landscapes)

To create a badge (in GitHub or on your website, for example) that will open to your model in RunwayML, use the following template:

### Markdown Format:

```
[![Open in RunwayML Badge](https://open-app.runwayml.com/gh-badge.svg)](https://open-app.runwayml.com/?model=genekogan/spade-landscapes)
```

### HTML Format:
```
<a href="https://open-app.runwayml.com/?model=genekogan/spade-landscapes" target="_blank"><img src="https://open-app.runwayml.com/gh-badge.svg" width=120/></a>
```
