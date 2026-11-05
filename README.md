# GIS-poi-demo

一个 WebGIS 练习项目，目标是从零走通「底图 → 图层 → 数据 → 交互 → 部署」这条链路。

## 在线预览

https://crazy-git-hub.github.io/GIS-poi-demo/

## 目前实现

- 高德街道底图（style=8）与卫星影像（style=6）双层叠加，透明度可调
- 基于 OpenLayers 10，支持滚轮缩放、拖拽平移、缩放级别限制
- HTML / CSS / JavaScript 三层分离的页面结构
- GitHub Pages 自动部署，国内网络可直接访问（不依赖代理）

## 怎么运行

用到了本地服务器（后续要 fetch 加载数据文件），不能用 file:// 打开：

    cd D:\GIS-poi-demo
    python -m http.server 8000

然后访问 http://localhost:8000/

## 技术栈

- HTML5 / CSS3（Flexbox + 绝对定位）
- 原生 JavaScript（ES6+）
- OpenLayers 10.11（CDN 引入，无需构建工具）
- 高德瓦片服务（GCJ-02 坐标系）

## 文件说明

| 文件 | 说明 |
|---|---|
| index.html | 地图主页面（站点首页） |
| basics.html | 第一课练习页（HTML/CSS/JS 基础），保留作记录 |
| README.md | 本文件 |

## 踩过的坑

- OpenStreetMap 官方瓦片禁止网页应用调用，返回 403「Access blocked」
- OSM / Esri 在国内需要代理，最终改用高德瓦片（国内直连，但 GCJ-02 有偏移）
- 各家瓦片的 z/x/y 顺序不同：Esri 是 {z}/{y}/{x}，高德是 {z}/{x}/{y}
- file:// 下无法 fetch 本地文件，必须用本地服务器
- CSS 百分比高度需要父元素有确定高度，否则链条断开、容器高度为 0

## 下一步计划

- [x] 接入 OpenLayers，显示底图
- [ ] 加载 GeoJSON 矢量数据（点/线/面）
- [ ] 点击要素弹出属性窗
- [ ] 处理 GCJ-02 与 WGS84 的坐标偏移
- [ ] 框选查询与结果统计
