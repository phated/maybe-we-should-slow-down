## Private APIs - Symbols

## conferences.js (before)
```js
var _ = require('lodash');

class Conferences {
    constructor(confs){
        this._data = confs;
        this._page = 0;
        this._query = null;
    }
    find(filter){
        this._page = 0;
        this._query = filter;
        return this.findNext()
    }
    findNext(){
        var result = _.where(this._data, this._query);
        return this._paging(result);
    }
    _paging(data){
        var currentPage = this._page;
        var nextPage = currentPage + 1;
        this._page = nextPage;
        return data.slice(currentPage, nextPage);
    }
}

module.exports = Conferences;
```

## conferences.js (after)
```js
var _ = require('lodash');

var data = Symbol('data');
var page = Symbol('page');
var query = Symbol('query');
var paging = Symbol('paging');

class Conferences {
    constructor(confs){
        this[data] = confs;
        this[page] = 0;
        this[query] = null;
    }
    find(filter){
        this[page] = 0;
        this[query] = filter;
        return this.findNext()
    }
    findNext(){
        var result = _.where(this[data], this[query]);
        return this[paging](result);
    }
    [paging](data){
        var currentPage = this[page];
        var nextPage = currentPage + 1;
        this[page] = nextPage;
        return data.slice(currentPage, nextPage);
    }
}

module.exports = Conferences;
```

## index.js
```js
var Conferences = require('./conferences');

var data = [
  { name: 'Thunder Plains', category: 'JavaScript', month: 'November' },
  { name: 'JSConf', category: 'JavaScript', month: 'December' }
];

var confs = new Conferences(data);

confs.find({ category: 'JavaScript' });
// [{ name: 'Thunder Plains', category: 'JavaScript', month: 'November' }]

confs.findNext();
// [{ name: 'JSConf', category: 'JavaScript', month: 'December' }]
```

