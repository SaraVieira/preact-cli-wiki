## Using Plugins via `preact.config.js`

To make customizing your configuration easier, preact-cli supports plugins. Plugins are essentially `preact.config.js` files that are published to npm as modules that you can install.  Here's the process:

1. Install it:  `npm install --save-dev preact-cli-foo`
2. Create `preact.config.js` file in project directory.
3. Invoke the plugin from your `preact.config.js`:

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
- [**preact-cli-plugin-flow**](https://github.com/SaraVieira/preact-cli-flow): Add `flow` support in your project and scaffhold a `.flowconfig`.
- [**preact-cli-typescript**](https://github.com/wub/preact-cli-plugin-typescript): Adds `typescript` support to your preact project.
