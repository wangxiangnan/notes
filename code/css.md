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
      2. input , select 文字会自动居中
      3. 查看一个元素的盒模型，要由外向里去看，寻找规律，再去定是使用line-height，padding， margin，or border，只有这样才能搭建一个良好的页面结构

#### 当给盒子为inline-block的问题（因为外部盒子内默认会有一个文字，以此文字的基线进行对齐。）
	问题1：外层盒子底部有间隙
	处理方法： 1. 外层盒子设置font-size: 0。 2. 外层设置line-height: 0, 3. 内层设置vertical-align: 0
	问题2：同样样式的盒子，设置行内块，有文字的盒子会掉下去。
	1. 里面如果有文字，因为默认的垂直对齐是以文字baseline,也就是基线对齐
	解决方法：
		    给每个inline-block盒子设置vertical-align: top

#### 对于以图片为布局大小时，要考虑到兼容小屏幕，更要以底部为基准定位
      1. 使用flex布局时，宽度自适应时，两侧的padding要注意，有可能阻碍自适应