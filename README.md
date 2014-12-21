[gulp](https://github.com/gulpjs/gulp)-chokidar
=============

Awesome Gulp Watcher and glob wrapper of [chokidar](https://github.com/paulmillr/chokidar).

## Installation

Run `npm install gulp-chokidar`.

## Usage

For using gulp tasks you need to pass `gulp` instance

```js
var gulp = require('gulp'),
    watch = require('gulp-chokidar')(gulp);

gulp.task('hello-css');

gulp.task('default', function () {
    watch('src/css/**/*.css', { root: 'src/css' }, 'hello-css');
});
```

Or you may use watcher without gulp

```js
var watch = require('gulp-chokidar');

watch('src/css/**/*.css', { root: 'src/css' }, function () {
	console.log('update something);
});

```

## API

### watch(globs, [options, task])

Creates watcher that will spy on files that were matched by `globs` which can be a
[`node-globule`](https://github.com/cowboy/node-globule) string or array of strings.

#### task

This task is called, when some events is happens on file-system.
If gulp instance passed with require `task` can be function, task string or task array.

#### Options

#### options.root
Type: `String`
Default: `.`

Directory that will be watching. Recommended to specify.

#### options.ready
Type: `Boolean`
Default: false

Run task on start watching

### Events

 * `all` — any event.
 * `ready` — emits on watcher ready.
 * `add` — when new file was created.
 * `change` — when file was changed.
 * `delete` — when file was deleted`.
 * `error` — when something happened inside callback, you will get notified.


```js
require('gulp-chokidar')('src/css/**/*.css')
	.on('change', function () {
		console.log('update something);
	});

```
