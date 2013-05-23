# grunt-simple-templates

> Simple compilation of JavaScript templates into objects

## Getting Started
This plugin requires Grunt `~0.4.1`

If you haven't used [Grunt](http://gruntjs.com/) before, be sure to check out the [Getting Started](http://gruntjs.com/getting-started) guide, as it explains how to create a [Gruntfile](http://gruntjs.com/sample-gruntfile) as well as install and use Grunt plugins. Once you're familiar with that process, you may install this plugin with this command:

```shell
npm install grunt-simple-templates --save-dev
```

Once the plugin has been installed, it may be enabled inside your Gruntfile with this line of JavaScript:

```js
grunt.loadNpmTasks('grunt-simple-templates');
```

## The "templates" task

### Overview
In your project's Gruntfile, add a section named `templates` to the data object passed into `grunt.initConfig()`.

```js
grunt.initConfig({
  templates: {
    options: {
      // Task-specific options go here.
    },
    your_target: {
      // Target-specific file lists and/or options go here.
    },
  },
})
```

### Options

#### options.namespace
Type: `String`
Default value: `'TEMPLATES'`

Your templates will be in an object called `window.#{NAMESPACE}`.

#### options.extension
Type: `String`
Default value: `'mustache'`

Templates matching the extension `options.extension` will be compiled.

### Usage Examples

#### Default Options
In this example, the default options are used to compile Mustache templates. So if the `testing.mustache` file has the content `{{test}}` and the `dir/testing.mustache` file had the content `{{nested test}}`, the generated result would be `window.TEMPLATES = {"testing":"{{test}}\n","dir/testing":"{{nested test}}\n"};\n`

```js
grunt.initConfig({
  templates: {
    options: {},
    files: {
      src: 'templates/',
      dest: 'js/templates.js'
    },
  },
})
```

#### Custom Options
In this example, custom options are used to compile Handlebars templates. So if the `testing.hbs` file has the content `{{test}}` and the `dir/testing.hbs` file had the content `{{nested test}}`, the generated result in this case would be `window.HANDLEBARS = {"testing":"{{test}}\n","dir/testing":"{{nested test}}\n"};\n`

```js
grunt.initConfig({
  templates: {
    options: {
      namespace: 'HANDLEBARS',
      extension: 'hbs'
    },
    files: {
      src: 'templates/',
      dest: 'js/templtes.js'
    },
  },
})
```

## Contributing
In lieu of a formal styleguide, take care to maintain the existing coding style. Add unit tests for any new or changed functionality. Lint and test your code using [Grunt](http://gruntjs.com/).

## Release History

`0.0.2`: Only match provided or default extension.
`0.0.1`: Initial release.
