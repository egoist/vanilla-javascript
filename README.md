# vanilla-javascript

## Selector

```javascript
// works like $('#id')
var $  = document.getElementById.bind(document);
// works like $('.class')
var $$ = document.querySelectorAll.bind(document);
```

## Clone object

```javascript
function clone(obj) {
    if(obj === null || typeof(obj) !== 'object')
        return obj;

    var temp = obj.constructor(); 

    for(var key in obj) {
        if(Object.prototype.hasOwnProperty.call(obj, key)) {
            temp[key] = clone(obj[key]);
        }
    }
    return temp;
}
```
