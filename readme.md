# Chai HTML

[![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg)](https://github.com/i-like-robots/chai-html/blob/master/LICENSE) [![Build Status](https://travis-ci.org/i-like-robots/chai-html.svg?branch=master)](https://travis-ci.org/i-like-robots/chai-html) [![Coverage Status](https://coveralls.io/repos/github/i-like-robots/chai-html/badge.svg?branch=master)](https://coveralls.io/github/i-like-robots/chai-html) [![npm version](https://img.shields.io/npm/v/chai-html.svg?style=flat)](https://www.npmjs.com/package/chai-html)

HTML assertions plugin for [Chai](http://chaijs.com/).

## Installation

This is a [Node.js] module available through the [npm] registry.

Node 6 or higher is required.

[Node.js]: https://nodejs.org/
[npm]: http://npmjs.com/

You can install using the package manager of your choice:

```sh
# installation with NPM
$ npm install -D chai-html

# or install using Yarn
$ yarn add -D chai-html
```

## Usage

```js
const { use, expect } = require('chai')
const chaiHtml  = require('chai-html')

// Register the plugin
use(chaiHtml)

// Write assertions!
expect('<div><img /></div>').html.to.equal('<div><img></div>')
expect('<h1>Hello World!</h1>').html.to.not.equal('<h1>Hallo Welt!</h1>')
```

HTML assertions will throw an error directing you to the change, so instead of squinting at a long HTML string you'll get something useful:

```js
expect('<img />').html.to.equal('<br />')
// throws: tag <img> was changed to tag <br>

expect('<img src="..." />').html.to.equal('<img src="..." alt="..." />')
// throws: attribute [alt="..."] has been added

expect('<p>Hello World!</p> Hej!').html.to.equal('<p>Hello World!</p>')
// throws: text " Hej!" has been removed
```

## How does it work?

Underneath this plugin uses [parse5](https://github.com/inikulin/parse5) to parse the given HTML strings and normalize the generated trees before being compared. This means that although the two strings of markup may not be the same they should generate equivalent structures.

## Credits

This plugin is heavily inspired by the similar [chai-xml](https://www.npmjs.com/package/chai-xml) plugin.

## License

chai-html is MIT licensed.
