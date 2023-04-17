---
title: Vue 自定义指令
date: 2023-04-17 14:24:23
tags:
---

```vue
全局自定义指令
私有自定义指令
```
<!-- more -->
```vue
全局
Vue.directive('auth',{
        //当被绑定的元素插入DOM中时执行
        inserted:function(el){
            //使元素自动获得焦点
            el.focus();
        }
    })
v-auth
```

```vue
局部
var demo = new Vue({
         el: '#element',
         data:{
            border:'1px solid green'
         },
         directives:{
            addBorder:{
                inserted:function(el,binding){
                    el.style.border=binding.value;
                }
            }
         }
     })
驼峰 写法 v-add-border
```

```vue
钩子函数	说明
bind	只能调用一次，在指令第一次绑定到元素上时调用，用这个钩子函数可以定义一个在绑定时执行一次的初始化设置
inserted	被绑定元素插入父元素时调用
update	指令在bind之后立即以初始值为参数进行第一次调用，之后每次当绑定值发生变化之后时调用，接收的参数为新值和旧值
componentUpdated	指令所在组件及其子组件更新时调用
unbind	只调用一次，指令从元素上解绑时调用
```

