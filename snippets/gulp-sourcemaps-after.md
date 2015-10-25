# gulp-sourcemaps after

```js
var gulp = require('gulp');
var uglify = require('gulp-uglify');

gulp.task('js', function(){
  return gulp.src('./src/*.js', { sourcemaps: true })
    .pipe(uglify())
    .pipe(gulp.dest('./dist/js/', { sourcemaps: { path: './' } }));
});
```
