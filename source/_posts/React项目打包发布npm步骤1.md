---
title: React项目打包发布npm步骤
date: 2023-04-1 14:24:23
tags:
---
# React项目打包发布npm步骤
<!-- more -->
```json
React项目打包发布npm步骤
1.注册 登录npm   网址：https://www.npmjs.com（http://39.97.165.254:1234/）
2.创建项目，进入项目进行登录：npm login
3.本地初始化项目以及命名，版本：npm init
4.仓库指向地址：npm config set registry https://registry.npmjs.org/
指向公司自己搭建的地址：npm config set registry http://39.97.32.22:1234/（测试）npm config set registry http://39.97.165.254:1234/（生产）
5.发布：npm publish（要进行邮箱验证才可以发布成功）
6.在项目中npm install 项目名称

验证包是否可以引入
1.npm run build 打包组件
2.Npm link 把打包之后的组件引入global node_modules
3.在其他项目中引用 npm link 项目名称，进行验证是否符合预期

4.Index.js文件写法
import EndPage from './app/containers/EndPage'

module.exports = {
    EndPage
}
6.在项目中import EndPage from EndPage
修改你项目主目录下的package.json文件在文件添加一个程序的入口配置 如图：还有记得修改private 为 false（取消私有）
主文件入口：“main”：“dist/app.js”
https://blog.csdn.net/qq_41387882/article/details/82775705

设置仓库地址为npm官方仓库地址(国内大部分都使用阿里淘宝镜像，如果没改publish会失败) npm config set registry https://registry.npmjs.org/
7.仓库指向地址：npm config set registry https://registry.npmjs.org/

[root@node3 ~]# npm config set proxy null 清空指向
[root@node3 ~]# npm config set registry http://39.97.32.22:1234/ 指向
http://39.97.165.254:1234/


output: {
    path: path.join(__dirname, '../lib'),
    filename: 'index.js',
    libraryTarget: 'umd'  
    //发布组件专用,必须配置libraryTarget: 'umd'，umd为兼容模式
}



是用别人的npm库
https://blog.csdn.net/w13707470416/article/details/85246909
```

