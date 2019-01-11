---
title: ES6-迭代
date: 2019-01-11 14:25:26
tags:
---
## 迭代器

- 迭代器是一个对象，它提供了一个next() 方法，用来返回序列中的下一项。这个方法返回包含两个属性：done和 value。
迭代器对象一旦被创建，就可以反复调用next()。

```
function makeIterator(array){
    var nextIndex = 0;
    return {
       next: function(){
           return nextIndex < array.length ?
               {value: array[nextIndex++], done: false} :
               {done: true};
       }
    };
}
-----------------------------------------
//一旦初始化，next()方法可以用来依次访问对象中的键值：

var it = makeIterator(['yo', 'ya']);
console.log(it.next().value); // 'yo'
console.log(it.next().value); // 'ya'
console.log(it.next().done);  // true
```

## 生成器

- 如果使用function*语法,可以得到生成器

```
function* idMaker() {
  var index = 0;
  while(true)
    yield index++;
}

var gen = idMaker();

console.log(gen.next().value); // 0
console.log(gen.next().value); // 1
console.log(gen.next().value); // 2
// ...
```

## 自定义迭代对象

```
var myIterable = {};
myIterable[Symbol.iterator] = function* () {
    yield 1;
    yield 2;
    yield 3;
};

for (let value of myIterable) { 
    console.log(value); 
}
// 1
// 2
// 3

```
## 三种遍历
- `for(let i=0;i<array.length; i++){}`

- `for(let key in array){}`

- `for(let item of array){}`  ，item是value,不是key.<br>
for ...of 对数组可以，对一般的对象不可以。