# opalrb-loader
> Opal is a compiler for writing JavaScript in Ruby.

This package allows transpiling Ruby files using [Opal](http://opalrb.org) and [webpack](https://github.com/webpack/webpack).

## Installation

```bash
npm install opalrb-loader --save-dev
```

## Usage

[Documentation: Using loaders](http://webpack.github.io/docs/using-loaders.html)

```javascript
// webpack.config.js 
module: {
  loaders: [
    {
      test: /\.rb?$/,
      exclude: /(node_modules|bower_components)/,
      loader: 'opalrb-loader'
    }
  ]
}
```

### Options

See the `Opal::Compiler` [options](https://github.com/opal/opal/blob/master/lib/opal/compiler.rb).

### Examples

It's under [Examples](https://github.com/zetachang/opalrb-loader/tree/master/examples) folder.

* simple: Basic setup without further dependency.
* complex: Compile opal/corelib and other gems.

### Compared to `Opal::Builder`
* Relative `require` is correctly resolved.
* `require_trees` is **not yet implemented**.
* erb is not supported (which should be implemented as separate loader).

### Known issues
* First time compiling is relatively slow compared to Ruby one, use `--watch` option for webpack to speed up dev iteration.
* Use `require` to load JS file is broken, but you can write as below to load JS module (webpack will correctly resolve it).

```ruby
# Inside ruby file
`var $ = require("jquery")`
```
* **stdlib** and some gems may not be correctly compiled, please file an issue if you encounter one.

## Development

* `./build_compiler.sh` to build compiler
* `npm start` to compile `index.es6.js` ([Babel CLI](https://babeljs.io/docs/usage/cli/) is required)

## Contact

[David Chang](http://github.com/zetachang)
[@zetachang](https://twitter.com/zetachang)

## License

Available under the MIT license. See the LICENSE file for more info.