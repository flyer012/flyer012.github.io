title: Mac+github+Hexo搭建博客指南
date: 2015-12-08 16:14:15
categories: 其他
tags: [Hexo,技术]
---
开始不明白觉得好麻烦，一路踩坑，最后发现其实也蛮简单的！

## 程序安装
需要安装3个东西 nodejs、git、hexo
### 安装nodejs
 hexo是基于nodejs的,所以先从这个开始。
 
[点击下载](https://nodejs.org/en/)

![](http://7xp069.com1.z0.glb.clouddn.com/201512080001.jpg)


下载并安装nodejs.安装完成可以使用命令行查看是否安装成功

``` 
node -v
npm -v
```

![](http://7xp069.com1.z0.glb.clouddn.com/201512080002.jpg)



### 安装git
hexo提交部署github需要使用git工具，到git官网下载安装包吧！

[点击下载](http://git-scm.com/download/) 并安装。

![](http://7xp069.com1.z0.glb.clouddn.com/201512080003.jpg)

### 安装hexo
使用命令行：

```
sudo npm install hexo-cli -g
```

如果安装不报错，那么安装文件就算是完成了！


## 开始bolg之旅
### 创建blog
创建bolg很简单哦，只需要下列命令行。

cd到你需要创建的目录下：

```
hexo init blog  #创建一个blog名称为blog
cd blog    ＃进入blog目录
npm install    ＃载入npm   报错了请查看是否进入到blog目录里
```

![](http://7xp069.com1.z0.glb.clouddn.com/201512080004.jpg)

### 编辑并生成可发布文件

操作请到cd到项目里面执行

```
hexo clean    ＃清理之前编译
hexo generate    ＃生成编译
hexo server    #本地部署启动服务器 打开浏览器http://localhost:4000查看
hexo deploy    ＃生成部署文件，可放到git服务端
```

### 将项目发布到git
如何创建git仓库，请自己查找，网上很多。

到github新建一个项目，项目名为：你的用户名.github.io必须为这个名字

安装： 

```
npm install hexo-deployer-git --save
```

然后，配置文件_config.yml

```
deploy:
  type: github
  repository: git@github.com:你的帐号/你的帐号.github.io.git
  branch: master
```

重新安装上面步骤生成编译文件，生成的文件在 "项目路径/public"，将里面的文件push到git仓库

![](http://7xp069.com1.z0.glb.clouddn.com/201512080005.jpg)

打开你的用户名.github.io就看到你的博客了。

### 写文章

```
hexo new "My New Post"
```

会在blog/source/_posts目录下生成一个markdown文件：My-New-Post.md

可以使用一个支持markdown语法的编辑器（我是使用Mou）来编辑该文件

## 其他

### 更换淘宝源（针对网络不好的童鞋）

```
sudo npm install nrm -g
nrm use taobao
```


### 参考：
[cnfeat.com](http://cnfeat.com/blog/2014/05/10/how-to-build-a-blog/)

[jianshu.com](http://www.jianshu.com/p/465830080ea9)

[错误集锦](https://xuanwo.org/2014/08/14/hexo-usual-problem/)

[markdown样板](https://www.zybuluo.com/mdeditor)

[hexo主题列表](https://github.com/hexojs/hexo/wiki/Themes)

[hexo官网](http://hexo.io)

[markdown使用](http://www.markdown.cn)

[七牛图床说明](http://www.jianshu.com/p/13725d818565)
