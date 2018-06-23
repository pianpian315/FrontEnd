#### 一、 安装 node.js

http://nodejs.cn/

安装完成后，可以命令行工具中输入 node -v 和 npm -v，如果能显示出版本号，就说明安装成功。

#### 二、安装 vue-cli

安装淘宝镜像

npm install -g cnpm --registry=https://registry.npm.taobao.org

安装vue脚手架
cnpm install -g vue-cli

#### 三、生成项目

创建项目

vue init webpack Vue-Project

cnpm 安装依赖

cnpm install

启动项目

npm run dev

#### 四、打包上线

npm run build

打包完成后，会生成 dist 文件夹，如果已经修改了文件路径，可以直接打开本地文件查看

项目上线时，只需要将 dist 文件夹放到服务器就行了。



参考文章

https://blog.csdn.net/wisewrong/article/details/55212684
