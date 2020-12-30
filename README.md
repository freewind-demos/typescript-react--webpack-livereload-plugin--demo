TypeScript React "webpack-livereload-plugin" Demo
=================================

虽然我们已经有了webpack-dev-server，可以自动处理live reload甚至可以“局部热更新”，但有时候，我们可能有一些别的需求，
需要提供一种独立的live reload方案。可以使用webpack-livereload-plugin插件。

设置`appendScriptTag: true`后，它会自动在html中插入

```
<script src="http://localhost:35729/livereload.js"></script>
```

由于没有使用webpack-dev-server，所以需要两个命令分别处理：
1. `webpack --watch`监视文件变化并产生新文件，同时`webpack-livereload-plugin`会起作用监听一个端口（如35729）
2. 一个普通的http server来serve生成的index.html

由于webpack生成的index.html中包含了对livereload.js的引用，当webpack重新产生了文件后，浏览器中index.html就可以知道该事件，
触发页面的刷新。

```
npm install
npm run demo
```

It will open page on browser automatically.
