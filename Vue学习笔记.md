# vue学习笔记3.30

> 从GitHub从下载vue项目如何运行？

- npm install  （操作不允许时，以管理员身份运行命令行）

  ![image-20200330104838091](C:\Users\xq\AppData\Roaming\Typora\typora-user-images\image-20200330104838091.png)

> 测试后台遇到的技术难点

1. el-tree-select element 的选择框和树形相结合
   - ![image-20200405222435129](C:\Users\xq\AppData\Roaming\Typora\typora-user-images\image-20200405222435129.png)	
   - 将GitHub上的valueId删掉，组件中用到Id的全改成name
   - https://github.com/KBeginner/el-tree-select 修改的代码
   
2. 选择子节点后，关闭选项框

   ## typora打印完整的pdf文档

   文章中不要有<>这种标签,否则就停止转化

## P27 const的使用和注意点

const主要的作用是将某个变量修饰为常量,被const修饰的标识符为常量,不可以再次赋值

const修饰 对象时,可以修改对象的值.因为const P是存储对象所在的地址,对象是引用时间,如果对象的地址不变,那么就可以用const来修饰

```js
const obj = {
	name:'why',
    age:'18',
    height:'1.88'
}
// 修改obj对象的值
obj.name = "xx";
obj.age = 21;
obj.height = 1.77
```

