# markdown语法参照

![image-20200415141455851](C:\Users\xq\AppData\Roaming\Typora\typora-user-images\image-20200415141455851.png)

# html 学习笔记

## p2 邂逅软件开发

服务器 -> 安卓端 iOS端 网页端

Flutter ->dart -> ios/android /ios/pc

Weex -> vuejs -> ios/android

## p3 网站-浏览器显示网页过程

### 网页的显示过程

客户端发送网络请求 服务器

服务器返回html等数据给浏览器解析

## p4 浏览器的内核分类

 ### 网页组成

- HTML（超文本标记语言）
- css（样式）
- js（交互）

### 浏览器内核

>  浏览器内核用来解析html，css，js这些内容，不同内核解析渲染效果不同

常见的浏览器内核：

- trident（三叉戟）：IE，360，搜狗
- gecko（壁虎）：Firefox
- webkit：safari，360，搜狗，移动端浏览器（Android。iOS）
- webkit -> blink：Google chrome

## p5 记事本开发第一个页面

### ！doctype的作用

- HTML文档声明，告诉浏览器当前页面是HTML5页面，让浏览器用ＨＴＭＬ５的标准去解析识别HTML文档
- 必须放在HTML文档的最前面，不能省略，省略了回出现兼容性问题