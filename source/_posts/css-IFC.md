---
title: css-IFC
date: 2018-10-31 11:10:48
tags:
---
inline formatting content

1. font-size:em-square(就像活字印刷术刻每个字的方形刻板)

2. line-height:实际的占地高度

3. 内敛元素默认baseline对齐，当两个内敛元素的font-family不同时，基线不一样，会导致父元素的高度有变化。

4. img引入图片后，图片下面有空隙：

- vertical-align：middle；（推荐使用，这是vertical-align在内联元素中唯一用途，其余时候都不要用）

- img{display：block；}

5.内联元素之间对不齐，可以用flex/float,不要用vertical-align!

6.内联元素之间有空隙，用flex/float解决