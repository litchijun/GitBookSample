# 图书项目结构
README.md和SUMMARY.md是Gitbook项目必备的两个文件，也就是一本最简单的gitbook也必须含有这两个文件，它们在一本Gitbook中具有不同的用处。
## README.md 与 SUMMARY编写
### README.md
这个文件相当于一本Gitbook的简介。
### SUMMARY.md
这个文件是一本书的目录结构，使用Markdown语法，新建一个测试用的示例书目录：
```
* [简介](README.md)  
* [第一章](chapter1/README.md)  
 - [第一节](chapter1/section1.md)  
 - [第二节](chapter1/section2.md)  
* [第二章](chapter2/README.md)  
 - [第一节](chapter2/section1.md)  
 - [第二节](chapter2/section2.md)  
* [结束](end/README.md) 
```
