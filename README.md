![GulpKit Logo](http://i.imgur.com/3f5iz63.png)

Abstraction for front-end automation.

GulpKit aims to match the simplicity of CodeKit with the power of NPM and Gulp packages. In a matter of minutes, you can get setup with a highly configurable gulpfile that compiles your front-end site(s) and watches for changes.

[![Travis](https://img.shields.io/travis/GulpKit/GulpKit.svg?maxAge=120)](https://travis-ci.org/GulpKit/GulpKit)
[![npm](https://img.shields.io/npm/dt/gulpkit.svg)](https://www.npmjs.com/package/gulpkit)
[![npm](https://img.shields.io/npm/v/gulpkit.svg)](https://www.npmjs.com/package/gulpkit)
[![npm](https://img.shields.io/npm/l/gulpkit.svg)](https://raw.githubusercontent.com/GulpKit/GulpKit/master/LICENSE)

## Install

    npm i gulpkit

## Creating a gulpfile

    var GulpKit = require('GulpKit');

    GulpKit(function(kit) {
        // tasks
    });

### Tasks

#### scss

Compile sass files, autoprefix vendor prefixes, combines media queries and concat/minify CSS with sourcemaps.

    kit.scss({
        source: './scss/app.scss',
        output: './css/style.css'
    });

#### js

Combine Javascript files, run JSHint and uglify with sourcemaps.

    kit.js({
        source: './js/main.js',
        output: './build/script.js'
    });

#### browserSync

Browsersync makes developing and testing faster by synchronising code changes and interactions like clicks, scrolls and form inputs across multiple devices.

All output from tasks are added to the list of files that Browsersync will watch and refresh connected browsers on changes.

    kit.browserSync({
        proxy: 'yourapp.local'
    });

## Extending GulpKit

If the options in config aren't enough or you need extra functionality, you can extend GulpKit and make a custom task.

    GulpKit.extend('custom', function(options) {

        return new GulpKit.Task('custom', options, function() {
            // return a gulp stream
        })
        .watch('path/to/watch')
        .ignore('path/to/ignore');

    });

## Credit

* Some tasks built by [Jake Cobley](http://cobe.ly) from [JakeCobley/Kettle](https://github.com/JakeCobley/Kettle)
* - scss
