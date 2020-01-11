# React-demos
a collection of simple demos of React.js

## 如何使用
1. 首先git clone 到本地
   - https://github.com/luckyMuChen/React-demos.git

2. React-demos目录下build文件是用来解析reat语法代码，让浏览器识别，每一个demo中直接 `<script>`标签中引用即可
   - react.development.js 是React核心库  
   - react-dom.development.js 是操作DOM的React库
   - babel.min.js ES6转ES5  JSX转JS

---
## HTML模板
```html
<!DOCTYPE html>
<html lang="zh">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <meta http-equiv="X-UA-Compatible" content="ie=edge" />
  <title>React-demo</title>
  <script type="text/javascript" src="../build/react.development.js"></script>
  <script type="text/javascript" src="../build/react-dom.development.js"></script>
  <script type="text/javascript" src="../build/babel.min.js"></script>
</head>

<body>
  <div id="demo"></div>
  <script type="text/babel">

  // ** Our code goes here! **
  </script>
</body>

</html>
```
**注意**：
```html
  <!-- 先引入react，再引入react-dom，它们的顺序不可以调换 -->
  <!-- react-dom是依赖于react运行的，所以react-dom必须放在react的下面，放在上面会报错，提示找不到react -->
  <script type="text/javascript" src="../build/react.development.js"></script>
  <script type="text/javascript" src="../build/react-dom.development.js"></script>
  <!-- 引入babel将jsx语法转换成浏览器识别的语法 -->
  <script type="text/javascript" src="../build/babel.min.js"></script>
```
---

## Demo01：Hello World
[demo01](https://github.com/luckyMuChen/React-demos/tree/master/demo01)/[source](https://github.com/luckyMuChen/React-demos/blob/master/demo01/index.html)

- React中的模板语法称为JSX。JSX允许将HTML标签直接放入JavaScript代码。ReactDOM.render()是将JSX转换为HTML，并将其呈现到指定的DOM节点的方法。
- 核心代码
  ```js
  <body>
    <div id="demo"></div>
    <script type="text/babel">
      // 1.创建虚拟DOM对象
      const h1 = <h1>Hello,World</h1>
      // 2.将虚拟DOM对象渲染到页面指定容器中
      ReactDOM.render(h1, document.getElementById('demo'))
    </script>
  </body>
  ```
- 注解： 
  - JSX语法:
    ```js
    ReactDOM.render(<h1>Hello World</h1>,document.getElementById('demo'))
    ```
  - 创建一个虚拟DOM
    ```js
    const h1=<h1>Hello World2</h1>
    ```
  - 渲染虚拟DOM到页面中的指定的容器对象中
    ```js
     ReactDOM.render(h1,document.getElementById('demo'))
    ```
- 注意：
1. 问题: script标签中的`type="text/javascript" `会报错`:Uncaught SyntaxError: Unexpected token <`
   - 解决: 修改script标签中的`type="text/babel" `
2. 虚拟DOM对象中的属性很少---------可以查看该对象是不是虚拟对象
   - `console.dir(h1)`
3. 真实DOM对象中的属性很多---------可以查看该对象是不是真实DOM对象
   - `console.dir(document.getElementById('demo'))`