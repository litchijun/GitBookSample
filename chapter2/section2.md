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
输出为PDF文件，这个过程可能比较波折，需要先使用NPM安装上gitbook pdf：
```
$npm install gitbook-pdf -g
```
> Windows 版本一般能够顺利安装gitbook-pdf


然后，使用下面的命令，可生成PDF文件了：
```
$gitbook pdf ./图书目录
```
如果你在图书目录内容，也可以这样做：
```
$gitbook pdf .
```
> 转pdf时需要calibre 的ebook-convert组件支持, 如果遇到  
`EbookError: Error during ebook generation: 'ebook-convert'`  
的错误，此时请到[这里](https://calibre-ebook.com/download) 手动安装
> 还会遇到 `Error: ENOENT: no such file or directory, stat`  
此时请参考这个帖子修正：[random errors when using gitbook plugin on running "gitbook serve"](https://github.com/GitbookIO/gitbook/issues/1309)
> 更有甚者，可能会遇到
```
Failed to load libGL.so   
error libGL.so: cannot open shared object file: No such file or directory
```
此时可以尝试以下命令安装libGL.so 支持
```
$ sudo apt-get install git-core gnupg flex bison gperf build-essential \
	zip curl libc6-dev libncurses5-dev:i386 x11proto-core-dev \
	libx11-dev:i386 libreadline6-dev:i386 libgl1-mesa-glx:i386 \
	libgl1-mesa-dev g++-multilib mingw32 openjdk-6-jdk tofrodos \
	python-markdown libxml2-utils xsltproc zlib1g-dev:i386
$ sudo ln -s /usr/lib/i386-linux-gnu/mesa/libGL.so.1 /usr/lib/i386-linux-gnu/libGL.so (这一步某些Ubuntu版本不需要)
```

然后，你会发现你的目录里多了一个名为book.pdf的文件，就是它了！
但是，笔者在测试的时候发现，生成的PDF文件在排版上不是合理，如页面的边距明显过小，如果是图文混排的话，整个版面感觉有些零乱。

#### PDF输出格式调整
book.json
```
{
	"gitbook": "3.x.x",
	"title": "GitBook从安装到第一本样书示例",
	"description": "GitBook从安装到第一本样书示例版",
	"language": "zh",
	"structure": {
		"readme": "README.md"
	},

	"pluginsConfig": {
		"fontSettings": {
		"theme": "white",
		"family": "msyh",
		"size": 2
		},
		"plugins": [
		"yahei",
		"katex",
		"-search"
		]
	},

	"pdf": {
		"pageNumbers": true, 
		"fontFamily": "Arial",
		"fontSize": 12,
		"paperSize": "a4",
		"margin": {
			"right": 62,
			"left": 62,
			"top": 56,
			"bottom": 56
		}
	}
}
```

Variable | Description
------------------- |--------------------------------
pdf.pageNumbers    |   是否添加页码，默认是true
pdf.fontSize    |   字体大小，默认是12
pdf.fontFamily    |  		 字体，默认字体是Arial)
pdf.paperSize    |Paper size, options 	are 'a0', 'a1', 'a2', 'a3', 'a4', 'a5', 'a6', 'b0', 'b1', 'b2', 'b3', 'b4', 'b5', 'b6', 'legal', 'letter' (default is a4)
pdf.margin.top    |   Top margin (default is 56)
pdf.margin.bottom|   Bottom margin (default is 56)
pdff.margin.right|   Right margin (default is 62)
pdf.margin.left    |  		 Left margin (default is 62)
```
