# gulp descriptions API

```js
'use strict';

var gulp = require('gulp');

function hello(cb){ ... }
hello.description = 'This is';

function thunder(cb){ ... }
thunder.description = 'an example';

function plains(cb){ ... }
plains.description = 'of task descriptions';

gulp.task(hello);
gulp.task(thunder);
gulp.task(plains);
```
