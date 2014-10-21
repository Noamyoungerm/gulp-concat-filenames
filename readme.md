[![Build Status](https://travis-ci.org/the-simian/gulp-concat-filenames.svg?branch=master)](https://travis-ci.org/the-simian/gulp-concat-filenames) [![Coverage Status](https://coveralls.io/repos/the-simian/gulp-concat-filenames/badge.png?branch=coveralls)](https://coveralls.io/r/the-simian/gulp-concat-filenames?branch=coveralls)




# Information

|              |                                                                                                               |
|--------------|---------------------------------------------------------------------------------------------------------------|
| Package      | gulp-concat-filenames                                                                                         |
| Description  | Similar to concat, but creates a list of names in the output file, rather than all the contents being merged. |
| Node Version | >= 0.10                                                                                                       |

## Usage


### Basic Usage, No options.
```js
var concatFilenames = require('gulp-concat-filenames');

var concatFilenamesOptions = {

};

function fileManifest(){
  gulp
      .src('./lib/**/*.*')
      .pipe(concatFilenames('manifest.txt', concatFilenamesOptions))
      .pipe(gulp.dest('./output/'));
}


gulp.task('file-manifest', fileManifest);

```

###Arguments

Gulp concat-filenames takes 2 arguments: `filename` and `options`

####Filename

This first argment is the name of the output file the list fo filenames will be put into. This is required.

#####Options

The second argument is optional, and is an object with the following properties:

- `newline` - The character to use in place of `\n` for a newline. The default value will be `\n`

- `prepend` - Some text to prepend to every entry in the list of filenames

- `append` - Some text to append to every intry in the list of filenames

- `root` - the root folder. Including this argument will return a list of relative paths instead of absolute paths.


Given the file structure:

```
.
+-- somefile.txt
+-- lib
|   +-- one.txt
|   +-- two.txt
+-- gulpfile.js

```



```js
var concatFilenames = require('gulp-concat-filenames');

var concatFilenamesOptions = {
    root: '/lib',
    prepend: '==> ',
    append: ' <=='
};

function fileManifest(){
  gulp
      .src('./lib/**/*.*')
      .pipe(concatFilenames('manifest.txt', concatFilenamesOptions))
      .pipe(gulp.dest('./output/'));
}


gulp.task('file-manifest', fileManifest);
```

running `gulp file-manifest` now produces a file called `manifest.txt` with the contents

```
==> one.txt <==
==> two.txt <==

```








