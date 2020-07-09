# JS学习笔记

## JavaScript视频学习 -coderwhy

### p7 JS的注意事项

#### 1.Js的注意事项

1. script标签不能写成但标签
2. 可以省略script标签中的type属性
3. 加载顺序
   1. 作为HTML文档内容的一部分,JS默认遵循HTML文档的加载顺序,即自上而下的加载顺序
   2. 推荐将JavaScript代码和编写位置放在body子元素的的最后一行
4. JavaScript代码严格区分大小写
   1. HTML元素和CSS属性不区分大小写,但是在JavaScript中严格区分大小写

####  2.DOM操作

DOM操作:Document Object Manager

```js
<body>
    <h2 class="title">hhhhh</h2>
    <script>
        //DOM操作:Document Object Manager
        document.querySelector('.title').onclick = function() {
            console.log("hello word")
        }
    </script>
</body>
```

### P8 JavaScript注释的写法

```js
        // JavaScript注释方法:文档注释法
        /**
         *这是一个测试函数
         */
        function test() {

        }
        test()
```

### P9 Javascript和浏览器交互

1. 交互方式一:浏览器弹出弹窗

   ```js
   alert("hello word")
   ```

2. 交互方式二:在控制台打印一段内容

3. 交互方式三:DOM操作时(了解)

   ```js
   doucument.write("<H2>hello word</H2>")
   ```

4. 交互方式四:接受用户输入的一个内容(了解)

   ```js
   var age = prompt("请输入你的年龄");
   console.log("您的年龄:",age)
   ```

### P10 变量-变量定义的方式

```
        // 1.定义变量赋值
        // 1.1 变量的定义同时进行赋值
        var name = "why"

        // 1.2 给变量重新赋值
        name = "kobe"

        // 2.先定义(声明),但是后面再进行赋值
        var age;
        age = 10;
```



### P11 变量-同时声明赋值多个变量

```js
// 同时定义多个变量
var num1,num2,num3;
num1 = 10;
num2 = 20;
num3 = 20;

var num4 = 20,num5 = 23, num6 = 21;
```

## JavaScript 高级程序设计

### 疑问地方

- P181
- P187
- P192



