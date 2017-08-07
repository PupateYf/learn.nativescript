# nativescript入坑指北
NativeScript官网:[https://www.nativescript.org](https://www.nativescript.org)

目前只踩了mac的坑
### 安装

首先默认各位都装好了[node](https://nodejs.org/)...也默认各位装好了[HomeBrew](http://brew.sh/)...

接下来开始正题，先安装ns的cli工具
```bash
$ npm install -g nativescript
```
如果这里出现了`Permission denied`的错误，请在开头加上`sudo`。

安装完成后可以运行下面的命令
```bash
$ tns

或

$ nativescript
```
当出现如下信息，表示已经安装成功
```bash
┌─────────┬─────────────────────────────────────────────────────────────────────┐
│ Usage   │ Synopsis                                                            │
│ General │ $ tns <Command> [Command Parameters] [--command <Options>]          │
│ Alias   │ $ nativescript <Command> [Command Parameters] [--command <Options>] │
└─────────┴─────────────────────────────────────────────────────────────────────┘
```
安装完ns的脚手架，因为我们写的是原生应用，所以ios开发相关的工具也要一并装上。首先装个XCode,这个可以在App Store里安装。

从[https://developer.apple.com/downloads/index.action](https://developer.apple.com/downloads/index.action)下载Command Line Tools for Xcode并安装(如果有通过terminal使用git基本都装过的了)

接着运行如下命令，安装`xcodeproj`
```bash
$ sudo gem install xcodeproj
```

接着安装`CocoaPods`
```bash
$ sudo gem install cocoapods
```

同样的，安卓方面，也需要安装一系列的工具...

首先去装个[JDK8](http://www.oracle.com/technetwork/java/javase/downloads/index.html)，进去在 Java SE Development Kit里勾选同意，下载macos专用的版本，安装好后将`export JAVA_HOME=$(/usr/libexec/java_home)`添加到系统环境变量中:
```bash
$ cd ~
$ touch .bash_profile
$ vim .bash_profile
# 将export JAVA_HOME=$(/usr/libexec/java_home)追加到文件中
```
接着安装android sdk
```bash
$ brew cask install android-sdk
```
如无意外这里会报个错的: ) `Error: Unknown command: cask`，这里有官方[解决办法](https://github.com/caskroom/homebrew-cask/blob/master/doc/reporting_bugs/error_unknown_command_cask.md)，其实就是运行下面这行命令：
```bash
$ cd $(brew --repo); git fetch; git reset --hard origin/master; brew update
```
同样的，在安装完android-sdk后，将`export ANDROID_HOME=/usr/local/share/android-sdk`添加到`~/.bash_profile`中

接着，运行下面这个命令，安装所有安卓所需的依赖包
```bash
$ $ANDROID_HOME/tools/bin/sdkmanager "tools" "platform-tools" "platforms;android-25" "build-tools;25.0.2" "extras;android;m2repository" "extras;google;m2repository"
```
注意，这里也有点坑，最好你的电脑能科(fan)学(qiang)上网，鄙人用的是4g搭配正确的科学姿势跑完的

然后

*这里占个坑，android的模拟器还要装个Android Studio后补,并不影响接下来的操作*


最后运行
```
$ tns doctor
```
这里就如它的提示一样，be patient..反正就是有点久，建议将npm源改为taobao或者cnpm`(推荐使用nrm管理)`这样安装的过程会舒爽很多。

当最后出现`'No issues were detected.'`，那么恭喜你，环境终于搭好了
