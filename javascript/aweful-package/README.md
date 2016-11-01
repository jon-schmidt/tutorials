# Managing a Node.js Application with NPM

This tutorial should serve as a reference for automating a variety of common tasks
with npm and as a reference for structuring `package.json` files and considerations
for developing `npm script` tasks.

I'll be providing some basic task management for a web application that builds
CSS, Javascript, and HTML files from source running tasks such as `build`,
`test`, `publish`, `start` for development and staging. This is list is not
comprehensive and probably not final. Furthermore, this list and the following
recommendations are personal preferences or just plain wrong.

---
## Application Design

Francois Ward's [State of the Art Javascript][2] provided a very useful, and
reasonable place to start with regards to considering the the structure of a
Javascript-heavy project and what libraries and frameworks to accommodate. I have
tried to focus on tool-agnostic `npm run` options to keep these suggestions as
flexible as possible although many *State of the Art* features are overwhelmingly
in support of explicit tooling setups and I've chosen to follow many of the
recommendations linked [above][2] and elsewhere with a strict focus on keeping
the project management within the scope of Node.js/npm.

- *Process Management*: `pm2`
- *Linting*: `eslint`
- *Transpilation*: `Babel`
- *Bundling*: `Webpack` or `Rollup`

### File Structure
```
  app/
    |- build
    |- src/
    |- .gitignore
    |- package.json
```

### Production vs Development vs Staging
Many of the tools are environment aware. (ie: `Babel` accepts the `env` option in
its configuration to control its output.) I have decided to include suggestions
for configuration of environments to control `production`, `development` and
`staging` features.

---
# Tasks

https://github.com/coryhouse/react-slingshot/blob/master/package.json
## Tasks: Building
```
$ npm run build`
$ npm run build:clean        # Cleans up build directory: rm -rf build/**
$ npm run build:js           #
$ npm run build:bundle       #
$ npm run publish            #
```

## build:clean

## build:transpile
Transpiling code is still a fundamental process of developing Javascript
application in 2016 and **Babel** features overwhelmingly as the transpiler of
choice for working with modern JS. I suggest including your settings in your
package's `package.json` file and per directory in a `.babelrc` file as needed.

A consideration which I would delegate to someone with more experience and
knowledge is what browsers and features to support. These concerns may affect
your Babel configs and require you to include something like `babel-polyfill` in
your project.

Suggested packages:
- `babel-cli`
- `babel-preset-latest` or `babel-preset-es2015`;

Suggested plugins:

## deployment

**package.json**

```javascript
  "scripts" : {
    "build:babel" : "babel src -d lib/babel"
  }
  "devDependencies" : {
    "babel-cli" : "^6.0.0"
  },
  "babel" : {
    "env" : {
      "development" : {
        "compact" : false,
        "minified" : false,
        "presets" : ["latest"]
      },
      "production" : {
        "comments" : false,
        "compact" : true,
        "minified" : true,
        "presets" : ["latest"]
      }
    }
  }
```
**webpack.config.js**

### Linting


### Bundling
webpack

jspm



- database
- process management `pm2`
- api `expresss`

### serving files

##
1. build tools
  - **uglifyjs**:


  - **babel**:
  - **rollup**:
  - **systemjs**:
  - **jspm**:
  - **webpack/webpack-dev-server**:
2. serve files
  1. **webpack-dev-server**:
  2. **nginx**:

build
babel
webpack-dev-server
rollup
systemjs


- build
  - html
  - javascript
  - css
- start
  - dev
  - staging
- test
  - html
  - js
  - css
- publish

---
## References
The following sources were used to guide the development of this project:

1. [How It Feels To Learn Javascript in 2016](https://hackernoon.com/how-it-feels-to-learn-javascript-in-2016-d3a717dd577f)
1. [State of the Art Javascript in 2016](https://medium.com/javascript-and-opinions/state-of-the-art-javascript-in-2016-ab67fc68eb0b)
1. [How to Use npm as a Build Tool](https://www.keithcirkel.co.uk/how-to-use-npm-as-a-build-tool/)
1. [Why I Left Gulp and Grunt for npm Scripts](https://medium.freecodecamp.com/why-i-left-gulp-and-grunt-for-npm-scripts-3d6853dd22b8)
