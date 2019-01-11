---
title: ES6-新增数据类型
date: 2019-01-11 13:48:56
tags:
---
## symbol类型

- 全局函数　window.Symbol()
  
- `typeof window.Symbol()` 返回的类型为 "symbol"
  
- 不支持语法：　new Symbol()

- 每个从Symbol()返回的值都是唯一的:<br>
`var a=Symbol(); var b=Symbol()`，a==b不成立 .

- Symbol()可以作为一个对象的属性（key）,这是该数据类型存在的唯一目的。并且由于唯一性，别人读不到这个属性。

- Symbol是一种基本数据类型

## set类型

- Set是一种对象，Set 对象允许你存储任何类型的唯一值，无论是原始值或者是对象引用。
```
let myset = new Set([1,2,3,3,4,5,5,5])
myset //{1,2,3,4,5}
```
- 对原始值或对象的引用可去重，如果不同的对象里面有相同的值则不会被去重。

```
let a={};
let b={};
new Set ([a,b])  //{{...},{...}}
```
- 数组去重
  
```
function uniq(arr){
    Array.from(new Set(arr))
}
```

## map类型

- map对象保存键值对。任何值(对象或者原始值) 都可以作为一个键或一个值。

```
var mymap = new Map();

var keyobj = {}, 
keyFunc = function () {},
keyString = "a string";

//添加key
mymap.set(keyobj,'objvalue');
mymap.set(keyFunc,'value');
mymap.set(keyString,'value');

//读取值
myMap.get(keyString);    
myMap.get(keyobj);       
myMap.get(keyFunc);
```
- myMap.entries(),返回一个新的 Iterator 对象，它按插入顺序包含了Map对象中每个元素的 [key, value] 数组。

```
var myMap = new Map();
myMap.set("0", "foo");
myMap.set(1, "bar");
myMap.set({}, "baz");

var mapIter = myMap.entries();

console.log(mapIter.next().value); // ["0", "foo"]
console.log(mapIter.next().value); // [1, "bar"]
console.log(mapIter.next().value); // [Object, "baz"]
```
- mymap.keys()得到一个新对象，里面包含mymap的所有key
- mymap.values()得到一个新对象，里面包含mymap的所有value