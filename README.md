package-requirejs
=================

Generate a valid requirejs-config.js file automatically detecting all the package.json dependencies

### How to use

Install the package

```bash
$ sudo npm install package-requirejs -g
```

Trigger the following shell command from the the folder containing your package.json, being sure to have all your local dependencies already installed

```bash
$ package-requirejs
```

This command will generate a require-config.js file into the current folder.

#### Example

Having a `package.json` like the following

```json
{
  "name": "MyScript",
  "dependencies": {
    "backbone": "^1.1.2",
    "jquery": "^2.1.1"
  }
}
```

`package-requirejs` will produce a requirejs-config.js file like this one

```javascript
requirejs.config({
  paths: {
    "underscore": "node_modules/backbone/node_modules/underscore/underscore",
    "backbone": "node_modules/backbone/backbone",
    "jquery": "node_modules/jquery/dist/jquery"
  },
  shim: {
    "backbone": [
      "underscore"
    ]
  }
});
```

#### Options

You can pass your custom options to `package-requirejs` in the following order

 1. Output of the script (`requirejs-config.js` default)
 2. Path to prepend to all the requirejs paths modules (`""` default)
 3. Property in your package.json where the script can loop the dependencies installed (`"dependencies"` default)

```bash
$ package-requirejs path/to/the/output/requirejs-config.js ../path/to/prepend/to/the/modules
```


