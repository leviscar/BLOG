---
title: Javascript 流程图框架对比
date: 2020-08-08 21:00:37
tags: 可视化
---

## 背景
需要实现一个支持拖拽的流程图页面，同时支持文件管理等，需要考虑对于三大框架的支持性，需要考虑后续可维护性，证书是否商用

## 绘图框架对比
目前主流绘图软件对比

https://www.npmtrends.com/Joint-vs-jsplumb-vs-mxgraph-vs-echarts-vs-gojs-vs-d3-vs-mermaid-vs-chart.js-vs-flowchart.js

### 趋势
{% asset_img trend.png 趋势图%}

### 使用分析
{% asset_img stats.png 使用分析%}

## 绘图框架分类
依照框架程度的封装程度可以分为下列两个等级：
1. 底层绘图框架 如D3.js
2. 中等封装框架 如Gojs，jsplumb，Joint，mxgraph，node-red等

## 详细框架对比
### 底层绘图框架
#### D3.js 开源
[github](https://github.com/d3/d3)   [官网](https://d3js.org/)
D3(Data-Driven Documents) 是一个帮助开发者通过SVG,HTML,Canvas来可视化数据的JS库.相比于常规开箱即用的数据可视化库,D3由于更为底层(类似JQuery)，开发灵活性更高，但是学习成本较大，无法短期内上手，开发成本也很高。
{% asset_img d3.png D3%}

### 中等封装框架
#### mermaid.js 开源
marmaid 是一个用于markdown生成图表的js库，原生不支持拖拽，不符合业务场景
[github](https://github.com/mermaid-js/mermaid) [官网](http://mermaid-js.github.io/mermaid/)

#### GoJS  需付费
[官网](https://gojs.net/latest/index.html)
- GoJS是一个实现交互类可视化图表（比如流程图，树图，关系图，力导图，思维导图等等）的JS库。
- GoJS是一个MVVM模型库，底层基于canvas实现，对于Angular的支持比较好
- GoJS为用户交互提供了许多高级功能，如拖放，删除，复制和粘贴，撤销与重做，文本编辑，工具提示，上下文菜单，自动布局，数据绑定和模型，事务状态和撤销管理，事件处理程序，命令以及用于自定义操作的可扩展工具系统等等。
- 价格比较贵，单应用单域名永久授权就要7千美刀

#### Joint 分为社区版和收费版
[官网](https://www.jointjs.com/)
- Joint基于JQuery+lodash+Backbone技术栈，底层基于html+svg，用JQuery维护dom，用lodash辅助计算以及渲染模版，用Backbone的Model和Events定义实体和暴露接口，并且自己实现了一套SVG渲染引擎。
- 对Backbone比较熟悉的同学使用Joint上手会比较快。Joint自定义节点（使用模版）非常方便，动画相关的功能也很强大。另外，Joint还可以和布局库dagre配合使用，实现自动布局。
- Joint作为rapid的社区版（开源版本）功能并不全面，很多时候要真正应用在项目里需要进行深入的定制。另外，其维护者对github上的issue响应速度很慢，有时候bug report也没有回应。

[Joint 社区版和付费版对比](https://www.jointjs.com/rappid-comparison)


#### jsplumb 分为社区版和收费版
[官网](https://jsplumbtoolkit.com/)
jsPlumb采用的是svg和html混排的做法，把所有节点都是html，所有连线都是单独的svg节点包裹的path元素。这么做的好处是主要是可以兼容低版本浏览器，并且节点可以充分利用css进行定制。缺点也很明显，首先文档结构散乱，很难导出、转换，其次画出来的图总有莫名的违和感，感觉是像素图形和矢量图形生硬地放到了一起，再次，一旦css在js之后加载完成，jsPlumb的图就崩溃了，而jsPlumb的css也是有侵入性的。



价格也比较贵,社区版的功能比较少
{% asset_img jsplumb_price.png D3%}

#### mxGraph 开源
这个商业产品是上述提到的可视化建模产品里最强大的一个。从05年立项至今，这个库开发时间已有十年。而它的前身JGraph立项时间更早，是2000年。虽然开发模式落后（还是绑定全局变量的方式）、体积庞大，但mxGraph的设计、功能、文档各个方面都难以挑剔。前端可视化建模的标杆作品[draw.io](http://draw.io/)以及中文作图社区[ProcessOn](https://www.processon.com/)都是基于这个库的。基本上目前mxGraph能做到的，就是前端可视化建模能做到的。
[github]() [官网](https://jgraph.github.io/mxgraph/)
[mxGraph 入门实例教程](https://segmentfault.com/a/1190000018510996)
[记一次绘图框架技术选型 - jsPlumb VS mxGraph](https://yejinzhan.gitee.io/2019/03/21/%E8%AE%B0%E4%B8%80%E6%AC%A1%E7%BB%98%E5%9B%BE%E6%A1%86%E6%9E%B6%E6%8A%80%E6%9C%AF%E9%80%89%E5%9E%8B_jsPlumb_VS_mxGraph/)
[Angular使用](https://itnext.io/how-to-integrate-mxgraph-with-angular-6-18c3a2bb8566) [使用范例](https://github.com/diegogusava/angular-mxgraph)

#### node-red 开源
[github](https://github.com/node-red/node-red)
node-red是IBM公司开发的一个开源的JS绘图库，是一个OpenJS基金会项目。

使用方式，通过iframe的方式嵌入到angular应用中，使用不是很方便

## 参考
1. [12 个评估 JS 库你需要关心的事](https://zhuanlan.zhihu.com/p/45264866)
2. [前端可视化建模技术概览](https://github.com/leungwensen/blog/blob/gh-pages/2015/frontend-visual-modeling.md)
3. [UI/UX Workflow Design Analyzing libs](https://medium.com/thinkspecial/ui-ux-workflow-design-5329edf9ba0b)
