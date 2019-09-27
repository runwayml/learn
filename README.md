<a href="#" target='_self' >
  <p align="center">
    <img src="./docs/assets/images/banner.png">
  </p>
</a>

[![Runway Slack](https://img.shields.io/badge/slack-runwayml.slack.com-33b279.svg)](https://runwayml.com/joinslack)

This is the public page to learn about how to use [Runway](https://runwayml.com/). This includes technical references, the Runway API docs, tutorials and examples.

The site is online at [http://learn.runwayml.com](http://learn.runwayml.com)

## Developing and running locally

This site is built with [docsify](https://docsify.js.org/#/).

To get started developing locally first install `docsify-cli` globally by running:

```bash
npm i docsify-cli -g
```

Then, clone this repository and then `cd` into the directory.

To start the dev server run:

```bash
docsify start ./docs
```

Now the documentation app will be running at [http://localhost:4000](http://localhost:4000)

```bash
[SSR] Serving ./docs now.
Listening at http://localhost:4000
```

Check [docsify's quick start guide](https://docsify.js.org/#/quickstart) if you have any issues with the development.

## Structure

The source code is hosted inside the [`docs`](https://github.com/runwayml/docs/tree/master/docs) folder.

Every tutorial is named following the `tutorial_[NAME_OF_TUTORIAL].md` syntax. All other pages are listed individually.

There's one global [`style`](https://github.com/runwayml/docs/blob/master/docs/assets/css/style.css) file.

## Contributing

We are happy to receive any pull requests with changes that could make our documentation better and easier to understand.
