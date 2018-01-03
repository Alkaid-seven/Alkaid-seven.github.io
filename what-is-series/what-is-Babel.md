## what is babel



babel-standalone 非node环境中使用babel，实时compile JS，应用程序中已经嵌入JS引擎，通过JS拓展应用程序

babel

Babel-register 是一个 require hook，bind 到 node 的 require 上去，自动编译文件

babel-core 需要以编程的方式调用babel的API进行转码

babel-node 是node 的CLI的替代品，是整合babel最简单的方式。不适合在正式的产品环境中使用此方式编译的代码，但是构建脚本是可以的。

babel-cli (command-line interface) 通过命令行使用babel编译文件

运行babel，只是将代码从A放到了B，并没有进行“翻译” （通用编译器，默认什么也不做）



通过 plugins 插件 或者 预设 presets（一组插件） 指示babel应该做什么

.babelrc 文件，告诉babel应该做什么的配置文件



babel-polyfill

babel 只转换语法，不转换API。想要使用新的API就要添加 babel-polyfill

`Polyfill 代码填充 或者 兼容性补丁。在当前环境中模拟性复制尚不存在的原生API代码`



babel-runtime

babel 使用“助手”方法来保持生成代码的整洁性。助手方法有可能特别长并且会被添加到每一个文件的顶部，因此，将所有的助手方法挪到 "运行时runtime"中去









