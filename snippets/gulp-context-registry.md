# Custom Registries - Modify Behavior

## context-registry.js
```js
var DefaultRegistry = require('undertaker-registry');

class ContextRegistry extends DefaultRegistry {
  constructor(context){
    super();
    this.context = context;
  }
  set(name, fn){
    var boundFn = fn.bind(this.context);
    return super.set(name, boundFn);
  }
}

module.exports = ContextRegistry;
```

# gulpfile.babel.js
```js
var gulp = require('gulp');
var ContextRegistry = require('./context-registry');

var context = { thunder: 'plains' };

var registry = new ContextRegistry(context);

gulp.registry(registry);

gulp.task('default', function(cb){
  // this === context
  cb();
});
```
