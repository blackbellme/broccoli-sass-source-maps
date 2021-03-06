# broccoli-sass

The broccoli-sass plugin compiles `.scss` and `.sass` files with
[libsass](https://github.com/sass/libsass).

This is a fork of broccoli-sass that includes support for more options and provides (partial)
support for source maps by embedding the content of the SASS source files in the source map using `sourcesContent`.

Be aware that the paths in the generated source map not correct, but this module does what I need
until the [underlying issue](https://github.com/sass/libsass/issues/908) is resolved.

## Installation

```bash
npm install --save-dev broccoli-sass-source-maps
```

## Usage

```js
var compileSass = require('broccoli-sass-source-maps');

var outputTree = compileSass(inputTrees, inputFile, outputFile, options);
```

* **`inputTrees`**: An array of trees that act as the include paths for
  libsass. If you have a single tree, pass `[tree]`.

* **`inputFile`**: Relative path of the main `.scss` or `.sass` file to compile.
  Broccoli-sass expects to find this file in the *first* input tree
  (`inputTrees[0]`).

* **`outputFile`**: Relative path of the output CSS file.

* **`options`**: A hash of options for libsass. Supported options are:
  `functions`, `indentedSyntax`, `omitSourceMapUrl`, `outputStyle`, `precision`,
  `sourceComments`, `sourceMap`, `sourceMapEmbed`, and `sourceMapContents`.

* **`nodeSass`**: Allows a different version of [node-sass](https://www.npmjs.com/package/node-sass) to be used.

### Example

```js
var appCss = compileSass(['styles', 'vendor'], 'myapp/app.scss', 'assets/app.css');
```
