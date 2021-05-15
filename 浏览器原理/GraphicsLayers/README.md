https://groups.google.com/a/chromium.org/g/blink-dev/c/j7YQtj0Yyxs/m/MNWnuLgtBgAJ

从这篇文章中得出，

update Layer tree的过程就是指2个事情：

1.blink渲染引擎层更新过程。即决定哪些Paint Layer要进行合成，收集和清空CompositedLayerMapping，创建和设置GraphicsLayers的属性和几何结构

2.遍历相关的数，包括Paint Layer数和GraphicsLayers树，在布局对象上找出绘制失效问题，并构建绘制属性树。



有人提问为什么update layer tree的时间很长。

https://stackoverflow.com/questions/49283773/what-leverage-can-be-used-to-reduce-updatelayertree-operation-in-blink

解决办法有2个：

1.尽量减少position定位的元素

2.把元素设置为display:none。这样在可视窗口就不会显示，但是又已经在页面中。并且不会在updateLayerTree的过程中。



update layer tree为什么长？

https://stackoverflow.com/questions/25724126/chrome-devtools-timeline-update-layer-tree-event

有人回答可能是因为基本层失效，导致整个树的layer都重新更新。





2020.02.18
需要把这里的例子执行下，写下文章。
https://juejin.cn/post/6844903476506394638#heading-15

还有这里的：

https://fed.taobao.org/blog/taofed/do71ct/performance-composite/