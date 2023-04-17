---
title: Eslint
date: 2021-03-1 14:24:23
tags:
---
# Eslint
<!-- more -->
```js
eslint在react中使用的实例
http://react-china.org/t/react-eslint/29150
一.安装引入eslint
1.yarn add -g eslint
2.Yarn add eslint --save-dev（node版本8.10.0）  eslint-plugin-react
3.eslint init(报错的话可以直接新建.eslintrc.js)
webstorm安装eslint
把文件.eslintrc.js引入webstorm
```

![](C:\Users\li\Desktop\1572319991(1).png)

```js
package配置项 
"scripts": {
    "precommit": "lint-staged",
    "lint": "eslint --ext .js --ext .jsx app", 
    "format": "onchange 'app/**/*.js' -- prettier --write {{changed}}",
    "prettify": "prettier --write --no-semi --jsx-bracket-same-line --single-quote --no-bracket-spacing ./app/**/*.js"
  },
      //precommit是提交代码时的检测
  "pre-commit": [
    "lint"
  ],
   "lint-staged": {
    "*.js": [
    "prettier --write --no-semi --jsx-bracket-same-line --single-quote --no-bracket-spacing ./app/**/*.js",
      "git add"
    ]
  },
 需要安装的插件下载
"babel-eslint": "^10.0.1",	
"eslint": "^5.11.1",
"eslint-config-airbnb": "^17.1.0",
"eslint-plugin-import": "^2.14.0",
"eslint-plugin-jsx-a11y": "^6.1.2",
"eslint-config-prettier": "^6.0.0",
"eslint-plugin-prettier": "^3.1.0",
"eslint-plugin-react": "^7.12.2",
"pre-commit": "^1.2.2",
"prettier": "^1.18.2",
```

