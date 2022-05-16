###### 1.层级选择器

```css
E>F 子选择器
E+F 相邻兄弟选择器
E^F 通用选择器
```

<!-- more -->

###### 2.属性选择器

```css
E[attr] 只使用属性名，但没有确定任何属性值
例如：p[title] {color: red;}
		 img[alt] {border: 5px solid red;}
E[attr:'value']:指定属性名，并指定了属性值
E[attr~:'value']:指定属性名，并指定了属性值,s属性值是一个词列表，并且以空格隔开，词列表中包含了一个value词
E[attr^:'value']:指定属性名，并指定了属性值,属性值以value开头
E[attr$:'value']:指定属性名，并指定了属性值,属性值以value结尾
E[attr*:'value']:指定属性名，并指定了属性值,属性值包含value值
```

###### 3.伪类选择器

```css
1.结构伪类选择器
x:first-child{}
x:last-child{}
x:nth-child(n){}
x:only-child{}
2.目标伪类选择器
E:target
3.UI元素状态伪类选择器（用于表单）
E:entabled
E:disabled
E:checked
E::selection
4.否定伪类选择器
E:not(s)
例如：li:nth-child(odd){}
li:not(:nth-child(odd)){}
5.动态伪类选择器
E:link 链接伪类选择器
E:visited
E:active
E:hover
E:focus
例如：input[type='checkout']:checked+label:after{
  left:70px;
}

```
