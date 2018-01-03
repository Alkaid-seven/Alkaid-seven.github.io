### what is browserify





### what browserify can do



sdf



### how to use browserify



sdf



### how browserify works

sdf









- [browserify](http://browserify.org/)是目前比较流行的模块打包工具之一(另外一个[webpack](http://webpack.github.io/))
- 基于流式(stream)思想设计
- 可以通过command line，也可以通过API来使用
- 仅处理javascript
- 模块化的逆过程，但是推动着模块化的更好发展
- 内置了一些[node core module](https://github.com/substack/browserify-handbook#builtins)
- node模块可以在浏览器端使用，是[同构应用](http://isomorphic.net/)的有力武器








browserfiy的输入内容整体上分为两类：file、transform function。file就是需要打包的文件，transform function用于对输入的file内容进行处理。

b.pipeline是browserify里面的核心对象。通过这个对象，可以对module进行一系列的处理，这个对象具有如下特点：

- 由[labeled-stream-splicer](https://www.npmjs.com/package/labeled-stream-splicer)生成
- 整合了很多transform stream后，生成一个整体transform stream
- 带有label，通过label访问内部具体的transform stream
- write进去的chunk分两种情况：带有file的对象，带有transform function的对象



#### 模块依赖的解析

面对的问题：

- 在模块合并前，首先要做的工作就是找出入口文件(entry file)的依赖以及依赖的依赖，例如在charpter1的demo中，入口文件foo.js仅依赖square.js
- 考虑要对源代码进行转换
- browserify通过[module-deps](https://github.com/substack/module-deps)来解决上述问题



#### 模块的打包

利用[browser-pack](https://www.npmjs.com/package/browser-pack)，将上述的json数据打包合并成一个文件，browser-pack具体做了如下工作:

1. 定义浏览器端可用的require关键词

  2.将json source合并在一起

- source: 是一个map结构，key存在两种情况(默认为内部数字、显示[expose](https://github.com/substack/node-browserify#brequirefile-opts)出来的key)
- source元素分为两部分：源代码(包含的function(require, module, exports) {…})、代码中存在的依赖
- cache是缓存信息，避免再次读取souce
- entry: 是打包代码入口文件的key



相比较webpack，个人更喜欢browserify，webpack给人的感觉是一直在配置、使用plugin，并且代码结构很复杂，里面涉及大量事件，源码不容易阅读。而使用browserify给人感觉是在开发，使用起来也较为灵活，同时browserify的stream设计思路给人更多启发，可以向其他方向(例如css合并)迁移



![browserify_base](/Users/jfliu/Documents/typora/browserify_base.png)


question：

1. 什么是同构应用   一份代码同时在客户端和服务端渲染的JavaScript应用。同构的意义就在于任何一段代码（当然有些特殊代码例外）都能同时跑在客户端与服务器端。 “同构JavaScript”是一个范围 — 它开始只能共享模板，之后管理整个项目的视图层，再到大多数应用的业务逻辑层。事实上JavaScript代码共享在前后端是要取决于你的程序设计，以及它的独特约束。
2. 单页面应用（SPA） SPA 在首次加载页面时就获取了所有必需的资源，或者再按需动态加载并且渲染到页面上。SPA 准许重度的交互设计，因为几乎所有的操作都在客户端执行，保持最低限度地与服务端进行交流。
   1. SPA 需要更多的客户端代码，需要下载数据的体积也更大。这使得手机加载速度很慢，可能会导致一些极端的状况 
   2. 因为单页面应用依赖于 JavaScript 的执行，服务器不会提供它们可能用到的任何 HTML 内容。
   3. web 爬虫很难去索引到这些页面。爬虫就是可以向 web 服务器发送请求，并且将结果分析成原始文本的程序，而不需要像一个浏览器运行 JavaScript 那样解释和执行客户端的内容。
   4. 同构 JavaScript 应用基于 JavaScript 编写，可以在客户端和服务端运行。







阶段1：预编译阶段

> 1.从入口模块开始，分析代码中require函数的调用 
>
> > 由于浏览器端并没有原生的require函数，所以所有require函数都是需要我们自己实现的。因此第一步我们需要知道一个模块的代码中，哪些地方用了require函数，依赖了什么模块。browerify实现的原理是为代码文件生成AST，然后根据AST找到require函数依赖的模块。
>
> 2.生成AST
> 3.根据AST找到每个模块require的模块名
>
> > 生成js描述的AST以及解析AST对象 [代码生成AST](https://github.com/ariya/esprima )  [从AST中提取reqiure](https://github.com/browserify/detective)  [AST生成代码](https://github.com/Constellation/escodegen)
>
> 4.得到每个模块的依赖关系，生成一个依赖字典
>
> 5.包装每个模块（传入依赖字典以及自己实现的export和require函数），生成用于执行的js
>
> > 拥有了上面的依赖字典之后，我们相当于知道了代码中的依赖关系。为了让代码能执行，最后一步就是实现浏览器中并不支持的export和require。因此我们需要对原有的模块代码进行包装，外层会传入自己实现的export和require函数。

阶段2：执行阶段

> 从入口模块开始执行，递归执行所require的模块，得到依赖对象。





[解析browserify工作原理](https://segmentfault.com/a/1190000004128257)

[browserify 运行原理](https://segmentfault.com/a/1190000007555597)

[browserify-handbook](https://github.com/browserify/browserify-handbook)