# Ubuntu 2024 安装 Flutter

## 安装依赖

文档地址

```
https://docs.flutter.cn/get-started/install/linux/android#development-tools
```

Ubuntu 依赖

```bash
sudo apt-get update -y && sudo apt-get upgrade -y;
sudo apt-get install -y curl git unzip xz-utils zip libglu1-mesa
```

要开发Android应用，为Android Studio安装以下必备软件包。

```bash
sudo apt-get install \
    libc6:amd64 libstdc++6:amd64 \
    libbz2-1.0:amd64 libncurses5:amd64
```

## 安装 JDK

Flutter 至少需要 jdk > 8, 这里选择 jdk 11

JDK 清华大学镜像下载地址

```
https://mirrors.tuna.tsinghua.edu.cn/Adoptium/11/jdk/x64/linux/
```

进入 JDK 安装包下载目录, (我这里将软件下载到 ~/Downloads 目录)

```bash
cd ~/Downloads
```

解压 flutter_linux_3.22.3-stable.tar.xz 文件，得到 flutter 目录

```bash
tar -xvf OpenJDK11U-jdk_x64_linux_hotspot_11.0.24_8.tar.gz
```

将 jdk 目录复制到 /opt 目录 , 个人习惯将软件安装在 /opt 目录

```bash
sudo mv jdk-11.0.24+8 /opt/jdk11
```

## 配置 JDK

有的软件需要 JDK8

有的软件需要JDK11,

为了放置 JDK 环境变量冲突，此处不配置用户环境变量

选择在项目配置文件中配置 JDK 版本

## 安装 Android Studio

推荐使用 ToolBox 安装 Android Studio

```

```

## 配置 ADB

修改用户环境变量文件

```bash
vim ~/.bashrc
```

在文件 .bashrc 末尾添加以下内容， 然后保存、退出文件编辑

```
# adb
export PATH=$PATH:~/Android/Sdk/platform-tools
```

使用以下命令， 生效环境变量

```bash
source ~/.bashrc
```

使用以下命令，可以打印 adb 命令的版本信息， 检查 adb 是否配置成功

```bash
adb version
```

adb version 命令的输入内容如下

```
Android Debug Bridge version 1.0.41
Version 35.0.1-11580240
Installed as /home/demodeom/Android/Sdk/platform-tools/adb
Running on Linux 6.8.0-39-generic (x86_64)
```



## 下载 Flutter

文档地址

```
https://docs.flutter.cn/get-started/install/linux/android#install-the-flutter-sdk
```

Flutter 清华大学镜像下载地址

```
https://mirrors.tuna.tsinghua.edu.cn/flutter/flutter_infra/releases/stable/
```

## 安装 Flutter

进入 Flutter 安装包下载目录, (我这里将软件下载到 ~/Downloads 目录)

```bash
cd ~/Downloads
```

解压 flutter_linux_3.22.3-stable.tar.xz 文件，得到 flutter 目录

```bash
tar -xvf flutter_linux_3.22.3-stable.tar.xz
```

将 flutter 文件复制到 /opt 目录 , 个人习惯将软件安装在 /opt 目录

```bash
sudo mv flutter /opt
```

## 配置 Flutter

修改用户环境变量文件

```bash
vim ~/.bashrc
```

在文件 .bashrc 末尾添加以下内容， 然后保存、退出文件编辑

```
# flutter
export PATH=$PATH:/opt/flutter/bin
```

使用以下命令， 生效环境变量

```bash
source ~/.bashrc
```

使用以下命令，可以打印 flutter 命令的版本信息， 检查 flutter 是否配置成功

```bash
flutter -v
```

flutter -v 命令的输入内容如下

```
Manage your Flutter app development.

Common commands:

  flutter create <output directory>
    Create a new Flutter project in the specified directory.

  flutter run [options]
    Run your Flutter application on an attached device or in an emulator.

Usage: flutter <command> [arguments]

Global options:
-h, --help                      Print this usage information
此处省略
```

## 配置 Flutter 镜像

Flutter 开发依赖于 SDK 的升级 和 Dart Package 生态， 因此，如果您的网络访问 Google 受阻，需要将您开发设备的如下两个环境变量设置指向 TUNA 镜像站：

- `PUB_HOSTED_URL`
- `FLUTTER_STORAGE_BASE_URL`

修改用户环境变量文件

```bash
vim ~/.bashrc
```

在文件 .bashrc 末尾添加以下内容， 然后保存、退出文件编辑

```
# flutter tsinghua mirror
export FLUTTER_STORAGE_BASE_URL="https://mirrors.tuna.tsinghua.edu.cn/flutter"
export PUB_HOSTED_URL="https://mirrors.tuna.tsinghua.edu.cn/dart-pub"
```

使用以下命令， 生效环境变量

```bash
source ~/.bashrc
```

通过以下命令，检查镜像相关的变量是否配置成功

```
echo $FLUTTER_STORAGE_BASE_URL
```

假如配置成功，会输出以下内容

```
https://mirrors.tuna.tsinghua.edu.cn/flutter
```



## 检查 Flutter 环境

使用以下命令， 检查 flutter 环境是否正常

```
flutter doctor
```

### 错误 cmdline

错误信息如下

```
✗ cmdline-tools component is missing
      Run `path/to/sdkmanager --install "cmdline-tools;latest"`
      See https://developer.android.com/studio/command-line for more details.
```

使用 android studio 安装 sdkmanager

### 错误 android licenses

```
✗ Android license status unknown.
      Run `flutter doctor --android-licenses` to accept the SDK licenses.
      See https://flutter.dev/docs/get-started/install/linux#android-setup for more details.
```

使用以下命令， 解决上述错误

```
flutter doctor --android-licenses
```

看到类似以下的提示， 一律输入 y , 然后回车

```
Review licenses that have not been accepted (y/N)? 
```

看到类似以下的提示， 一律输入 y , 然后回车

```
Accept? (y/N):
```

### 错误 Linux Dekstop

完整错误信息如下

```
[✗] Linux toolchain - develop for Linux desktop
    ✗ clang++ is required for Linux development.
      It is likely available from your distribution (e.g.: apt install clang), or can be downloaded from https://releases.llvm.org/
    ✗ CMake is required for Linux development.
      It is likely available from your distribution (e.g.: apt install cmake), or can be downloaded from https://cmake.org/download/
    ✗ ninja is required for Linux development.
      It is likely available from your distribution (e.g.: apt install ninja-build), or can be downloaded from
      https://github.com/ninja-build/ninja/releases
    ✗ GTK 3.0 development libraries are required for Linux development.
      They are likely available from your distribution (e.g.: apt install libgtk-3-dev)
```

使用以下命令， 解决上述错误

```bash
sudo apt install clang cmake libgtk-3-dev ninja-build -y
```



### Flutter 环境配置正确

```
flutter doctor
```

假如环境配置正确， 上述命令输出如下

```
Doctor summary (to see all details, run flutter doctor -v):
[✓] Flutter (Channel stable, 3.22.3, on Ubuntu 24.04 LTS 6.8.0-39-generic, locale zh_CN.UTF-8)
[✓] Android toolchain - develop for Android devices (Android SDK version 35.0.0)
[✓] Chrome - develop for the web
[✓] Linux toolchain - develop for Linux desktop
[✓] Android Studio (version 2024.1)
[✓] Connected device (2 available)
[✓] Network resources

• No issues found!
```



## 