## Some common recipes for use in `preact.config.js`.

See [`webpack-helpers`](https://github.com/developit/preact-cli/blob/master/docs/webpack-helpers.md) for reference on helpers argument.

### Customising babel options (using loader helpers)

To customize babel config `babel-loader` options have to be changed.

```
export default (config, env, helpers) => {
  let { rule } = helpers.getLoadersByName(config, 'babel-loader');
  let babelConfig = rule.options;
  
  babelConfig.plugins.push('my-chosen-plugin');
  babelConfig.env = { ...some settings... }
};
```

### Disabling source maps (using plugin helpers)

```
export default (config, env, helpers) => {
  let { plugin } = helpers.getPluginsByName(config, "UglifyJsPlugin")[0];
  plugin.options.sourceMap = false
}
```

### Conditional changes based on env

```
export default (config, env, helpers) => {
  if (env.ssr) {
    ...do sth for prerender...
  } else {
    ...do sth for regular bundles...
  }

  if (env.production) {
   ...do sth for production...
  } else {
   ...do sth for watch mode...
  }
}
```

### Setting proxy for dev server (using config directly)

```
export default config => {
  config.devServer.proxy = [
    {
      path: '/api/**',
      target: 'http://api.example.com',
      ...any other stuff...
    }
  ];
};
```

### Removing plugin, loader or rule

Each wrapper for plugin, loader or rule comes with it's position in array so that it can be easily removed.
```
export default (config, env, helpers) => {
  let { index } = helpers.getPluginsByName(config, 'some-plugin')[0]
  config.plugins.splice(index, 1)
};
```