```js
.eslintrc.js 文件配置项
module.exports = {
	"env": {
		"browser": true,
		"es6": true
	},
	//"extends": "eslint:recommended",
    "extends": ["airbnb","prettier"],//使用扩展库
	"globals": {
		"Atomics": "readonly",
		"SharedArrayBuffer": "readonly"
	},
	"parserOptions": {
		"ecmaFeatures": {
			"jsx": true
		},
		"ecmaVersion": 2018,
		"sourceType": "module"
	},
    parser: "babel-eslint",
	"plugins": [
		"react",
        "prettier"
	],
	"rules": {
	/*	"indent": [
			"error",
			"tab"
		],*/
        //"prettier/prettier": "error",
		/*"linebreak-style": [
			"error",
			"windows"
		],
		"quotes": [
			"error",
			"double"
		],
		"semi": [
			"error",
			"always"
		]*/
        "react/jsx-filename-extension": [1, { "extensions": [".js", ".jsx"] }],
       /* "import/extensions": [2, "never", { "web.js": "never", "json": "never" }],
        "import/no-extraneous-dependencies": [2, { "devDependencies": true }],
        "import/no-unresolved": [2, { "ignore": ["antd-mobile"] }],*/
        'linebreak-style': ["off", "windows"],
        "no-tabs":"off",
        "quotes": [0, "single"], //单引号
        "no-console": 2, //不禁用console
        "no-debugger": 0, //禁用debugger
        "no-var": 2, //对var警告
        "semi": 0, //不强制使用分号
        "no-irregular-whitespace": 2, //不规则的空白不允许
        "no-trailing-spaces": 2, //一行结束后面有空格就发出警告
        "eol-last": 0, //文件以单一的换行符结束
        //例如
        //import react from 'react'

        //import router from'react-router'
        "no-unused-vars": [2, {"vars": "all", "args": "after-used"}], //不能有声明后未被使用的变量或参数
        "no-underscore-dangle": 2, //标识符不能以_开头或结尾
        "no-alert": 2, //禁止使用alert confirm prompt
        "no-lone-blocks": 2, //禁止不必要的嵌套块
        "no-class-assign": 2, //禁止给类赋值
        "no-cond-assign": 2, //禁止在条件表达式中使用赋值语句
        "no-const-assign": 2, //禁止修改const声明的变量
        "no-delete-var": 2, //不能对var声明的变量使用delete操作符
        //例如:在变量上使用delete运算符可能会导致意外的行为
        // var x;
        //delete x;
        "no-dupe-keys": 2, //在创建对象字面量时不允许键重复
        //例如var foo = {
        // bar: "baz",
        // bar: "qux"
        // };
        "no-duplicate-case": 2, //switch中的case标签不能重复
        "no-dupe-args": 2, //函数参数不能重复
        "no-empty": 2, //块语句中的内容不能为空
        "no-func-assign": 2, //禁止重复的函数声明
        "no-invalid-this": 2, //禁止无效的this，只能用在构造器，类，对象字面量
        "no-redeclare": 2, //禁止重复声明变量
        "no-spaced-func": 2, //函数调用时 函数名与()之间不能有空格
        "no-this-before-super": 2, //在调用super()之前不能使用this或super
        "no-undef": 2, //不能有未定义的变量
        "no-use-before-define": 2, //未定义前不能使用
        "camelcase": 1, //强制驼峰法命名
        "jsx-quotes": [2, "prefer-double"], //强制在JSX属性（jsx-quotes）中一致使用双引号
        "react/display-name": 1, //防止在React组件定义中丢失displayName
        "react/forbid-prop-types": [1, {"forbid": ["any"]}], //禁止某些propTypes
        "react/jsx-boolean-value": 1, //在JSX中强制布尔属性符号
        "react/jsx-closing-bracket-location": 0, //在JSX中验证右括号位置
        "react/jsx-curly-spacing": [2, {"when": "never", "children": true}], //在JSX属性和表达式中加强或禁止大括号内的空格。
        "react/jsx-indent-props": [0, 4], //验证JSX中的props缩进
        "react/jsx-key": 1, //在数组或迭代器中验证JSX具有key属性
        "react/jsx-max-props-per-line": [0, {"maximum": 1}], // 限制JSX中单行上的props的最大数量
        "react/jsx-no-bind": 2, //JSX中不允许使用箭头函数和bind
        "react/jsx-no-duplicate-props":2, //防止在JSX中重复的props
        "react/jsx-no-literals": 0, //防止使用未包装的JSX字符串
        "react/jsx-no-undef": 1, //在JSX中禁止未声明的变量
        "react/jsx-pascal-case": 1, //为用户定义的JSX组件强制使用PascalCase
        "react/jsx-sort-props": 0, //强化props按字母排序
        "react/jsx-uses-react": 1, //防止反应被错误地标记为未使用
        "react/jsx-uses-vars": 1, //防止在JSX中使用的变量被错误地标记为未使用
        "react/no-danger": 1, //防止使用危险的JSX属性
        "react/no-did-mount-set-state": 1, //防止在componentDidMount中使用setState
        "react/no-did-update-set-state": 1, //防止在componentDidUpdate中使用setState
        "react/no-direct-mutation-state": 0, //防止this.state的直接变异
        "react/no-multi-comp": 1, //防止每个文件有多个组件定义
        "react/no-set-state": 0, //防止使用setState
        "react/no-unknown-property": 1, //防止使用未知的DOM属性
        "react/prefer-es6-class": 1, //为React组件强制执行ES5或ES6类
        "react/prop-types": 1, //防止在React组件定义中丢失props验证
        "react/react-in-jsx-scope": 1, //使用JSX时防止丢失React
        "react/self-closing-comp": 1, //防止没有children的组件的额外结束标签
        "react/sort-comp": 1, //强制组件方法顺序
        "no-extra-boolean-cast": 2, //禁止不必要的bool转换
        "react/no-array-index-key": 0, //防止在数组中遍历中使用数组key做索引
        "react/no-deprecated": 2, //不使用弃用的方法
        "react/jsx-equals-spacing": 2, //在JSX属性中强制或禁止等号周围的空格
        "no-unreachable": 2, //不能有无法执行的代码
        "no-mixed-spaces-and-tabs": 2, //禁止混用tab和空格
        "prefer-arrow-callback": 0, //比较喜欢箭头回调
        "arrow-parens": 2, //箭头函数用小括号括起来
        "arrow-spacing": 2 ,//=>的前/后括号
        "prefer-template": "off",
        "jsx-a11y/no-static-element-interactions":[0],//事件报错增加规则
        "jsx-a11y/click-events-have-key-events":0,//ESLint检查强制非Button的onClick 事件需要至少一个键盘事件。
        "import/no-unresolved":0,//验证使用绝对路径
        "react/no-unused-state":2,//避免定义未使用的state
        "comma-dangle": 0, //对象字面量项尾不能有逗号，
        "import/prefer-default-export":0, //export const要有default
        "spaced-comment":0//要求或不允许以空格（制表符或制表符）开头的注释（带空格的注释）
	}
};
```

