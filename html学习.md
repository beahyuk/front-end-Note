# markdown语法参照

![image-20200415141455851](C:\Users\xq\AppData\Roaming\Typora\typora-user-images\image-20200415141455851.png)

# html 学习笔记

## 一.HTML基础练习

### p2 邂逅软件开发

服务器 -> 安卓端 iOS端 网页端

Flutter ->dart -> ios/android /ios/pc

Weex -> vuejs -> ios/android

### p3 网站-浏览器显示网页过程

#### 网页的显示过程

客户端发送网络请求 服务器

服务器返回html等数据给浏览器解析

### p4 浏览器的内核分类

#### 网页组成

- HTML（超文本标记语言）
- css（样式）
- js（交互）

#### 浏览器内核

>  浏览器内核用来解析html，css，js这些内容，不同内核解析渲染效果不同

常见￥的浏览器内核：

- trident（三叉戟）：IE，360，搜狗
- gecko（壁虎）：Firefox
- webkit：safari，360，搜狗，移动端浏览器（Android。iOS）
- webkit -> blink：Google chrome

### p5 记事本开发第一个页面

#### ！doctype的作用

- HTML文档声明，告诉浏览器当前页面是HTML5页面，让浏览器用ＨTML５的标准去解析识别HTML文档
- 必须放在HTML文档的最前面，不能省略，省略了回出现兼容性问题

## 十二.浮动 float

#### p180 浮动的理解-规则一

- 元素一旦浮动后
  - 脱离标准流
  - 朝着向左或向右方向移动，直到自己的边界紧贴着包含块（一般是父元素）或者其他浮动元素的边界为止
- 定位元素会层叠在浮动元素上面

#### p181 浮动的理解-规则二

- 浮动元素不能与行内级内容层叠，行内级内容将会被浮动元素推出
  - 比如行内级元素，inline-block元素，块级元素的文字内容

#### p182 浮动的理解-规则三

- 行内级元素，inline-block元素浮动后，其顶部将与所在行的顶部对齐
  - 例如图片和文字，图片浮动后，文字会与图片顶部对齐

#### p183 浮动的理解-前面规则的现象

综合前面几条应用并解释：

- div2 进行左浮动/有浮动的时候，只会在当前自己行中浮动
- div1 进行左浮动时，div2 在没有浮动时，div0的排布是?
  - div1覆盖div2上
- div1 进行左浮动时，div2 在没有浮动时，但里面有文本，文本会如何排布？
  - 根据规则二，**浮动元素不能与行内级内容层叠，行内级内容将会被浮动元素推出**
  - 所以文字会在浮动元素外面
- div1 进行左浮动时，div2也进行浮动时，那么div1和div2以此在第一行排布
- div1 和div2 都进行浮动，但是父元素没有设置高度，那么父元素的高度会消失（高度的坍塌）

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        .div0 {
            background: #ffc700;
        }
        
        .div1 {
            float: left;
            width: 100px;
            height: 100px;
            background: #4e57d0;
        }
        
        .div2 {
            width: 150px;
            height: 150px;
            background: #e94242;
        }
    </style>
</head>

<body>
    <div class="div0">
        <div class="div1"></div>
        <div class="div2">我是测试文本</div>
    </div>
</body>

