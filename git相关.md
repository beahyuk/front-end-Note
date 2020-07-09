# git学习

## 新建git远程仓库

在本地项目的文件夹内打开cmd

1. 在本地项目文件夹内打开cmd

2. 输入以下代码

   ```git
      1. git init ->.git  //生成.git文件
      2. git status      //查看状态
      3. git add .      //增加文件
      4. git commit -m "注释"
   ```
   
4. 在代码托管平台(GitHub) 新建远程仓库

4. 继续在cmd输入代码

   ```
   1. git remote add origin  项目名  //关联仓库,新建仓库后会有代码提示
   2. git push -u origin master //之后再push,直接git push
   
   ```


## 已有项目连接数据库

1. 在本地新建数据库pm_db

2. 在idea新建mysql database为pm_db

3. 改jdbc的url,项目名

   ```
   jdbc.driver=com.mysql.cj.jdbc.Driver
   jdbc.url=jdbc:mysql://localhost:3306/pm_db?useSSL=false&serverTimezone=UTC
   jdbc.user=root
   jdbc.password=123456
   
   ```

4. 点击运行已有的脚本sql.sql

> 坑: 注意tomcat的接口和 项目的接口 是否相同



## 创建vue项目

1. vue create 项目名

2. 选择设置,手选设置,按空格为选中

3. 是否给Babel,ESlint等单独搞个文件

   1. in dedicated config files 单独搞个文件
   2. 不选in package json

4. 项目生成后,添加一个文件,增加别名设置

   ```js
   //文件名:vue.config.js
   const path = require('path');
   function resolve (dir) {
     return path.join(__dirname, dir)
   }
   module.exports = {
     lintOnSave: true,
     chainWebpack: (config)=>{
       config.resolve.alias
         .set('@', resolve('src'))
         .set('assets',resolve('src/assets'))
         .set('components',resolve('src/components'))
         .set('views',resolve('src/views'))
     },
     devServer: {
       open: true, //是否自动弹出浏览器页面
       host: "127.0.0.1", 
       port: '8081', 
       https: false,   //是否使用https协议
       hotOnly: false, //是否开启热更新
       proxy: {
           '/api': {
               target: 'http://127.0.0.1:8080', //API服务器的地址
               ws: true,  //代理websockets
               changeOrigin: true, // 虚拟的站点需要更管origin
               pathRewrite: {   //重写路径 比如'/api/aaa/ccc'重写为'/aaa/ccc'
                   '^/api': ''
               }
           }
       },
     }
   }
   
   
   ```

   ![image-20200503151706588](E:\学习笔记markdown\git相关.assets\image-20200503151706588.png)

   

   