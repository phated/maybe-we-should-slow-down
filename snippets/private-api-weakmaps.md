# Private APIs - WeakMaps

## conferences.js
```js
var _ = require('lodash');

var data = new WeakMap();

class Conferences {
    constructor(confs){
        data.set(this, confs);
    }
    find(filter){
        return _.where(data.get(this), filter);
    }
}
```

## index.js
```js
var data = [
  {
    name: 'Thunder Plains',
    category: 'JavaScript',
    month: 'November'
  },
  {
    name: 'JSConf',
    category: 'JavaScript',
    month: 'December'
  }
];

var confs = new Conferences(data);

confs.find({ month: 'November' });
// { name: 'Thunder Plains', category: 'JavaScript', month: 'November' }

confs.find({ category: 'JavaScript' });
// { name: 'Thunder Plains', category: 'JavaScript', month: 'November' },
// { name: 'JSConf', category: 'JavaScript', month: 'December' }
```
