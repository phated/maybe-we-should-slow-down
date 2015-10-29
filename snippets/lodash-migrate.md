# lodash-migrate

Example taken from [lodash-migrate docs](https://npmjs.com/package/lodash-migrate).

```js
// load the older lodash 
var _ = require('lodash');
// load lodash-migrate after 
require('lodash-migrate');
 
// later when using API not supported by the latest lodash release 
_.first([1, 2, 3], 2);
// => logs: 
// lodash-migrate: _.first([ 1, 2, 3 ], 2) 
//   v2.4.1 => [ 1, 2 ] 
//   v3.0.0 => 1 
```
