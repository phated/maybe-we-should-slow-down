# Custom Registries - Sharing Tasks

## shared-tasks.js
```js
var DefaultRegistry = require('undertaker-registry');

class SharedTasksRegistry extends DefaultRegistry {
  init(gulp){
    gulp.task('js', function(cb){ ... });
    gulp.task('css', function(cb){ ... });
    gulp.task('clean', function(cb){ ... });
  }
}

module.exports = SharedTasksRegistry;
```

## gulpfile.babel.js
```js
var gulp = require('gulp');
var SharedTasksRegistry = require('./shared-tasks.js');

var registry = new SharedTasksRegistry();

gulp.registry(registry);

gulp.task('default', gulp.series('clean', 'css', 'js'));

```