</html>
```

#### p184 浮动的理解-规则四和五

##### 浮动的规则四

- 如果元素是向左（右）浮动，浮动元素的左（右）边界不能超出**包含块**的左（右）边界

##### 浮动的规则五

- 浮动元素之间不能层叠
  - 如果一个元素浮动，另外一个浮动元素已经在那个位置了，后浮动的元素将紧贴着前一个浮动元素（左浮动找左浮动，右浮动找右浮动）
  - 如果水平方向剩余的空间不够显示浮动元素，浮动元素将向下移动，直到有充足的空间为止



#### p185 浮动的理解-浮动的规则六

浮动元素的顶端不能超过包含块的顶端，也不能超过之前所有浮动元素的顶端

#### p186 浮动的理解-浮动的总结和应用

- 浮动常用的场景
  - 解决行内级元素，inline-block元素的水平间隙问题
  - 布局
  - 例如：京东首页的布局，就是用浮动完成，保证了每个卡片之间的间距。一般来说，行内级元素或者inline-block元素之间有间隙是因为换行，有空格了，所以有空格，这个间隙大小是由html{font-size：26px}决定的。**用了浮动后就能准确的计算间隙大小**，是单纯的margin值，不加间隙的值了

#### p197 浮动高度坍塌-清浮动

##### 浮动存在的问题

- 由于浮动元素脱离了标准流，变成了脱标元素，所以不再向父元素汇报高度
- 父元素计算总高度时，就不会计算浮动子元素的高度，导致了高度坍塌的问题
- 解决父元素高度坍塌问题的过程，一般叫做清浮动（清理浮动，清除浮动）
- 清浮动的目的是
  - 让父元素计算总高度的时候，把浮动子元素的高度算进去

##### 清浮动的常见方法

- 给父元素设置固定高度

  - 扩展性不好**（不推荐）**

- 在父元素最后增加一个空的块级子元素，并且让它设置clear:both

  - 会增加很多无意义的空标签，维护麻烦
  - 违反了结构与样式分离的原则**（不推荐）**

- 在父元素最后增加了一个br标签：`<br clear='all>`

  - 会增加很多无意义的空标签，维护麻烦
  - 违反了结构与样式分离的原则**（不推荐）**

- 给父元素增加::after伪元素

  - 纯css样式解决，结构与样式分离**（推荐）**

  - ```css
    .clear-fix::after{
        content:'';
        display:block;
        clear:both;
        height:0 ;/* 兼容旧浏览器*/
        visibility:hidden; /*兼容旧浏览器*/
    }
    .clear-fix{
        *zoom:1; /*兼容IE6~7浏览器*/
    }
    ```

##### CSS属性-clear

- clear的常用取值
  - left:要求元素的顶部低于之前生成的所有左浮动元素的底部
  - right:要求元素的顶部低于之前生成的所有右浮动元素的底部
  - both:要求元素的顶部低于之前生成的所有浮动元素的底部
  - none:默认值，无特殊要求
- 一般就只用在非浮动元素上，可以让非浮动元素与浮动元素不层叠

## 十三.补充

### transform变形

- CSS transform属性允许你旋转，缩放，倾斜或平移给定元素。

- Transform是形变的意思
- 常见的函数transform function有：
  - 平移：translate(x,y)
  - 缩放：scale(x,y)
  - 旋转：rotate(deg)
  - 倾斜：skew(deg,deg)

#### p199 transform-translate使用

- 平移：translate（x，y）
- 值个数
  - 一个值时，设置x轴上的位移
  - 两个值时，设置x轴和y轴上的位移
- 值类型：
  - 数字：100px
  - 百分比：参照元素本身

一般用最多，水平居中和垂直居中的时候用的最多，父绝子相

#### p200 transform-scale使用

- 缩放：scale（x，y）
- 值个数
  - 一个值时，设置x轴上的缩放
  - 两个值时，设置x轴和y轴上的缩放
- 值类型
  - 数字：
    - 1：保持不变
    - 2：放大一倍
    - 0.5：缩小一半
  - 百分比：不支持百分比

#### p201 transform-origin使用

- transform-origin：变形的原点
- 值个数
  - 一个值时，设置x轴的原点
  - 两个值时，设置x轴和 y轴的原点
- 值类型
  - length：从左上角开始计算
  - left，center，right，top，bottom关键字
  - 百分比：参考元素本身大小

#### p202 transform-rotate使用

- 旋转：rotate（deg）
- 值个数
  - 一个值时，表示旋转的个数
- 值类型
  - deg：旋转的角度
  - 正数为顺时针
  - 负数为逆时针
- 注意：旋转的原点受transform-origin的影响

#### p203 transform-skew使用

- 倾斜：skew（x，y）
- 值个数
  - 一个值时，表示x轴上的倾斜
  - 两个值时，表示x轴和y轴上的倾斜
- 值类型
  - deg：旋转的角度
  - 正数为顺时针
  - 负数为逆时针
- 注意：倾斜的原点受transform-origin的影响

### transition动画

#### p204 transition的过渡动画

- transition CSS属性是transition-property，transition-duration，transition-timing-function和transition-delay
- transition-property：指定应用过渡属性的名称
  - 可以写all表示所有可动画的属性
  - 属性是否支持动画查看文档
- transition-duration：指定过渡动画所需的时间
  - 单位可以是秒（s）或毫秒（ms）
