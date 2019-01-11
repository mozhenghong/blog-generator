---
title: ES6-模块
date: 2019-01-11 11:35:56
tags:
---
## import

- import语句用于导入由另一个模块导出的绑定。
- 在浏览器中， import语句只能在声明了`type="module"`的script的标签中使用。
  
#### 导入整个模块的内容

`import * as name from './1.js'`
- 导入1.js中导出的所有模块，并且命名为name 
- 可以用name调用导入的变量及函数，例如导入的模块包含一个doAllTheAmazingThings()，则可以用`name.doAllTheAmazingThings()`来调用。

#### 导入单个导出

`import {myExport} from './1.js'`

#### 导入多个导出

`import {foo, bar} from './1.js'`

#### 重命名导出

`import {
  reallyReallyLongModuleMemberName as shortName, 
  anotherLongModuleName as short
} from './1.js'`

#### 导入默认值

`import myDefault from './1.js'`
- mydefault不一定要与`export default`中的命名一样，可以随意命名。

#### 仅为副作用而导入一个模块

`import './1.js'`
- 运行1.js模块中的全局代码, 但实际上不导入任何值。函数由于没有被调用所以不会执行。

## export

```
//1.js
function cube(x) {
  return x * x * x;
}

const foo = Math.PI + Math.SQRT2;

export { cube,foo };

//main.js

import { cube, foo } from './1.js';
console.log(cube(3)); // 27
console.log(foo);    // 4.555806215962888
```

## export default

```
//1.js
export default function cube(x) {
  return x * x * x;
}

//main.js
import fn from './1.js'
fn(3) //27
```
- 不能使用var，let或const用于导出默认值export default。