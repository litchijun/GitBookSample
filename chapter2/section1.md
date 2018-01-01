## 目录初始化
当这个目录文件创建好之后，我们可以使用Gitbook的命令行工具将这个目录结构生成相应的目录及文件：
```
D:\gitbook\mybook>gitbook init
info: create chapter1/README.md
info: create chapter1/section1.md
info: create chapter1/section2.md
info: create chapter2/README.md
info: create chapter2/section1.md
info: create chapter2/section2.md
info: create end/README.md
info: create SUMMARY.md
info: initialization is finished

D:\gitbook\mybook>tree .
文件夹 PATH 列表
卷序列号为 00000002 0236:A566
D:\GITBOOK\MYBOOK
├─chapter1
├─chapter2
└─end
```
我们可以看到，gitbook给我们生成了与SUMMARY.md所对应的目录及文件。
每个目录中，都有一个README.md文件，相当于一章的说明。
