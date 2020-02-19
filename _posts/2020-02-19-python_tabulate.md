---
layout: post
title:  python-tabulate
categories: 
  - 介绍
tags:
  - 工具
  - python
excerpt:  一个能够打印不同类型表格的python库
comments: true
---

其实在用 pandas 也能获得比较好的一个效果，特别是 pandas 这次 1.0.0 版本增加了 to_markdown 的新功能。

但是这个 tabulate 也是不可或缺的一个库，它能够输出各种类型的表格。

[pypi 链接 ：tabulate](https://pypi.org/project/tabulate/)

### 简单示例

```
from tabulate import tabulate

table = [["Sun",696000,1989100000],["Earth",6371,5973.6],
...          ["Moon",1737,73.5],["Mars",3390,641.85]]
print(tabulate(table))
-----  ------  -------------
Sun    696000     1.9891e+09
Earth    6371  5973.6
Moon     1737    73.5
Mars     3390   641.85
-----  ------  -------------
```

### 函数

```py
tabulate(tabular_data, headers=(), tablefmt='simple', floatfmt=_DEFAULT_FLOATFMT, numalign='decimal', stralign='left', missingval=_DEFAULT_MISSINGVAL, showindex='default', disable_numparse=False, colalign=None)
```

|参数|默认|输入格式|
|-|-|-|
|tabular_data | | tabel 类型的大多都可以，详见 pypi |
|headers| |`实参列表` `firstrow` 或者 `"keys"`|
|showindex| `default` | `None` `True/False` `"always"` 或者指定列表中的某一列 |
|tabelfmt| `simple`| plain/simple/github/latex/... |
|numalign  | `decicmal` |`right`, `center`, `left`, `decimal` (only for numbers), and `None` (to disable alignment) |
|stralign  | `left` |`right`, `center`, `left`, `decimal` (only for numbers), and `None` (to disable alignment) |

### tabel format

不同的格式

*   "plain"      # none
*   "simple"   # the default format
*   "github"   # github_markdown
*   "grid"
*   "fancy_grid"
*   "pipe"     # `pipe_tables` in Pandoc
*   "orgtbl"
*   "jira"
*   "presto"
*   "psql"
*   "rst"
*   "mediawiki"
*   "moinmoin"
*   "youtrack"
*   "html"    # standard HTML
*   "latex"
*   "latex_raw"
*   "latex_booktabs"
*   "textile"


