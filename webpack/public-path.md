[back]: https://github.com/rafaelrinaldi/til/tree/master/webpack
[webpack-public-path]: http://webpack.github.io/docs/configuration.html#output-publicpath
[webpack-gh-issue]: https://github.com/webpack/webpack/issues/443

# `publicPath`

Webpack has a very useful configuration that let you specify the base path for
all the assets on your application. It's called
[`publicPath`][webpack-public-path]

## Use cases

There are a few use cases on real applications where this feature becomes
specially neat.

### Set value on build time

For development mode what we usually have is an `assets/` folder that lives on
the same level of our index page. This is fine but let's say you want to host
all these static assets on a CDN on your production environment?

To approach this problem you can easily use a good old environment variable.
Let's say we have a variable `ASSETS_PATH`:

```js
import webpack from 'webpack';

// Whatever comes as an environment variable, otherwise use root
const ASSET_PATH = process.env.ASSET_PATH || '/';

export default {
  output: {
    publicPath: ASSETS_PATH
  },

  plugins: [
    // This makes it possible for us to safely use env vars on our code
    new webpack.DefinePlugin({
      'process.env.ASSET_PATH': JSON.stringify(ASSET_PATH)
    })
  ]
};
```

### Set value on the fly

Another possible use case is to set the public path on the fly. Webpack exposes
a global variable that let's you do that, it's called `__webpack_public_path__`.
So in your application entry point, you can simply do this:

```js
__webpack_public_path__ = process.env.ASSET_PATH;
```

That's all you need. Since we're already using the `DefinePlugin` on our
configuration, `process.env.ASSETS_PATH` will always be defined so we can safely
do that.

---

[← Back][back]
