# 前端代码的压缩
前端的js、css、html的压缩不仅会让网页加载更快一些，在移动互联网的今天省流量也成为了一大好处。

google的Closure就是一个JS压缩工具（google暂时好像没有css压缩工具），还有雅虎的[YUI Compressor](http://yui.github.io/yuicompressor/) 它是JS/CSS压缩工具。它们都是用java写的工具，用起来就是一行命令，类似于：

	java -jar yui.jar --type css --charset utf-8 -o dest.css src.css

就酱紫。

但是用起来我总不能每改一次css、js文件就手动执行一般这个命令吧……很麻烦的。

所以有了jetbrains黑科技公司的IDE就方便很多啦。

# Webstorm等系列IDE的File Watchers功能
在settings->File Watchers里设置。如图：

![](http://cyhhao.qiniudn.com/Blog/HtmlCompressor/添加watcher.png)
**File Watchers**是一个可以按照文件类型实时监测工程里的文件变化，并且提供回调接口的功能。比如我可以实时监测CoffeeScript文件变化，并且把它们自动地编译生成js文件。是不是很方便？

![](http://cyhhao.qiniudn.com/Blog/HtmlCompressor/coffee2js.png)

什么都不用担心，直接在html里引用js文件，然后尽情地写你的CoffeeScript吧。

附带一下CoffeeScript的File Watchers的配置方式：

![](http://cyhhao.qiniudn.com/Blog/HtmlCompressor/coffee的配置.png)

那个$FileDir$和$FileName$指的是各种相对路径，具体的你可以点击Insert macro...查看，就不过多说明了（Insert macro...点击之后有详细的样例说明）

YUI Compressor压缩JS/CSS的配置：
![](http://cyhhao.qiniudn.com/Blog/HtmlCompressor/YUI1配置.png)

三个红框的配置分别是：

1. 下载好的jar 的路径
2. $FileName$ -o $FileNameWithoutExtension$.min.js
3. $FileNameWithoutExtension$.min.js

CSS文件监测的设置同理，把js改成css就行。

# HTML压缩
重点来了，WebStorm好像没有直接提供HTML文件压缩的选项，但是有了<custom>的选项我们就可以自己做一个啊。

于是昨天迫于强迫症犯了，css、js都自动压缩了，html一定也要自动压缩！所以网上找了个html压缩的代码，改了改，加了接口自己做了个插件。

github地址：https://github.com/cyhhao/HtmlCompressor

jar就在** out/artifacts/unnamed/unnamed.jar **路径，下载下来直接用就好。

用法就是 

	源文件路径 -o 生成文件路径 

目前还很粗糙啦，只有-o命令……只支持utf-8编码……以后有时间会继续更新更新的嘛~

WebStorm配置方式：
![](http://cyhhao.qiniudn.com/Blog/HtmlCompressor/html压缩配置.png)

三个红框的配置分别是（举一反三啦~）：

1. 下载好的jar 的路径
2. $FileName$ -o $FileNameWithoutExtension$.min.html
3. $FileNameWithoutExtension$.min.html
