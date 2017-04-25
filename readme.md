# Drupal 8 Theme Using the ZURB Template

This theme makes use of the [Zurb template](https://github.com/zurb/foundation-zurb-template) to include the full set of SCSS and Javascript included with the [Zurb Foundation](http://foundation.zurb.com/) front end framework.

It also includes:

- Handlebars HTML templates with [Panini](https://github.com/zurb/panini)
- [Style Sherpa](https://github.com/zurb/style-sherpa): A basic Style Guide generator from Zurb.
- Sass compilation and prefixing
- JavaScript concatenation
- Built-in BrowserSync server
- CSS and JavaScript minimizing (optional)
- Image compression

## Local Development Installation

To use this theme as a basis for developing your own Foundation-based theme, your computer needs:

- [NodeJS](https://nodejs.org/en/) (0.12 or greater) for installing/using [gulp](http://gulpjs.com/) and [bower](http://bower.io/).
- [Git](https://git-scm.com/)

To get started, go to this folder in your command line, and install the needed dependencies:

```npm install```

```bower install```

Once node and bower have completed installing the dependencies, you can run two commands:

- Run `npm start` to run Gulp tasks for compiling files and watching for changes to `.scss` files, `.js` files, `.html` and `.hbs` files in the src directory. These files will be compiled into mirrored directories within the dist directory. The static prototype that is generated is viewable at:

```
http://localhost:8000
```

Every time changes are made to any of the files in the src/assets, src/layouts, or src/styleguide directory that page will update automatically through BrowserSync.

The `*.libraries.yml` file for this theme is set up to use the compiled CSS and js within dist/assets. By default the CSS and js will include source maps, so prior to using this theme in a production environment run:

 ```npm run build```

To recompile all files *without* source maps.

## Workflow

In src/assets/scss there is a `_settings.scss` file, and `app.scss` file, which are used to define which components from the Foundation framework you'd like to use. Consult the [Foundation sites docs](http://foundation.zurb.com/sites/docs/) for information about the various components and settings.

There are also some starter partials included within src/assets/scss/components to help you get started with custom styling on top of Foundation. All of these files are imported into the `_init.scss` file, which is imported at the bottom of the `app.scss` file.

If you need to customize which js files are included from the Foundation framework the simplest way to do so is by commenting out the unneeded js files listed under `javascript:` in the config.yml file.

## Known Issue: Slowness with Drupal Cache Refresh

If you experience slowness with Drupal cache refreshes in your local development environment you may need to move the `node_modules` directory outside of the Drupal installation, and create a sym link to that directory. See [https://www.drupal.org/node/2329453](https://www.drupal.org/node/2329453).

**Note:** This theme is meant to be used in a typical git workflow, so if you are manually moving it into a production environment **DO NOT** include the `node_modules`, or `bower_components` directory.
