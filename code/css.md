## 表单元素

#### input
  默认元素的对齐方式是baseline

#### 小程序蒙版滑动，页面也会一起滑动

      1. 解决方法：给整个view或body一个overflow
      2. 给最外层一个position: fixed; top: 0; right: 0; bottom: 0; left: 0;

#### 小程序图片闪拉长的问题

      1. 给图片一个固定高度

#### css样式总结

      1. 在使用white-space: nowrap时，父级一定要加上overflow: hidden;要不有可能横向滑动