## Using Plugins via `preact.config.js`

To make customizing your configuration easier, preact-cli supports plugins. Plugins are essentially `preact.config.js` files that are published to npm as modules that you can install.  Here's the process:

1. Install it:  `npm install --save-dev preact-cli-foo`
2. Invoke it from your `preact.config.js`:

    ```js
    import foo from 'preact-cli-foo';
    export default (config, env, helpers) => {
      config = foo(config, helpers);
      return config;
    };
    ```

## List of Plugins

- [**preact-cli-lodash**](https://github.com/SaraVieira/preact-cli-lodash): Optimize builds using `babel-plugin-lodash` & `lodash-webpack-plugin`.
- [**preact-cli-postcss**](https://github.com/SaraVieira/preact-cli-postcss): Replaces default PostCSS config with your `postcss.config.js`