elint中测试需要修改的地方

```js
1.Component should be written as a pure functioneslint(react/prefer-stateless-function)
给class中的constructor添加state
```

```js
2.Must use destructuring props assignment
错误：this.props.local
修改:const {local} = this.props
```

```js
3. `react-helmet` import should occur before import of `./shared/BlankCopyright`
引入插件位置必须在文件之前
例如：
import Helmet from 'react-helmet'
import BlankCopyright from './shared/BlankCopyright'
```

```js
4.Unable to resolve path to module 'containers/shared/Auth'
因为eslint不识别webpack的路径别名
修改配置项
```

```js
5.propType "showModal" is not required, but has no corresponding defaultProps declaration
proptype“showmodel”不是必需的，但没有相应的defaultprops声明
```

```js
6.Arrow function should not return assignment
错误：ref={input => (this.passInput = input)}
修改：ref={(input) => (this.passInput = input)}
```

```js
7.Prefer default export.
错误:export {modalStyle}
修改:export default modalStyle
```

```js
8.Unexpected string concatenation
ESLint总是推荐用ES6的Template String来拼接字符串，而不能用+号，这个比较烦，毕竟残留代码比较多，所以，禁止掉！
'prefer-template': 'off'
```

```js
9.ESLint: Static HTML elements with event handlers require a role. (jsx-a11y/no-static-element-interactions
由于ESLint检查强制非Button的onClick 事件需要至少一个键盘事件。
键盘事件：onKeyUp, onKeyDown, onKeyPress
错误：<span className="icon" onClick={() => onShow(task.taskType)}>分配</span>                        修改:  <span className="icon" onClick={() => onShow(task.taskType)} onKeyDown={this.handleKeyDown}>分配</span>                                         
```

```js
.eslintrc.js 文件内容
node_modules
dist
```

二.安装引入prettierrc

```js
在webstorm中安装prettier插件(webstorm版本2018以上版本)
```

![](C:\Users\li\Desktop\1572320955(1).png)

![](C:\Users\li\Desktop\1572321021(1).png)

```js
.prettierrc 文件内容(手动添加文件)
{
  "printWidth": 80, //一行的字符数，如果超过会进行换行，默认为80
  "tabWidth": 2, //一个tab代表几个空格数，默认为80
  "useTabs": false, //是否使用tab进行缩进，默认为false，表示用空格进行缩减
  "singleQuote": false, //字符串是否使用单引号，默认为false，使用双引号
  "semi": true, //行位是否使用分号，默认为true
  "trailingComma": "none", //是否使用尾逗号，有三个可选值"<none|es5|all>"
  "bracketSpacing": true, //对象大括号直接是否有空格，默认为true，效果：{ foo: bar }
  "parser": "babylon" //代码的解析引擎，默认为babylon，与babel相同。
}
```

```js
.editorconfig文件配置
# http://editorconfig.org

root = true

# 对所有文件生效
[*]
# utf-8编码
charset = utf-8
# 空格形式缩进2空格
indent_style = space
indent_size = 2
# 使用单引号
quote_type = single
# Linux换行符
end_of_line = CRLF
# 结尾插入新行
insert_final_newline = true
# 去除结尾空格
trim_trailing_whitespace = true

# 对后缀名为 md 的文件生效
[*.md]
trim_trailing_whitespace = false

```



















