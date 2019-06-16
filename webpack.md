###webpack 自动化构建工具、项目构建、打包处理、转换让浏览器支持的语法 
https://www.webpackjs.com/concepts/ 官网
> 难点-> 英文
> 目标:当学完之后，希望大家都能够自己手动配置webpack
> 一般结果 -> 学完之后，啥东西？干啥的？我是谁？我在哪？

> <div id="box"></div> -> <div id=box></div>

### 四个核心概念
- 入口(entry)
```
    entry:'./2.js',  字符串，单入口
    entry:['./2','./1'], //多入口单出口
    output:{
        filename:'haha.js'
    }
    //多入口多出口
    entry:{
        index:'./2',
        aa:'./1'
    },
    output:{
        filename:'[name].[hash:8].js'  
    }
    name就表示entry的key

```
- 输出(output)
- loader
> 模块的源代码进行转换
```
module:{
    rules:[
        {
            test:/\.css$/,  //处理上面文件
            use:[需要的模块]
        }
    ]
}
```

- 插件(plugins)
plugins:[new HTML({}),new Xxx()]

### 安装
-   npm i webpack webpack-cli --golbal  （第一次安装需要那么做）
-   项目目录名称千万不要写webpack
-   npm init -y(到你项目的目录中输入)
-   npm i webpack webpack-cli --save   （只要安装过，就不用安装上面那句话了）

### 配置
- 自己手动创建一个webpack.config.js的文件

```
const path = require('path');
const obj = {
    entry:'./2.js',
    output:{
        filename:'2.js',
        path:path.relove(__dirname,'./build')
    }
}
module.exports = obj;

```
### 设置package.json 文件
> 找到scripts 设置值为 "build（自定义名称）":"webpack"
> 到命令行输入npm run build

### mode设置

> production  生产环境   让用户看的
> development 开发环境   让程序员看的

配置 mini-css-extract-plugin
npm i mini-css-extract-plugin -S

const HtmlWebpackPlugin = require('html-webpack-plugin');//抽离html和js的
const MiniCssExtractPlugin = require('mini-css-extract-plugin');////抽离css的
安装压缩js环境//4.0自动压缩  不需要了
npm i uglifyjs-webpack-plugin --save-dev
可以安装成功
```
PS C:\Users\chen0104\Desktop\exprice> npm i uglifyjs-webpack-plugin --save-dev
npm WARN exprice@1.0.0 No description
npm WARN exprice@1.0.0 No repository field.

+ uglifyjs-webpack-plugin@2.1.3
added 3 packages from 38 contributors and audited 5821 packages in 5.782s
found 0 vulnerabilities
```
## 开发环境 development
安装npm i --save-dev webpack-dev-server编译静态文件 打开浏览器等
const path =require('path');
配置 extract-text-webpack-plugin
npm i extract-text-webpack-plugin -S
html-webpack-plugin 为了引入css样式
热更新 为了防闪
const webpack = require('webpack');
if(module.hot){
    module.hot.accept()
}
devServer: {
        port: 3000,
        open: true,
        hot: true 
    },
      plugins:[
        new HTML({
            title:'首页',
            filename:'index.html',
            template:'./index.html'
        }),//加上可以出来css样式
        new webpack.HotModuleReplacementPlugin(),//加热更新是为了防闪
    ]


