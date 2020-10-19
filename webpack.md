---
description: >-
  webpack is a static module bundler for modern JavaScript applications. When
  webpack processes your application, it internally builds a dependency graph
  which maps every module your project needs and g
---

# Webpack

* Entry
* Output
* Loaders
* Plugins
* Mode
* Browser Compatibility

## Dependency Graph

Any time one file depends on another, webpack treats this as a _dependency_. This allows webpack to take non-code assets, such as images or web fonts, and also provide them as _dependencies_ for your application.

When webpack processes your application, it starts from a list of modules defined on the command line or in its config file. Starting from these [_entry points_](https://webpack.js.org/concepts/entry-points/), webpack recursively builds a _dependency graph_ that includes every module your application needs, then bundles all of those modules into a small number of _bundles_ - often, just one - to be loaded by the browser.



### Entry <a id="entry"></a>

An **entry point** indicates which module webpack should use to begin building out its internal [dependency graph](https://webpack.js.org/concepts/dependency-graph/). webpack will figure out which other modules and libraries that entry point depends on \(directly and indirectly\).

**webpack.config.js**

```text
module.exports = {
  entry: './path/to/my/entry/file.js'
};
```

### Output <a id="output"></a>

The **output** property tells webpack where to emit the _bundles_ it creates and how to name these files. It defaults to `./dist/main.js` for the main output file and to the `./dist` folder for any other generated file.

You can configure this part of the process by specifying an `output` field in your configuration:

**webpack.config.js**

```text
const path = require('path');

module.exports = {
  entry: './path/to/my/entry/file.js',
  output: {
    path: path.resolve(__dirname, 'dist'),
    filename: 'my-first-webpack.bundle.js'
  }
};
```

the `output.filename` and the `output.path` properties to tell webpack the name of our bundle and where we want it to be emitted to. 



### Loaders <a id="loaders"></a>

Out of the box, webpack only understands JavaScript and JSON files. **Loaders** allow webpack to process other types of files and convert them into valid [modules](https://webpack.js.org/concepts/modules) that can be consumed by your application and added to the dependency graph.

> Note that the ability to `import` any type of module, e.g. `.css` files, is a feature specific to webpack and may not be supported by other bundlers or task runners. We feel this extension of the language is warranted as it allows developers to build a more accurate dependency graph.

At a high level, **loaders** have two properties in your webpack configuration:

1. The `test` property identifies which file or files should be transformed.
2. The `use` property indicates which loader should be used to do the transforming.

**webpack.config.js**

```text
const path = require('path');

module.exports = {
  output: {
    filename: 'my-first-webpack.bundle.js'
  },
  module: {
    rules: [
      { test: /\.txt$/, use: 'raw-loader' }
    ]
  }
};
```

### Plugins <a id="plugins"></a>

While loaders are used to transform certain types of modules, plugins can be leveraged to perform a wider range of tasks like bundle to improve proformance, asset management and injection of environment variables.

In order to use a plugin, you need to `require()` it and add it to the `plugins` array. Most plugins are customizable through options. Since you can use a plugin multiple times in a config for different purposes, you need to create an instance of it by calling it with the `new` operator.

Tapable

This small library is a core utility in webpack but can also be used elsewhere to provide a similar plugin interface. Many objects in webpack extend the `Tapable` class. The class exposes `tap`, `tapAsync`, and `tapPromise` methods which plugins can use to inject custom build steps that will be fired throughout a compilation.

Please see the [documentation](https://github.com/webpack/tapable) to learn more. An understanding of the three `tap` methods, as well as the hooks that provide them is crucial. The objects that extend `Tapable` \(e.g. the compiler\), the hooks they provide, and each hook's type \(e.g. the `SyncHook`\) will be noted.



**webpack.config.js**

```text
const HtmlWebpackPlugin = require('html-webpack-plugin'); //installed via npm
const webpack = require('webpack'); //to access built-in plugins

module.exports = {
  module: {
    rules: [
      { test: /\.txt$/, use: 'raw-loader' }
    ]
  },
  plugins: [
    new HtmlWebpackPlugin({template: './src/index.html'})
  ]
};
```

In the example above, the `html-webpack-plugin` generates an HTML file for your application by injecting automatically all your generated bundles.





By setting the `mode` parameter to either `development`, `production` or `none`, you can enable webpack's built-in optimizations that correspond to each environment. The default value is `production`.

```text
module.exports = {
  mode: 'production'
};
```

## Hot Module Replacement

\(HMR\) exchanges, adds, or removes [modules](https://webpack.js.org/concepts/modules/) while an application is running, without a full reload. This can significantly speed up development in a few ways:

* Retain application state which is lost during a full reload.
* Save valuable development time by only updating what's changed.
* Modifications made to CSS/JS in the source code results in an instant browser update which is almost comparable to changing styles directly in the browser's dev tools.

The following steps allow modules to be swapped in and out of an application:

1. The application asks the HMR runtime to check for updates.
2. The runtime asynchronously downloads the updates and notifies the application.
3. The application then asks the runtime to apply the updates.
4. The runtime synchronously applies the updates.

In addition to normal assets, the compiler needs to emit an "update" to allow updating from previous version to the new version. The "update" consists of two parts:

1. The updated [manifest](https://webpack.js.org/concepts/manifest) \(JSON\)
2. One or more updated chunks \(JavaScript\)

The manifest contains the new compilation hash and a list of all updated chunks. Each of these chunks contains the new code for all updated modules \(or a flag indicating that the module was removed\).

The compiler ensures that module IDs and chunk IDs are consistent between these builds. It typically stores these IDs in memory \(e.g. with [webpack-dev-server](https://webpack.js.org/configuration/dev-server/)\), but it's also possible to store them in a JSON file.

