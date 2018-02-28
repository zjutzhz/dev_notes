# ES5
## 1. NodeList to Array
```javascript
var list = document.querySelectorAll("ul")
// method 1
var listArray = Array.prototype.slice.call(list)
// method 2
var listArray2 = [].slice.call(list)
```

## 2. get keys of dictionary
```javascript
var a = {"name": "hz"}
var keyArray = Object.keys(a)
```