- transition-timing-function：指定动画的变化曲线

```css
.box{
    transition:值1 transition-property:transform/width/height/all
        	   值2 transition-duration:100ms(毫秒)/1s(秒)
        	   值3 transition-timing-function：动画的变化速度：ease/ease-in
        	   值4 transition-delay：延迟/等待多久再执行这个动画；
}
```



### HTML-CSS3的概念

#### p237 HTML和CSS3的概念

- HTML5 是定义HTML标准的最新版本，该术语通过两个不同的概念来表现：
  - 狭义的HTML5说的是HTML新的元素和属性
  - 广义的HTML5说的是HTML5新的标准，包括最新的HTML元素+css新特性+JavaScript
- CSS3目前并不存在真正意义上的CSS3，只是对某些Module Level 3的统称

#### p238 HTML5新增语义化元素

- HTML5新增了语义化的元素
  - `<header> `：头部元素
  - `<nav> `：导航元素
  - `<section>`：定义文档某个区域的元素
  - `<article>`：内容元素
  - `<aside>`：侧边栏元素
  - `<footer>` ：尾部元素
- 这些语义化的元素就是**普通的块级元素**，只是增加了语法。

#### p239 HTML多媒体元素-video

- HTML5新增了对媒体类型的支持（在HTML5之前是通过flash或者其他插件实现的）
  - 音频：`<audio>`
  - 视频：`<video>`
- HTML `<video>`元素 用于在HTML或者XHTML文档中嵌入媒体播放器，用于支持文档内的视频播放
- `<video>`元素常见属性：
  - src：媒体的来源
  - controls：增加控制工具栏
  - autoplay：自动播放，但存在兼容问题
  - muted：静音，增加后不静音并且自动播放会生效
  - loop：循环播放
- `<source>`元素
  - 如果存在兼容性问题，可以将多个视频格式的数据源放到source元素中
  - src：通过src指定数据的来源

#### p241 HTML多媒体元素 - audio

- HTML`<audio>`元素用于在文档中表示音频内容
- `<audio>`元素常见的属性：和video一样
- `<source>`元素也和video一样

#### p242 HTML对表单元素扩展

- HTML5对input进行了扩展，在之前我们已经学习过的其中几个属性也是HTML5的特性：
  - placeholder：输入框的占位文字
  - multiple：多个值
  - autofocus：最多输入的内容
- 另外对input的type值也有很多扩展
  - date，time，number，tel，color，email等等
- 还可以设置color的类型

### flex布局

#### p243 flex布局-认识flex布局重要概念

- flex布局是目前web开发中使用最多的布局方案：
  - flex布局（又称为flexible 布局，弹性布局）
  - 目前特别在移动端用的最多，现在pc端也用的多
- 两个重要概念
  - 开启了flex布局的元素叫 **flex container**
  - flex  container 里面的直接子元素叫做 **flex items**
- 设置display属性为flex或者inline-flex 可以成为flex container
  - flex：说明flex container 是块级元素
  - inline-flex：说明flex container是行内元素

#### p244 flex布局-认识flex的布局模型

- flex相关的属性
- 应用在flex container 上的css属性
  - flex-flow
  - flex-direction
  - flex-wrap
  - justify-content
  - align-items
  - align-content
- 应用在flex items上的css元素
  - flex
  - flex-grow 扩展
  - flex-shrink 收缩
  - flex-basis 宽度
  - order
  - align-self

#### flex-container属性

##### p245 flex-container属性-flex-direction

- flex items 默认都是沿着main axis（主轴，默认是水平）从main start开始往main end方向排布
- flex-direction决定了main axis的方向，有四个方向
  - row（默认值），row-reverse，column，column-reverse

##### p246 flex-container属性-justify-content

- justify-content决定了flex items 在main axis上的对齐方式
  - flex-start（默认）：与main start对齐
  - flex-end：与main end 对齐
  - center：居中对齐
  - space-between：flex items之间的距离相等，与main start ，main end 两端对齐
  - space-evenly：flex items之间的距离相等，与main start ，main end 之间的距离等于flex items之间的距离
  - space-around：flex items之间的距离相等，与main start ，main end 之间的距离是flex items之间的距离的一半

##### p247 flex-container属性 -align-items

