# Klei Generator [![Build Status](https://secure.travis-ci.org/klei/generator-klei.png?branch=master)](https://travis-ci.org/klei/generator-klei)

> A Yeoman generator for generating awesome module or app boilerplates! MEAN-stack (all parts optional) with scalability in mind and with Grunt and Bower sweetness..

## Differences from similiar generators

The Klei generator is built with scalability in mind. Which means that it doesn't have one file per object type (think AngularJS directives e.g) and neither one directory per object type, which is really common but not particularly good in the long run.

Instead the Klei generator advocates (and creates, particularly the subgenerators) one directory per module. Here's a [great read on scalable code organization with AngularJS](https://medium.com/opinionated-angularjs/9f01b594bf06).

### Great experience for developers

The goal with the Klei generator is to create a great, easy to use and maintainable project structure and development environment for web development with full stack Javascript.

## Getting Started

### Install Yeoman

```bash
$ npm install -g yo
```

### Install the Klei Generator

```bash
$ npm install -g generator-klei
```

### Install Bower

This is only needed if "Client APP" or "Stylesheets" are to be chosen in the generator.

```bash
$ npm install -g bower
```

### Do the magic:

```bash
$ yo klei
```

### Run the app:

```bash
$ grunt serve
```
> **Don't forget that your mongodb server should already be running!** (if you chose MongoDB in the generator)

### Run in production

The generator doesn't yet generate a fully production ready configuration following all best practices, but at least you must do the following steps:

#### Without REST API's

Build everything and run the static resource server (a `connect` server) with:

```bash
$ grunt serve:dist
```

#### With REST API's

First build everything for distribution:

```bash
$ grunt dist
```

Then run the server:

```bash
$ NODE_ENV=production node src/index.js
```

**N.B.** You should be using something like [Forever](https://npmjs.org/package/forever) or similar to keep the server up and running.


## What can the Klei Generator do?

The Klei Generator asks you what type of module you want to build, then you pick the parts you want from:

* REST API's - using [Express.js](http://expressjs.com)
* MongoDB - using [Mongoose](http://mongoosejs.com)
* Client - using [AngularJS](http://angularjs.org)
* Stylesheets - using [Stylus](http://learnboost.github.io/stylus/)

### What you'll get:

* A scalable directory structure (Todo list example included)
  - Not one directory per object type, which doesn't scale well, but instead one per REST mount point (backend) and one per view (frontend)
* A fully configured Gruntfile with livereload, serverreload, linting, concatenation, minification, testing etc.
* Automounting of API routes using [exctrl](https://npmjs.org/package/exctrl)
* No more editing of your html layout when adding scripts and stylesheets to your project, thanks to [grunt-injector](https://npmjs.org/package/grunt-injector)
  - This includes Bower installed components (which have a main section in their bower.json)
* Both frontend and backend unit testing with [Mocha](http://mochajs.org/) and [Chai](http://chaijs.com/)!
  - Frontend tests is run with [Karma](http://karma-runner.github.io/)
  - All necessary files are injected automatically into your `karma.conf.js` with the [grunt-injector](https://npmjs.org/package/grunt-injector)
* Subgenerators to easy add new API's, etc. (see Subgenerator section below)
* and more.. There's even more to come!

**Try it out!**

## Subgenerators

### klei:api

Usage:

```bash
$ yo klei:api "<you new api name here>"
```

Or just:

```bash
$ yo klei:api
```

And follow the guide.
The name you give to your new API will be camelized and used as: `./src/api/<newApiNameHere>/<newApiNameHere>.controller.js` which in turn will be mounted at the url: `/api/<newApiNameHere>`.

The generator will ask if you want to create a new Mongoose model as well.

### More to come...

## Contribute

Please feel free to contribute and help with building the best boilerplate for a great developer experience! I gladly accept pull requests!


## License

[MIT License](http://en.wikipedia.org/wiki/MIT_License)
