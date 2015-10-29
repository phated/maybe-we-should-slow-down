# Custom Registries - Sharing Tasks

## tasks-registry.js
```js
var del = require('del');
var uglify = require('gulp-uglify');
var concat = require('gulp-concat');

var DefaultRegistry = require('undertaker-registry');

class TasksRegistry extends DefaultRegistry {
  init(gulp){
    gulp.task('js', function(cb){
      return gulp.src('src/*.js')
        .pipe(uglify())
        .pipe(gulp.dest('dist/'));
    });
    gulp.task('css', function(cb){
      return gulp.src('src/*.css')
        .pipe(concat())
        .pipe(gulp.dest('dist/'));
    });
    gulp.task('clean', function(cb){
      return del('dist/');
    });
  }
}

module.exports = TasksRegistry;
```

## gulpfile.babel.js
```js
var gulp = require('gulp');
var TasksRegistry = require('./tasks-registry.js');

var registry = new TasksRegistry();

gulp.registry(registry);

gulp.task('default', gulp.series(
  'clean',
  'css',
  'js'
));
```
