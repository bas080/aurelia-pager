# Configurations

It is possible to alter the default values for bindables and to change the view
aurelia-pager components use.

## Defaults

Aurelia-pager ships with some default values for the bindables. It does however
allow you to change the defaults. This is done where one registers the plugin.

Currently aurelia-view-manager has two configurable properties.

- range = 3
- limit = 30

```js

    /* ... */

    aurelia.use

    .plugin('aurelia-pager', pager => {
      pager.configure({
        range: 5,
        limit: 40
      });
    })

    /* ... */

```

## View

Aurelia-pager currently only supports bootstrap's render strategy. This is done
using [aurelia-view-manager](https://github.com/spoonx/aurelia-view-manager).
It is possible to write your own views and use those instead of the default
bootstrap view. Read more about it over at the aurelia-view-manager docs.
