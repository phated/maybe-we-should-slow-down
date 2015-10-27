# gulp-sourcemaps

## gulpfile.js (before)
```js
var gulp = require('gulp');
var uglify = require('gulp-uglify');
var sourcemaps = require('gulp-sourcemaps');

gulp.task('js', function(){
  return gulp.src('./src/*.js')
    .pipe(sourcemaps.init())
      // Add transformation tasks to the pipeline here.
      .pipe(uglify())
    .pipe(sourcemaps.write('./'))
    .pipe(gulp.dest('./dist/js/'));
});
```

## gulpfile.js (after)
```js
var gulp = require('gulp');
var uglify = require('gulp-uglify');

gulp.task('js', function(){
  return gulp.src('./src/*.js', { sourcemaps: true })
    .pipe(uglify())
    .pipe(gulp.dest('./dist/js/', { sourcemaps: { path: './' } }));
});
```
