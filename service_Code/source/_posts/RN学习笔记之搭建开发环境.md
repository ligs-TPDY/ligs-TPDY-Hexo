---
title: RN学习笔记之搭建开发环境
date: 2019-06-04 15:42:43
tags: RN
---

###### 一般准备学习一项新技术，必须要先折腾一遍开发环境。

##### 安装依赖
###### 必须安装的依赖有：Node、Watchman 和 React Native 命令行工具以及 Xcode。虽然你可以使用任何编辑器来开发应用（编写 js 代码），但你仍然必须安装 Xcode 来获得编译 iOS 应用所需的工具和环境。

##### Node, Watchman
###### 我们推荐使用Homebrew来安装 Node 和 Watchman。在命令行中执行下列命令安装：
    brew install node
    brew install watchman
###### 如果你已经安装了 Node，请检查其版本是否在 v10 以上。安装完 Node 后建议设置 npm 镜像以加速后面的过程（或使用科学上网工具）。
    sudo npm config set registry https://registry.npm.taobao.org --global
    sudo npm config set disturl https://npm.taobao.org/dist --global
    
###### Watchman则是由 Facebook 提供的监视文件系统变更的工具。安装此工具可以提高开发时的性能（packager 可以快速捕捉文件的变化从而实现实时刷新）。



##### Yarn、React Native 的命令行工具（react-native-cli）
###### Yarn是 Facebook 提供的替代 npm 的工具，可以加速 node 模块的下载。React Native 的命令行工具用于执行创建、初始化、更新项目、运行打包服务（packager）等任务。

    sudo npm install -g yarn react-native-cli
    
###### 安装完 yarn 后同理也要设置镜像源：

    sudo yarn config set registry https://registry.npm.taobao.org --global
    sudo yarn config set disturl https://npm.taobao.org/dist --global
    
###### 安装完 yarn 之后就可以用 yarn 代替 npm 了，例如用yarn代替npm install命令，用yarn add 某第三方库名代替npm install 某第三方库名。


##### Xcode

###### React Native 目前需要Xcode 9.4 或更高版本。你可以通过 App Store 或是到Apple 开发者官网上下载。这一步骤会同时安装 Xcode IDE、Xcode 的命令行工具和 iOS 模拟器。

###### Xcode 的命令行工具

###### 启动 Xcode，并在Xcode | Preferences | Locations菜单中检查一下是否装有某个版本的Command Line Tools。Xcode 的命令行工具中包含一些必须的工具，比如git等。

    
##### 创建新项目

###### 使用 React Native 命令行工具来创建一个名为"AwesomeProject"的新项目：

    
###### ！！！注意！！！：init 命令默认会创建最新的版本，而目前最新的 0.45 及以上版本需要下载 boost 等几个第三方库编译。这些库在国内即便翻墙也很难下载成功，导致很多人无法运行iOS项目！！！中文网在论坛中提供了这些库的国内下载链接。如果你嫌麻烦，又没有对新版本的需求，那么可以暂时创建0.44.3的版本。

    sudo react-native init AwesomeProject

##### 提示：你可以使用--version参数（注意是两个杠）创建指定版本的项目。例如sudo react-native init MyApp --version 0.44.3。注意版本号必须精确到两个小数点。


##### 编译并运行 React Native 应用
###### 在你的项目目录中运行react-native run-ios：

    cd AwesomeProject
    sudo react-native run-ios
