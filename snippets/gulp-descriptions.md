# gulp descriptions API

```js
'use strict';

var gulp = require('gulp');
var uglify = require('gulp-uglify');
var concat = require('gulp-concat');

function js(cb){
  return gulp.src('src/*.js')
    .pipe(uglify())
    .pipe(gulp.dest('dist/'));
}
js.description = 'Bundles the JavaScript.';

function css(cb){
  return gulp.src('src/*.css')
    .pipe(concat())
    .pipe(gulp.dest('dist/'));
}
css.description = 'Builds the CSS files.';

gulp.task(js);
gulp.task(css);
```
