# gulp forward references

## gulpfile.js (before)

```js
var gulp = require('gulp');

gulp.task('default', ['fwd-ref']);

gulp.task('fwd-ref', function(cb){
  cb();
});
```

## gulpfile.js (after)

```js
var gulp = require('gulp');

gulp.task('fwd-ref', function(cb){
  cb();
});

gulp.task('default', gulp.parallel('fwd-ref'));
```

## gulpfile.js (can't fix ordering)

```js
var gulp = require('gulp');

var FwdRefRegistry = require('undertaker-forward-reference');

gulp.registry(new FwdRefRegistry());

gulp.task('default', gulp.parallel('fwd-ref'));

gulp.task('fwd-ref', function(cb){
  cb();
});
```
