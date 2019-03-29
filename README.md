# Ember Webpack Loaders

A set of webpack loaders to help with ember integration.

Check the example app here: https://github.com/tulios/ember-webpack-example

Check the rails 5.1 app using these loaders https://github.com/rajibahmed/ember-react-webpack-rails-demo

Use VERSION 0.2.0 if you're using webpack1 https://github.com/tulios/ember-webpack-loaders/tree/0.2.0

## Install

```sh
npm install ember-webpack-loaders
```

## Usage

Apply this set of loaders to your `webpack.config.js`:

```js
{
  module: {
    rules: [
      {
        test: /\.hbs$/,
        include: /app\/templates/, // or whatever directory you have
        loader: 'ember-webpack-loaders/htmlbars-loader'
      },
      {
        test: /app\/index\.js/, // the main app file
        use: [
            {
              loader: 'ember-webpack-loaders/inject-templates-loader',
              options: {
                appPath: './path/to/app',
              }
            },
            {
              loader: 'ember-webpack-loaders/inject-modules-loader',
              options: {
                appPath: './path/to/app',
              }
            }
         ],
       }
    ]
  }
}
```

## Options

#### for ember-webpack-loaders/htmlbars-loader

* __appPath__: Path for your ember app. Default assuming `webpack.config.js` in root folder and `./app`
* __templateCompiler__: default 'ember-source/dist/ember-template-compiler.js'

#### for ember-webpack-loaders/inject-templates-loader

* __appPath__: Path for your ember app. Default assuming `webpack.config.js` in root folder and `./app`

#### for ember-webpack-loaders/inject-modules-loader

* __appPath__: Path for your ember app. Default assuming `webpack.config.js` in root folder and `./app`
* __appVar__: Variable name of your `Ember.Application`. Default `App`

Example:

```js
{
  module: {
    rules: [
      {
        test: /app\/index\.js/,
        use: [ 
          {
            loader: 'ember-webpack-loaders/inject-templates-loader'
          },
          {
            loader: 'ember-webpack-loaders/inject-modules-loader',
          }
        ],
        options: {
          appVar: 'MyProject'
        }
      }
    ]
  }
}
```

## License

See [LICENSE](https://github.com/tulios/ember-webpack-loaders/blob/master/LICENSE) for more details.
