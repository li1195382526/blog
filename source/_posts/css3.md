###### 1.文本阴影

```css
text-shadow
```

###### 2.背景属性
<!-- more -->

```css
1.background-origin 背景原点
		属性值 padding-bx背景图像填充框的相对位置
					border-box 背景图像框的相对位置
					content-box 背景图像的相对位置的内容框
2.background-clip背景裁切
		属性值 padding-bx
					border-box
					content-box
3.background-size背景尺寸
		属性值 
		background-size : contain | cover | 100px 100px | 50% 100%;
		background-size：contain; // 缩⼩图⽚来适应元素的尺⼨（保持像素的长宽⽐）；
    background-size ：cover; // 扩展图⽚来填满元素（保持像素的长宽⽐）；
    background-size ：100px 100px; // 调整图⽚到指定⼤⼩；
    background-size ：50% 100%; // 调整图⽚到指定⼤⼩，百分⽐相对于包含元素的尺⼨。
4.background:url() no-repeat;
```

###### 3.颜色特性

```css
1.rgba
2.hsl
```

###### 4.边框属性

```css
1.border-color
2.border-image:url() 25 25 25 25 repeat;
 	border-image 属性是简写属性，用于设置一下属性
  border-image-source 边框图片路径
  border-image-slice 图片边框向内偏移
  border-image-repeat 图像边框是否平移（repaet） 铺满（round）拉伸（stretch）
  border-image-outset 边框图片路径
3.border-radius
4.box-shadow:10px 10px 5px 10px #888888 inset
						水平  垂直 模糊距离 阴影大小

```

###### 5.css3弹性盒子

```css
1.display:flex;
2.flex-direction:中轴排列方式
	row 默认一行排列
	row-reverse  反转 横向排列
	column	纵向排列
	column-reverse 反转纵向排列
3.justify-content；主轴对齐方式
	flex-start默认顶端对齐
	flex-end 末端对齐
	spece-between
	spece-around
4.align-items 侧轴对齐方式
	flex-start
	flex-end
	center
	baseline 和start同效果
5.flex-wrap 控制flex容器是单行还是多行
	nowrap 单行
	wrap 多行
	wrap-reverse 反转wrap排列
6.align-content 行与行之间的对齐方式
	flex-statr没有行间距
	flex-end底对齐没有行间距
	space-between两端对齐中间自动分配
	space-around 自动分配距离
7.align-self
	auto
	stretch
	center
	flex-end
```

