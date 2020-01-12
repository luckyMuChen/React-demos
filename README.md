# React-demos

a collection of simple demos of React.js

## 如何使用

1. 首先 git clone 到本地

   - https://github.com/luckyMuChen/React-demos.git

2. React-demos 目录下 build 文件是用来解析 reat 语法代码，让浏览器识别，每一个 demo 中直接 `<script>`标签中引用即可
   - react.development.js 是 React 核心库
   - react-dom.development.js 是操作 DOM 的 React 库
   - babel.min.js ES6 转 ES5 JSX 转 JS

---

## HTML 模板

```html
<!DOCTYPE html>
<html lang="zh">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <title>React-demo</title>
    <script type="text/javascript" src="../build/react.development.js"></script>
    <script
      type="text/javascript"
      src="../build/react-dom.development.js"
    ></script>
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

## Demo-01：Hello World

[demo01](https://github.com/luckyMuChen/React-demos/tree/master/demo01)/[source](https://github.com/luckyMuChen/React-demos/blob/master/demo01/index.html)

- React 中的模板语法称为 JSX。JSX 允许将 HTML 标签直接放入 JavaScript 代码。ReactDOM.render()是将 JSX 转换为 HTML，并将其呈现到指定的 DOM 节点的方法。
- 核心代码
  ```js
  <body>
    <div id="demo"></div>
    <script type="text/babel">
      // 1.创建虚拟DOM对象 const h1 = <h1>Hello,World</h1>
      // 2.将虚拟DOM对象渲染到页面指定容器中 ReactDOM.render(h1, document.getElementById('demo'))
    </script>
  </body>
  ```
- 注解：
  - JSX 语法:
    ```js
    ReactDOM.render(<h1>Hello World</h1>, document.getElementById('demo'))
    ```
  - 创建一个虚拟 DOM
    ```js
    const h1 = <h1>Hello World2</h1>
    ```
  - 渲染虚拟 DOM 到页面中的指定的容器对象中
    ```js
    ReactDOM.render(h1, document.getElementById('demo'))
    ```
- 注意：

1. 问题: script 标签中的`type="text/javascript"`会报错`:Uncaught SyntaxError: Unexpected token <`
   - 解决: 修改 script 标签中的`type="text/babel"`
2. 虚拟 DOM 对象中的属性很少---------可以查看该对象是不是虚拟对象
   - `console.dir(h1)`
3. 真实 DOM 对象中的属性很多---------可以查看该对象是不是真实 DOM 对象
   - `console.dir(document.getElementById('demo'))`

---

## Demo-02

- 核心代码

  ```html
  <body>
    <div id="test1"></div>
    <div id="test2"></div>
    <div>-------------------------分割线-----------------------</div>
    <div id="test3"></div>
    <div id="test4"></div>
    <script type="text/javascript">
      // 第一种方式：创建虚拟DOM对象
      const h1 = React.createElement(
        'h1',
        { id: 'myTitile', className: 'myClass' },
        'Hello h1标签'
      )
      // 将虚拟DOM对象渲染到页面指定容器中
      ReactDOM.render(h1, document.getElementById('test1'))

      // 用第一种创建方式，在h2标签中创建一个span标签
      const span = React.createElement('span', {}, '第一种方法创建span标签')
      const h2 = React.createElement(
        'h2',
        { id: 'myTitile', className: 'myClass' },
        span,
        span
      )
      // 将虚拟DOM对象渲染到页面指定容器中
      ReactDOM.render(h2, document.getElementById('test2'))
    </script>

    <script type="text/babel">
      // 第二种方式：创建虚拟DOM对象
      const h3 = (
        <h3 id="myTitle2" className="myClass2">
          <span>第二种方法创建span标签</span>
          <span>第二种方法创建span标签</span>
        </h3>
      )
      // 将虚拟DOM对象渲染到页面指定容器中
      ReactDOM.render(h3, document.getElementById('test3'))

      const id = 'myTitle3'
      const className = 'myClass3'
      const content = '我也是第二种方法创建span标签'
      const myH1 = (
        <h1 id={id} className={className}>
          <span>{content}</span>
          <span>我也是第二种方法创建span标签</span>
        </h1>
      )

      ReactDOM.render(myH1, document.getElementById('test4'))
    </script>
  </body>
  ```

-
