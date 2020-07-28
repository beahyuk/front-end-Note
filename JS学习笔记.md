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

### P12 变量的命名规则

- 变量名规则：必须遵守
  - 第一个字符必须是一个字母，下划线（_）或一个美元符号（$）
  - 其他字符可以是字母，下划线，美元符号或数字
  - 不能使用关键字和保留字
    - int这种

### p13 代码的书写规范

- 变量命名规范：建议遵守
  - 多个单词使用驼峰标识
  - 赋值 = 两边都加上一个空格
  - 一条语句结束后加上分号;

### p17 数字类型的表示方法

- JavaScript**基本的数据类型**
  - 数值型（Number）
  - 字符串型（string）
  - 布尔型（Boolean）
  - 空类型（Null）
  - 未定义类型（Undefined）
- 注意：这是基本数据类型，后面还有引用类型

### p19 数字类型 - NaN和isNaN的理解

- NaN：即非数值（Not a Number）是一个特殊的数值，js中当对数值进行计算时没有结果返回，则返回NaN
- isNaN：用于判断是否不是一个数字，不是数字返回true，是数字返回false

### p22  Undefined和Null的使用

- undefined类型只有一个值：undefined

  - 在使用var声明变量但未对其加以初始化时，这个变量的值就是undefined
  - typeof对没有初始化和没有声明的变量都会返回undefined

- Null类型也是只有一个值：undefined

  - 通常当一个对象（Object类型）不再使用时，可以赋值为NUll

- Null和Undefined的关系：

  - undefined值实际上是由null值衍生出来的，所以如果比较undefined和null是否相等，会返回true

  - ```js
    console.log(undefined == null )//true ,一定是两个等于，不可以三个等于
    ```

  - 面试会问到

### p23 变量在内存中的存储空间

- 内存的分类：栈空间和对空间
- 代码是保存在硬盘里的，例如f盘
- 当定义了一个基本数据类型，会去内存的栈空间申请一个空间
- 如果是定义了引用类型，会去堆空间申请一个空间，并且在栈空间中申请空间保存堆空间的内存地址
- ![image-20200727210948419](E:\学习笔记markdown\JS学习笔记.assets\image-20200727210948419.png)

### p24 转成数字类型- 方式一

- 将其他类型转成数字类型的方法：
  - Number(any)函数：将任意类型转成数字

### p26 字符串转成数字类型 - 方式二

- parseInt(string,radix)函数：将字符串转换成整数类型，radix表示基数，这里可以理解为进制

  - 如果第一个字符是数字或运算符号，那么就开始解析，知道遇到非数字字符，停止解析并得到解析结果
  - 如果第一个字符是非数字且非运算符号，则不解析并得到结果NaN

- parseFloat(string)函数：将字符串转换成浮点类型（小数类型）

  - 如果第一个字符是数字或运算符号，那么就开始解析，知道遇到非数字字符，停止解析并得到解析结果
  - 如果第一个字符是非数字且非运算符号，则不解析并得到结果NaN

  例如：`parseInt("abc")或parseInt("123abc")` 第一个是NaN，第二个是123

### p28 其它类型转成字符串类型

- 调用toString（）方法
- String（内容）
- 字符串拼接
  - `a= b+""` 只要是跟字符串有+ 就会拼接，成为字符串，就算是空的也行

### p29 其他类型转成布尔类型

- Boolean()函数 转为布尔类型
- 转换成false的五种特殊值： “ ”（空字符串），0（包括-0,0），undefined，null，NaN 
  - 如果某个值为 “ ”（空字符串），0（包括-0,0），undefined，null，NaN 时，结果返回false
  - 其余都返回true
- if（）做判断的时候，就会用到隐式的Boolean转换

JavaScript按照使用场景的不同将运算符分成了很多种类型

- 算术运算符、赋值预算福、关系（比较）运算符、逻辑运算符

### p31 算术运算符 - 基本算术运算符

- \+ 也可以作为连接字符串用
-  % 取余数
- ++ 自增 num++ 先运算后自增       ++num  先自增后运算
- -- 自减   num--  先运算后自减         --num 先自减后运算
- 只记得num++的顺序就像

### p35 关系运算符 - 全等和全不等

- == 比较：会进行隐式转换，再比较，例如字符串和布尔类型比较，都会转成number数字类型
- === 全等：类型相等，数据相等 。   这个在开发中用的更多，严谨一点
- !=  比较：隐式转换
- !==比较：不会进行隐式准换

### p36 逻辑运算符-使用过程

- 与运算：&&  ->  两个条件同时满足
- 或运算：|| ->  满足一个条件
- 取反运算： ！->  对之前的Boolean类型取反

## JavaScript 高级程序设计

### 疑问地方

- P181
- P187
- P192



