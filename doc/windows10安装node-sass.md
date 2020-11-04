# 安装node-sass

​	安装node-sass的环境: 

​		操作系统：windows10

​		node版本： 12.19.0

​		npm版本：6.14.8

## 遇到的问题

1. 拉取bieren代码库下来，就在执行npm i 的时候报错，提示没有node-sass，应该就是node-sass安装失败

## google到的解决方法

1. npm源的问题

   安装node-sass中，会去下载一个binding.node的文件，这里是从github上面下，所以可能会下载失败

   ~~~shell
   npm config set registry https://registry.npm.taobao.org/
   ~~~

   

2. 没有装python2

   在上一步如果没有下载成功，就会尝试在本地编译出该文件，这里就需要python和其他编译环境

   > 管理员身份执行

   ~~~shell
   #这一句用来安装
   npm install --global --production windows-build-tools
   npm install node-gyp --global
   ~~~

> 每次安装失败后，要把node_modules删了，还有如果安装某个库失败了，最好也先uninstall了后再重装。

安装分为全局安装和当前目录安装，在卸载module的时候要卸载干净