- align-items决定了flex items在cross axis上的对齐方式（默认垂直）
  - normal和stretch 很少用
  - flex-start：与cross start 对齐
  - flex-end：与cross-end对齐
  - center：居中对齐
  - baseline：与基准线对齐

##### p248 flex-container属性-flex-wrap

- flex-wrap决定了flex-container是单行还是多行
  - nowrap（默认）：单行
  - wrap：多行
  - wrap-reverse：多行（对比wrap，cross start与cross end相反）

##### p249 flex-container属性-flex-flow

- flex-flow是flex-direction || flex-wrap的简写
  - 可以省略，顺序任意

##### p250 flex-container属性-align-content

- align-content决定了多行flex items在cross axios 上的对齐方式，用法与justify-content类似

#### flex-items属性

##### p251 flex-items属性-order

- order决定了flex items的排布顺序（用的不是很多）
  - 可以设置任意整数（正整数，负整数，0），值越小就越排在前面
  - 默认值是0

##### p252 flex-items属性-align-self

- flex items可以通过align-self覆盖flex container设置的align-items
- 用的不是很多，就是单个可以自己设置在交叉轴上的排列方式，效果跟align-items一致

##### p253 flex-items属性-flex-grow

- flex-grow决定了flex items如何扩展
  - 可以设置任意非负数字（正小数，正整数，0），默认值是0
  - 当**flex containe**r在main axis方向上**有剩余size**时，flex-grow属性才会有效
- 如果所有flex items的flex-grow总和sum超过1，每个flex item扩展的size为
  - flex container的剩余size * flex-grow/sum
- 如果所有flex items的flex-grow总和sum不超过1，每个flex item扩展的size为
  - flex container的剩余size * flex-grow
- flex items 扩展后的最终size不能超过max-width\max-height

##### p254  flex-items属性-flex-shrink

- flex-shrink决定了flex items如何收缩
  - 可以设置任意非负数字（正整数，正小数，0），默认是0
  - 当flex items在main axis方向上**超过**了**flex container的size**，flex-shrink属性才会有
- 如果所有flex items的flex-shrink总和超过1，每个flex item收缩的size为
  - flex items超过flex container的size * 收缩比例/所有flex items的收缩比例之和
- 如果所有flex items的flex-shrink总和的sum不超过1，每个flex item收缩的size为
  - flex items超过flex container的size * sum *收缩比例/所有flex items的收缩比例之和
  - 收缩比例 = flex-shrink * flex item的base size
  - base size 就是flex item 放入flex container之前的size
- 二三条不是很懂，收缩比例啥的

##### p255 flex-items属性-flex-basis

- flex-basis用来设置flex items在main axis方向上的base size
  - auto（默认值），具体的宽度数值（100px）
- 决定flex items最终base size的因素，从优先级高到低
  - max-width\max-height\min-width\min-height
  - flex-basis
  - width\height
  - 内容本身的size
- flex-basis是用来设置宽度，但是很少用，一般都是直接设置width

##### p256 flex-items属性-flex

- flex是flex-grow || flex-shrink || flex-basis的简写，flex属性可以指定1个，2个或者3个值
- flex：1 表示的是flex-grow：1 ，扩展为1

### HTML和CSS补充

#### 网路字体的使用

##### p259 网络字体的使用

- @font-face可以让网页支持网络字体（web Font），不再局限于系统自带的字体

- 常见的字体种类

  - TRUEType字体：扩展名：.ttf
  - 等等

- @font-face的使用

  ```css
  <style>
  @font-face{
      /*字体名称，可以随便写，但建议最好跟原字体名称一致*/
      font-family:"迷你简立黑";
      /*浏览器会按照顺序加载每一个字体文件，直到找到它支持的字体*/
      /*把字体文件放在fonts里*/
      src:url('fonts/mini_black.ttf'),
          url("fonts/mini_black.otf")
  }
  div{
      font-family:"迷你简立黑";
      font-size:14px
  }
  </style>
  ```

#### 图片使用方式总结

在页面中，使用图片的方式：

- img元素
  - 网站的重要组成部分
  - 不能用精灵图
- background-image
  - 装饰
  - 先加载css -> url
  - 使用精灵图 -> background-position
- iconfont字体图标
  - 字体图标放大时，不会失真
  - 图片不会失真
  - 图片过多时，减少请求的次数
  - 图片过多时，相当于压缩图片

