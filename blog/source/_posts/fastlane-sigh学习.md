title: fastlane-sigh学习
date: 2015-12-08 16:14:15
categories: 技术
tags: [fastlane,sigh,技术]
---

### 概念
sigh是用命令行创建、更新、下载、修复provisioning profiles的工具，支持AppStore、AdHoc。团队开发的时候可以结合jenkins实现provisioning profiles的自动化拉取、分发。

### 安装

```
sudo gem install sigh
```
确保你有最新版本的Xcode command line tools。

```
xcode-select --install
```

### 用法
获取本地provisioning profiles的信息。

```
sigh manage
```
删除所有失效的provisioning profiles

```
sigh manage -e
```

验证appleID和apple账户名，获取provisioning profiles，如果没有这个证书，会创建一个可用的。

下载的路径为当前路径目录下，所以你可以切换存放路径。

```
sigh -a com.krausefx.app -u username

```
获取证书，并命名为myProfile.mobileprovision。

```
sigh -a com.krausefx.app -u username -q "myProfile.mobileprovision"
```

后面可以增加参数：
--skip_install  不自动载入provisioning profiles。


### 参考
[sigh官方文档](https://github.com/fastlane/fastlane/tree/master/sigh#readme)




