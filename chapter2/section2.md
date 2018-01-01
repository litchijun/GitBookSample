## 图书输出
本章内容讲述如何将编写好的图书输出为我们所需要的格式。目前为止，Gitbook支持如下输出：
静态HTML，可以看作一个静态网站
- PDF格式
- eBook格式
- 单个HTML文件
- JSON格式

我们这里着重说下如何输出静态的HTML和PDF文件。
### 输出为静态网站
你有两种方式输出一个静态网站：
本地预览时自动生成
当你在自己的电脑上编辑好图书之后，你可以使用Gitbook的命令行进行本地预览：
```
$gitbook serve ./图书目录
```
这里会启动一个端口为4000用于预览的服务器：
```
D:\gitbook\mybook>gitbook serve .
Live reload server started on port: 35729
Press CTRL+C to quit ...

info: 7 plugins are installed
info: loading plugin "livereload"... OK
info: loading plugin "highlight"... OK
info: loading plugin "search"... OK
info: loading plugin "lunr"... OK
info: loading plugin "sharing"... OK
info: loading plugin "fontsettings"... OK
info: loading plugin "theme-default"... OK
info: found 8 pages
info: found 7 asset files
info: >> generation finished with success in 1.6s !

Starting server ...
Serving book on http://localhost:4000
```

这里你会发现，你在你的图书项目的目录中多了一个名为_book的文件目录，而这个目录中的文件，即是生成的静态网站内容。

#### 使用build参数生成到指定目录
与直接预览生成的静态网站文件不一样的是，使用这个命令，你可以将内容输入到你所想要的目录中去：
```
D:\gitbook\mybook>mkdir tmp\gitbook

D:\gitbook\mybook>gitbook build --output=tmp\gitbook
info: 7 plugins are installed
info: 6 explicitly listed
info: loading plugin "highlight"... OK
info: loading plugin "search"... OK
info: loading plugin "lunr"... OK
info: loading plugin "sharing"... OK
info: loading plugin "fontsettings"... OK
info: loading plugin "theme-default"... OK
info: found 8 pages
info: found 7 asset files
info: >> generation finished with success in 1.9s !

```
无论哪种方式，你都可以将这个文件打包，然后把你的书发给你的朋友们了！
### 输出PDF
输入为PDF文件，需要先使用NPM安装上gitbook pdf：
```
$npm install gitbook-pdf -g
```
> 笔者在安装这个模块的时候，当下载一个名为phantomjs的包时，出现请求未能响应的情况，这时，你可以到这个应用的网站上去下载:
http://phantomjs.org/  
这个包的安装方法，请看网站上的说明。


然后，使用下面的命令，可生成PDF文件了：
```
$gitbook pdf ./图书目录
```
如果你在图书目录内容，也可以这样做：
```
$gitbook pdf .
```
然后，你会发现你的目录里多了一个名为book.pdf的文件，就是它了！
但是，笔者在测试的时候发现，生成的PDF文件在排版上不是合理，如页面的边距明显过小，如果是图文混排的话，整个版面感觉有些零乱。
