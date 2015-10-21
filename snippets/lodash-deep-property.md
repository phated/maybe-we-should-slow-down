# lodash get/set methods

```js
var _ = require("lodash")

var confs = {
  thunderplains: {
    date: 'Nov 3rd, 2015'
  },
  jsconf: {
    date: 'Dec 5th, 2015'
  }
};

var date = _.get(confs, 'thunderplains.date');
// date === "Nov 3rd, 2015"

_.set(confs, 'thunderplains.favorite', 'Maybe We Should Slow Down');
// confs.thunderplains.favorite === 'Maybe We Should Slow Down
```
