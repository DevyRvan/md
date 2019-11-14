# cordova + Vue 开发 APP 上手指南
## 什么是 cordova
cordova 是由 Apache 基金会支持的，使用 HTML5 + CSS3 + JS 来构建多平台 APP 程序的开发框架。其支持调用手机系统（Android、IOS、Windows phone）原生 API，它可以将你写的 Web 程序包裹进原生的 APP 壳中，也就是我们常说的 Hybrid APP （混合应用）。本文是一个前端开发者如何从 0 开始结合 Vue 来构建一个简单的 APP.

第一步，安装 cordova

## 安装 cordova
cordova 提供一个可以全局安装的脚手架工具，我们使用 npm 来安装，你的电脑还没有 npm 的话，需要先安装 node，node 本身自带 npm 包管理器，安装好 node 之后，我们打开命令行程序，输入以下命令，全局安装 cordova：

> npm install -g cordova

下载完之后，输入 cordova -v 查看是否成功安装，出现相应的版本号则成功安装。

## 创建 cordova 程序
安装好之后，我们来新建一个 cordova 应用，在命令行输入以下命令新建：

> cordova create learn-cordova

其中，我们重点关注 www 和 platforms 目录，我们写的 HTML/CSS/JS 代码就放在这个目录下面，现在这个目录下面已经有 cordova 为我们提供的示例项目代码。

platforms 是用来存放我们为相应的系统平台打包的运行源码，它现在是空的，我们依次执行以下命令来添加相应的平台：

```
cordova platform add android --save

cordova platform add ios --save

cordova platform add browser --save
```

添加完成之后，我们可以在 platforms 文件夹下面看到 android 和 ios 文件夹。我们可以使用下面这行命令来查看我们已经添加的平台和可以添加的全部平台：

> cordova platform

添加完平台之后，我们可以使用 cordova run < platform > 来运行相应平台的代码，作为前端开发者，我们可以首先在浏览器里面跑起来我们的项目：cordova run browser （前提是你前面添加了 browser 平台），默认情况下，它会在 8000 端口打开项目：

如果你想查看它在安卓平台下的效果，则需要安装配置 Android SDK 环境，包括 Java JDK 的安装和环境变量配置， Android SDK 的安装和环境变量配置。这个过程可以通过 Android studio 来更高效地安装配置，当然，如果你的项目不涉及调用原生 API 的话，则可以直接下载 SDK Manager 管理工具来下载，进去依次点击 "Android SDK 工具"，在下拉菜单中选择 "SDK Tools"， 然后在表格中选择相应的平台所需的 SDK 包，建议直接下载 zip，下载完之后，在环境变量中配置（具体过程可以百度，很简单）。

配置完成之后，在刚下载好的 SDK manager 中打开 SDK Manager.exe 文件，在打开的界面中下载相应 API 级别的 SDK （推荐安装 Android 8.0 级别）就可以了，其中 Tools 下面的前三项必须安装，需要注意的是，这些 SDK 都比较大，准备好硬盘空间。

一切环境配置好之后，就可以通过 cordova run android 来调试你的应用在 Android 系统下的表现了。

当然，你想打包出来 apk 可安装文件的话，也可以通过一行命令解决：

> cordova build android

打包成功之后的安装包可以在 "platforms → android → app → build → outputs → apk → debug" 下面找到。

以上就是一个简单 APP 的打包过程。

## 如何打包 Vue 项目
把打包后的文件放在www 项目之下

我们回到 cordova 项目目录，在其下执行 cordova build <platform name> 就可以打包出 vue 项目了。

以上就是使用 cordova 项目构建 APP 的基本过程，当然使用 cordova 的原因在于我们可以通过添加插件来拥有 Web 开发不曾拥有的原生功能体验，这些，通过学习多多尝试。