---
title: CDN数据
date: 2021-08-1 14:24:23
tags:
---
# CDN数据
<!-- more -->
```js
1、现在有一个js文件要放在cdn上。 这个js文件的内容如下   ：var CDNqtn= = {"qtn":{"id":'1234'}}
2、在react组件中获取这个对象值
3、export一个方法，传入地址和方法
export function importScript (path, success, error) {   
  var oS = document.createElement('script')
  oS.src = path
  document.getElementsByTagName('head')[0].appendChild(oS)
  oS.onload = function () {
    success && success()
  }

  oS.onerror = function () {
    error && error()
  }
}
4、组件中使用
import {importScript} from 'api/sortAdver'
importScript("https://f.epanel.cn/v2/files/template/qtn22185.js",data=>{
    console.log(CDNqtn)
    //这里的CDNqtn就是，cdn链接中获取到的数据啦
})
```

