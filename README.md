```JS
// #1
Object.entries('reversed string').sort((a,b)=>b[0]-a[0]).map(a=>a[1]).join('');

// #2
'reversed string'.split('').reduce((a,c)=>c+a);

// #3
[...'reversed string'].sort(_=>-1).join('');

// #4
[...(function() {
    const str = new String('reversed string');
    str[Symbol.iterator] = function() {
        return {
            value: this,
            index: this.length,
            next: function() {
                return {value: this.value[--this.index], done: typeof this.value[this.index] == 'undefined'}
            },
        }
    }
    return str;
})()].join('')
```
