---
layout: post
title:  echarts map 初探
categories: 
  - 笔记
tags:
  - echarts
  - django
excerpt: echarts 地图使用 一
comments: true
---

## echarts

```js
<script type="text/javascript" src="https://cdn.jsdelivr.net/npm/echarts/map/js/world.js"></script>  # 通过cdn使用地图信息
<div id="main" style="width: 600px;height:400px;"></div>  # 绘在一个600*400的画布上
<script>
var chart = echarts.init(document.getElementById('main'));
chart.setOption({
    series: [{
        type: 'map',
        mapType: 'world'
    }]
});
</script>

```

### 省份的问题

```js
    <div id="demo" style="width: 600px;height:400px;"></div>
    <script type="text/javascript" src="../static/map/js/province/beijing.js"></script>  # 引入北京的地图信息
    <script>
    var chart = echarts.init(document.getElementById('demo'),{renderer:'svg'});
    chart.setOption({
        series: [{
            type: 'map',
            mapType: '北京'    # 省份需写中文字
        }]
    });
    </script>
```

### 问题与提高

1. 这里只是引入地图，还未对每个地图做针对性的优化，例如添加背景色、图例。
2. 也没有将几个省份的地图合起来。
3. 多个图进行联动

## django静态文件

如果要给django添加静态文件，需要在setting中有一下两行，django即可扫描到static文件夹中的文件

```
STATIC_URL = '/static/'   # 访问的地址带static
STATICFILES_DIRS = [os.path.join(BASE_DIR, 'static')]  # 静态文件储存的文件夹地址
```