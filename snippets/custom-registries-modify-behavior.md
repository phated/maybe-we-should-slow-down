# Custom Registries - Modify Behavior

## task-metadata.js
```js
var DefaultRegistry = require('undertaker-registry');

class TaskMetadataRegistry extends DefaultRegistry {

  constructor(metadata){
    super(metadata);
    this.metadata = metadata;
  }

  set(name, fn){
    var task = this._tasks[name] = fn.bind(this.metadata);
    return task;
  }
}

module.exports = TaskMetadataRegistry;
```

# gulpfile.js
```js
var gulp = require('gulp');
var TaskMetadataRegistry = require('./task-metadata');

var sharedMetadata = {
  thunder: 'plains'
};

var registry = new TaskMetadataRegistry(sharedMetadata);

gulp.registry(registry);

gulp.task('default', function(cb){
  // this === sharedMetadata
  cb();
});
```
