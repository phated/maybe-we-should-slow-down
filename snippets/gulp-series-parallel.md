# gulp series/parallel

## gulpfile.js (before)

```js
var gulp = require('gulp');

gulp.task('clean', function(cb){
  cb();
});

gulp.task('js', ['clean'], function(cb){
  cb();
});

gulp.task('css', ['js'], function(cb){
  cb();
});

gulp.task('default', ['clean', 'js', 'css']);
```
__or__
```js
var gulp = require('gulp');
var runSequence = require('run-sequence');

gulp.task('clean', function(cb){
  cb();
});

gulp.task('js', function(cb){
  cb();
});

gulp.task('css', function(cb){
  cb();
});

gulp.task('default', function(cb){
  runSequence('clean', 'js', 'css', cb);
});
```

## gulpfile.js (after)

```js
var gulp = require('gulp');

gulp.task('clean', function(cb){
  cb();
});

gulp.task('js', function(cb){
  cb();
});

gulp.task('css', function(cb){
  cb();
});

gulp.task('default', gulp.series(
  'clean',
  'js',
  'css'
));
```
__and parallel (function composition)__
```js
var gulp = require('gulp');

gulp.task('clean', function(cb){
  cb();
});

gulp.task('js', function(cb){
  cb();
});

gulp.task('css', function(cb){
  cb();
});

gulp.task('default', gulp.series(
  'clean',
  gulp.parallel('js', 'css')
));
```
