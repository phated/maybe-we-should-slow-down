# Private APIs - WeakMaps

```js
var options = new WeakMap();

class Conference {
    constructor(opts){
        var defaultedOpts = Object.assign({
            name: '',
            schedule: []
        }, opts)
        options.set(this, defaultedOpts);
    }
    nextTalk(){
        var opts = options.get(this);
        return opts.schedule.shift();
    }
    name(){
        var opts = options.get(this);
        return opts.name;
    }
}

var conf = new Conference({
    name: 'Thunder Plains',
    schedule: [
        {
            title: 'Maybe We Should Slow Down'
        }
    ]
});

conf.name();
// 'Thunder Plains'

conf.nextTalk();
// { title: 'Maybe We Should Slow Down' }
```
