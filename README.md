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

## Get unique values in an array

```javascript
function ArrayUnique(array) {
   var u = {}, a = [];
   for(var i = 0, l = array.length; i < l; ++i){
      if(u.hasOwnProperty(array[i])) {
         continue;
      }
      a.push(array[i]);
      u[array[i]] = 1;
   }
   return a;
}
```

### Each loop

```javascript
// for an array
function each(arr, fn) {
  for(var i in arr) {
    fn(i, arr[i]);
  }
}
// for dom element, works like $.each
var elements = document.querySelectorAll(selector);
Array.prototype.forEach.call(elements, function(el, i) {
    // your action
});
```

## Get Object length

```javascript
function ObjectLength(obj) {
  var length = 0, key;
  for (key in obj) {
    if (obj.hasOwnProperty(key)) length++;
  }
  return length;
}
```

## Class

```javascript
// classList is much faster than className as we know, ref: http://t.cn/RAYkuEr
// addClass
function addClass(el, className) {
  if (el.classList)
    el.classList.add(className);
  else
    el.className += ' ' + className;
}
// removeClass
function removeClass(el, className) {
  if (el.classList)
    el.classList.remove(className);
  else
    el.className = el.className.replace(new RegExp('(^|\\b)' + className.split(' ').join('|') + '(\\b|$)', 'gi'), ' ');
}
// toggleClass
function toggleClass(el, className) {
  if (el.classList) {
    el.classList.toggle(className);
  } else {
    var classes = el.className.split(' ');
    var existingIndex = classes.indexOf(className);

    if (existingIndex >= 0)
      classes.splice(existingIndex, 1);
    else
      classes.push(className);

    el.className = classes.join(' ');
  }
}
```

## Trim

```javascript
// works like $.trim(string)
var string = ' ai shi te ru    ';
string.trim(); // print 'ai shi te ru'
```

## Get element offset

```javascript
function getOffset(el) {
  var _x = 0;
  var _y = 0;
  while (el && !isNaN(el.offsetLeft) && !isNaN(el.offsetTop)) {
    _x += el.offsetLeft - el.scrollLeft;
    _y += el.offsetTop - el.scrollTop;
    el = el.offsetParent;
  }
  return {
    top: _y,
    left: _x
  };
}
// example: var offset = getOffset(document.getElementById('yourElId'));
```
