# Private APIs - WeakMaps

## conferences.js (before)
```js
var _ = require('lodash');

class Conferences {
    constructor(confs){
        this._data = confs;
    }
    find(filter){
        return _.where(this._data, filter);
    }
}

module.export = Conferences;
```

## conferences.js (after)
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

module.exports = Conferences;
```

## index.js
```js
var Conferences = require('./conferences');

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
