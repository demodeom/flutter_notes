# Flutter 快速开始一个项目

以 Android 为例

## 创建项目

创建目录， 存放所有项目 （个人习惯）

```bash
mkdir ~/flutter_project
```

切换到 flutter_project 目录

```bash
cd ~/flutter_project
```

创建 flutter 项目， 项目名 flutter_example_1

```bash
flutter create flutter_example_1
```

假如项目创建成功， 上述命令输入如下

```
Creating project flutter_example_1...
Resolving dependencies in `flutter_example_1`... (1.1s)
Downloading packages... (1.2s)
Got dependencies in `flutter_example_1`.
Wrote 129 files.

All done!
You can find general documentation for Flutter at: https://docs.flutter.dev/
Detailed API documentation is available at: https://api.flutter.dev/
If you prefer video documentation, consider: https://www.youtube.com/c/flutterdev

In order to run your application, type:

  $ cd flutter_example_1
  $ flutter run

Your application code is in flutter_example_1/lib/main.dart.
```

## IDE 导入项目

使用 Android Studio 打开项目目录 flutter_example_1 

注意！注意！注意！ 

不是 flutter_project ！不是 flutter_project ！不是 flutter_project ！

打开 flutter_example_1 目录！打开 flutter_example_1 目录！打开 flutter_example_1 目录！







## 修改文件

### 配置 gradle 下载镜像

修改文件  

```
android/gradle/wrapper/gradle-wrapper.properties
```

将 

```
https\://services.gradle.org/distributions
```

替换为

```
https\://mirrors.cloud.tencent.com/gradle
```

### 配置 flutter 镜像

修改文件

```

```



##  编译

哎 ！！！ 国内 flutter 镜像， 一言难进！！！

有的包使用了配置的镜像，有的包没有使用到镜像，仍然 20 kb/s 的下载速度，暂时未找到原因

算了！算了！算了！直接上**魔法**， Linux 需要开启 **tun 模式**， 开启**系统代理**

以 Android 为例

```bash
cd flutter_example_1/android
./gradlew build
```

编译后， apk 文件生成目录

```
flutter_example_1/build/app/outputs/apk/release/app-release.apk
```





