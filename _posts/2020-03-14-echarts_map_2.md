---
layout: post
title:  echarts map 二（geoJson）
categories: 
  - 笔记
tags:
  - echarts
excerpt:  地图数据整理
comments: true
---

json 中的 coordinates 由一个个的点构成，描绘出了地图中的点、边框等。

## geoJson 数据下载

我们可以通过几个网站获取：

1.  [DataV Geo](http://datav.aliyun.com/tools/atlas/#&lat=33.521903996156105&lng=104.29849999999999&zoom=4)
2.  [geojson.io](http://geojson.io/)
3. [chinaMapJsonData](https://github.com/wenccro/chinaMapJsonData)
4. echarts 自带的世界、中国及省份数据

第一个是阿里的，输入想要的省市直接下载数据；第二个可玩性更高，可以自己描边绘制地图；第三个是网友整理好的数据，有全国省市县的 json 数据。

## 自己制作

上面的几个可以说是数据源，有些时候我们有特许的需求，那就需要直接自己做一个 geojson 文件出来。


```json
{
"type": "FeatureCollection",
  "features": [
        {"type":"Feature",
        "properties":{},
        "geometry":{
            "type":"xxxx",
            "coordinates":[105.380859375,31.57853542647338]
            }
        }
    ]
}
```

type 有以下几种：
- 点要素Point
- 多点要素MultiPoint
- 线要素LineString
- MultiLineString
- 多边形Polygon
- 多多边形MultiPolygon
- GeometryCollection

理解了 geojson 的数据格式之后，结合之前的 geojson 数据我们就可以制作任意想要的地图啦。

参考：
- [安利一个非常好用的 echarts geojson 生成器](https://juejin.im/post/5c99bd9be51d454e2b272d2e)
- [GEOJSON标准格式学习
](https://www.jianshu.com/p/852d7ad081b3)
- [GeoJSON格式规范说明](https://www.oschina.net/translate/geojson-spec)