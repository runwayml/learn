# Runway Documentation

This is the public documentation for [Runway](https://runwayapp.ai/). This includes technical references, the Runway API docs, tutorials and examples.

The documentation is online at [http://docs.runwayapp.ai](http://docs.runwayapp.ai)

## Developing and running locally

The documentation site is built with [docsify](https://docsify.js.org/#/).

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

## Documentation Structure

The source code is hosted inside the [`docs`](https://github.com/runwayml/docs/tree/master/docs) folder.

Every tutorial is named following the `tutorial_[NAME_OF_TUTORIAL].md` syntax. All other pages are listed individually.

There's one global [`style`](https://github.com/runwayml/docs/blob/master/docs/style.css) file.

## Contributing

We are happy to receive any pull requests with changes that could make our documentation better and easier to understand.