iconfont可以使用阿里图标库。四条都是iconfont的优点

#### 动画

##### p263 关键帧动画的使用

- 关键帧动画使用@keyframes来定义多个变化状态，并且使用animation-name来声明匹配

  - 1.使用@keyframes来创建一个规则
  - 2.@keyframes中使用百分比定义各个阶段的样式
  - 3.通过animation将动画添加到属性上
  - 另外，也可以使用from和to关键字。from是0%，to是100%

- animation属性：

  - 值1：使用的关键字帧动画名称
  - 值2：动画执行的时间
  - 值3：动画的速率

  ```css
  .box:hover{
      animation:test1 2s linear,test2 2s linear /*可以使用多个关键帧动画*/
  }
  @keyframes test1{
      from{
          transform:translate(0,0),scale(1,1);
      }
      25%{
          transform:translate(200px,0);
      }
      to{
          transform:traslate(0,0)
      }
  }
  @keyframes test2{
      /*不能和test1相同，不然会覆盖或者被盖住*/
  }
  ```

##### p264 页面动画实现方案

- css实现3D：
  - 父元素开启两个值
  - 1.transform-style：preserve-3d
  - 2.perspective
- JS实现3D的库
  - three.js  
  - 一般用js做3d动画

#### 文字省略号

##### p268 文字省略号的显示

css属性 - **text-overflow**

- white-space 用于设置空白处理和换行规则
  - normal：自动换行
  - nowrap：不自动换行
- text-overflow 用于设置 文字溢出时的行为（处理那部分不可见的内容）
  - clip：剪裁掉 溢出的内容
  - ellipse：省略号表示 溢出的内容
  - text-overflow生效的前提是overflow不为visible

- 显示一行文本并且有省略号的方法，三行代码

  ```css
  white-space：nowrap；/*不自动换行*/
  overflow:hidden;
  text-overflow:ellipsis;
  ```

- 显示两行文本并且显示省略号的方法

  ```css
  display:-webkit-box;
  -webkit-line-clamp:2; /*表示两行文本*/
  -webkit-box-orient:vertical;
  text-overflow:ellipsis;
  overflow:hidden;
  /*注意不要设置高度，因为设置高度后就算设置了两行文本，也会把剩下内容显示出来*/
  ```

#### 视口

##### p269 移动端适配-视口的设置

- 视口的大小：viewport

  ```html
  /*在HTML页面的head头部定义*/
  <meta name="viewport" content = "width=device-width,initial-scale=1.0">
  ```

- 移动端默认视口大小是980px，所有的元素在移动端没有设置视口的情况下会被缩小

  - width：设置视口的大小
  - initial-scale：设置缩放的比例

#### em单位

##### p270 不同的单位相对谁

- width宽度大小
  - px：200px
  - em:
    -  自己有设置的**font-size**，em相对自己的font-size，20*自己font-size
    -  自己没有设置的font-size，em相对**父元素的font-size**，20*父元素的font-size
  - %：相对于**父元素的宽度**
- margin-top
  - %：相对于**父元素的宽度**
- font-size
  - px：像素
  - em：相对于父元素字体的大小
  - %：相对于父元素字体的大小

##### p271 rem单位的使用

- rem的使用是根HTML root的大小

```html
<style>
    html{
        font-size:12px;
    }
    .box{
        font-size:2rem;
        width:200rem /*rem相对的是根元素字体的大小*/
    }
</style>
```

##### p272 rem如何进行移动端适配

- 问题一：动态设置html的font-size
  - 方法一：媒体查询
  - 方法二：通过**js动态计算**（最优方案）
- 问题二：动态计算rem的值
  - 方法一：利用vscode的插件快速转化
    - 插件:px to rem
    - 快捷键：alt+z
  - 方法二：利用postcss-pxtorem（最优方案）
    - postcss-pxtorem是js的一个包，在node里npm安装
  - 方法三：利用less，sass，stylus的计算能力
- 一般是通过js动态计算font-size，然后用postcss-pxtorem动态计算rem值

#### less

##### p273 less的基本使用

- Less是一种css预处理器，对css进行了扩展
- vscode的less插件：Easy LESS
- less学习的好处
  - less变量的定义，可以引入变量
  - less代码编写格式
  - less的加减乘除运算

