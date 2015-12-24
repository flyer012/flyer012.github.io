title: Mac-SublimeText 2 插件使用
date: 2015-12-22 12:00:20
categories: 其他
tags: [技术,SublimeText2,Package control]
---
每次使用Sublime Text 2都会忘记怎么弄，然后又四处查找，浪费时间。今天又浪费了一个多小时，所以，记录下来。

### Package Control 安装
SublimeText 2一般使用package control管理插件，所以，首先安装package control，其他插件用这个就可以安装了！

##### 代码安装
从菜单 View - Show Console 或者 ctrl + ~ 快捷键，调出 console。将以下 Python 代码粘贴进去并 enter 执行，不出意外即完成安装。

以下是Sublime Text 2安装package control代码：

```
import urllib2,os; pf='Package Control.sublime-package'; ipp = sublime.installed_packages_path(); os.makedirs( ipp ) if not os.path.exists(ipp) else None; urllib2.install_opener( urllib2.build_opener( urllib2.ProxyHandler( ))); open( os.path.join( ipp, pf), 'wb' ).write( urllib2.urlopen( 'http://sublime.wbond.net/' +pf.replace( ' ','%20' )).read()); print( 'Please restart Sublime Text to finish installation')
```

##### 手动安装
可能由于各种原因，无法使用代码安装，那可以通过以下步骤手动安装Package Control：

1.点击Preferences > Browse Packages菜单

2.进入打开的目录的上层目录，然后再进入Installed Packages/目录

3.[点击下载](https://github.com/wbond/sublime_package_control) Package Control.sublime-package，并复制到Installed Packages/目录

4.重启Sublime Text。

### 使用方法

每次需要加载插件都需要 Install Package哦！

快捷键 Ctrl+Shift+P（菜单 – Tools – Command Paletter）

输入 install 选中Install Package并回车载入package control.

![](http://7xp069.com1.z0.glb.clouddn.com/201512220001.jpg)

等待加载成功，就变成这样的,你就可以随便查找你需要的插件并安装了。

![](http://7xp069.com1.z0.glb.clouddn.com/201512220002.jpg)

### 常用的插件

##### Emmet
Emmet项目的前身是前端开发人员熟知的Zen Coding（快速编写 HTML/CSS 代码的方案）。

##### DocBlockr
如果你遵循的编码的风格很严格，这款插件能够使你的任务更容易。DocBlokr 帮助你创造你的代码注释，通过解析功能，参数，变量，并且自动添加基本项目。

##### Alignment
这个插件让你能对齐你的代码，包括 PHP、CSS 和 Javascript。代码看起来更简洁和可读，便于编辑。

##### Snippets
Snippets，可以帮你快速书写代码。

##### jquery插件
jquery提示库。