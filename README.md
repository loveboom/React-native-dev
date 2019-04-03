# React Native环境搭建（win10-andriod）

<a name="941fcb2b"></a>
### 准备工作：

```git
// 设置npm淘宝镜像
npm config set registry https://registry.npm.taobao.org --global
npm config set disturl https://npm.taobao.org/dist --global
// 安装react-native-cli
npm install -g yarn react-native-cli
// 设置yarn淘宝镜像（可代替npm）
yarn config set registry https://registry.npm.taobao.org --global
yarn config set disturl https://npm.taobao.org/dist --global
```

<a name="50f271e4"></a>
### 1.使用搜索引擎搜索下载 Node 、Python2 和[Java SE Development Kit (JDK)](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)
<a name="975fa198"></a>
#### node需要版本8.3+（命令行查看node -v，已经安装无需再次安装）
<a name="10f797e0"></a>
#### Python只能2.x([https://www.python.org/downloads/](https://www.python.org/downloads/))
<a name="1711babb"></a>
#### Python一路安装到底即可，安装完后环境变量设置：
```javascript
位置：左下角直接搜索编辑环境变量>环境变量
在环境变量Path中添加： C:\Python27
在环境变量Path再加一行： C:\Python27\Scripts
```
<a name="d41d8cd9"></a>
#### 
<a name="2179196d"></a>
#### java sdk安装：
例:我这里jdk和jre分别安装在这两个目录下：

![image.png](https://cdn.nlark.com/yuque/0/2019/png/250109/1554103501880-1069b8d5-f20a-4f1a-83ca-6d3124aaebb0.png#align=left&display=inline&height=416&name=image.png&originHeight=385&originWidth=654&size=46915&status=done&width=707)<br />
![image.png](https://cdn.nlark.com/yuque/0/2019/png/250109/1554103529699-cc033ae2-9c9b-4151-94a5-c17c9df08f89.png#align=left&display=inline&height=451&name=image.png&originHeight=403&originWidth=625&size=37456&status=done&width=699)

安装完后需要配置环境变量：
```
1.新增系统变量名为JAVA_HOME, 值为 D:\android\java
2.新增系统变量名为CLASSPATH, 值为 %JAVA_HOME%\lib
3.编辑系统变量Path, 新增一条值为 %JAVA_HOME%\bin
重新打开cmd, 输入 java -v 测试
输入javac 测试 ，都没问题说明安装完毕
```

<a name="756eeaea"></a>
### 安装andriod studio
<a name="e6bcbf4e"></a>
#### 1.[首先下载和安装 Android Studio](https://developer.android.com/studio/index.html)，国内用户可能无法打开官方链接，请自行使用搜索引擎搜索可用的下载链接。安装界面中选择"Custom"选项，确保选中了以下几项：
* `Android SDK`
* `Android SDK Platform`
* `Performance (Intel ® HAXM)` ([AMD 处理器看这里](https://android-developers.googleblog.com/2018/07/android-emulator-amd-processor-hyper-v.html))
* `Android Virtual Device`

然后点击"Next"来安装选中的组件。
<a name="4dfc2a96"></a>
#### 2.Android Studio 默认会安装最新版本的 Android SDK。目前编译 React Native 应用需要的是Android 9 (Pie)版本的 SDK（注意 SDK 版本不等于终端系统版本，RN 目前支持 android4.1 以上设备）。你可以在 Android Studio 的 SDK Manager 中选择安装各版本的 SDK。
你可以在 Android Studio 的欢迎界面中找到 SDK Manager。点击"Configure"，然后就能看到"SDK Manager"。<br />                      ![](https://cdn.nlark.com/yuque/0/2019/png/250109/1554130568089-0ddfb86f-7e9c-4515-933a-5be6ceb2ec09.png#align=left&display=inline&height=346&originHeight=346&originWidth=500&size=0&status=done&width=500)<br />在 SDK Manager 中选择"SDK Platforms"选项卡，然后在右下角勾选"Show Package Details"。展开Android 9 (Pie)选项，确保勾选了下面这些组件（重申你必须使用稳定的翻墙工具，否则可能都看不到这个界面）：<br />Android SDK Platform 28<br />Intel x86 Atom_64 System Image（官方模拟器镜像文件，使用非官方模拟器不需要安装此组件）<br />然后点击"SDK Tools"选项卡，同样勾中右下角的"Show Package Details"。展开"Android SDK Build-Tools"选项，确保选中了 React Native 所必须的28.0.3版本。你可以同时安装多个其他版本。<br />最后点击"Apply"来下载和安装这些组件。
<a name="e84d2a34"></a>
#### 3.配置 ANDROID_HOME 环境变量
打开控制面板 -> 系统和安全 -> 系统 -> 高级系统设置 -> 高级 -> 环境变量 -> 新建，创建一个名为ANDROID_HOME的环境变量（系统或用户变量均可），指向你的 Android SDK 所在的目录<br />![](https://cdn.nlark.com/yuque/0/2019/png/250109/1554130715936-ea698340-4e60-48c9-a240-4b292b0e870f.png#align=left&display=inline&height=165&originHeight=165&originWidth=653&size=0&status=done&width=653)<br />SDK 默认是安装在下面的目录：
```
c:\Users\你的用户名\AppData\Local\Android\Sdk
```
你可以在 Android Studio 的"Preferences"菜单中查看 SDK 的真实路径，具体是Appearance & Behavior → System Settings → Android SDK。<br />你需要关闭现有的命令符提示窗口然后重新打开，这样新的环境变量才能生效。
<a name="184d0f3c"></a>
#### 4. 把 platform-tools 目录添加到环境变量 Path 中
1. 把 platform-tools 目录添加到环境变量 Path 中<br />
打开控制面板 -> 系统和安全 -> 系统 -> 高级系统设置 -> 高级 -> 环境变量，选中Path变量，然后点击编辑。点击新建然后把 platform-tools 目录路径添加进去。<br />
此目录的默认路径为：<br />
c:\Users\你的用户名\AppData\Local\Android\Sdk\platform-tools
<a name="c9927f4e"></a>
### 创建新项目
```git
react-native init AwesomeProject
cd AwesomeProject
```
提示：你可以使用`--version`参数（注意是`两`个杠）创建指定版本的项目。例如`react-native init MyApp --version 0.44.3`。注意版本号必须精确到两个小数点。
<a name="6ff377b1"></a>
### 安装Android 模拟器
使用 Android Studio 打开项目下的"android"目录，然后可以使用"AVD Manager"来查看可用的虚拟设备，它的图标看起来像下面这样：<br />![](https://cdn.nlark.com/yuque/0/2019/png/250109/1554131947250-9f67488d-8b73-4e70-ad6d-ab234e4d1587.png#align=left&display=inline&height=25&originHeight=25&originWidth=29&size=0&status=done&width=29)<br />如果你刚刚才安装 Android Studio，那么可能需要先[创建一个虚拟设备](https://developer.android.com/studio/run/managing-avds.html)。点击"Create Virtual Device..."，然后选择所需的设备类型并点击"Next"，然后选择Pie API Level 28 image.
<a name="6b29a6e5"></a>
### 启动项目
先打开在android Studio导入项目<br />要导入项目android目录下才有效，如E:\Project\RN\AwesomeProject\android<br />导入完成后静静等它安装需要的依赖<br />随后cmd 在项目目录下执行 react-native run-android


<a name="c92a379a"></a>
# 可能遇到的问题整理：
<a name="7f43280e"></a>
## 1.打包错误Error:error: failed to read PNG signature: file does not start with PNG signature
Error:error: failed to read PNG signature: file does not start with PNG signature.<br />android studio 打包apk时报错.<br />错误：错误：无法读取PNG签名：文件没有从PNG签名开始。<br />一般都是图片格式有问题 可能是后缀更改了，可能是图片压缩时产生的问题。 重新处理图片再加载 <br />解决方法:<br />找到对应的图片,右键编辑下,重新另存为png类型的图片即可.<br />---------------------  
<a name="ae38e98c"></a>
## 2.Error:java.util.concurrent.ExecutionException: com.android.builder.internal.aapt.AaptException解决方案
问题：Error:java.util.concurrent.ExecutionException: com.android.builder.internal.aapt.AaptException:<br />这个问题一般会在打包的时候遇到，查阅了网上很多资料都是说因为项目路径过长原因导致，但是其实很多时候并不是的，其主要原因是builde.gradle会在你打包的时候去检查你的res资源，一旦出现不规范就会出现该错误。<br />以上是问题所在，解决方案：<br />当然解决方案就是我们主动去禁止它检查，即在你Module的builde.gradle中添加以下代码：<br />---------------------  
<a name="0beb831b"></a>
#### 问题1和2都建议先尝试删掉项目重新react-native init <项目名>再用android studio打开重试
```
android{
   .....
   aaptOptions.cruncherEnabled = false
   aaptOptions.useNewCruncher = false
   .....
}
```
<a name="62056667"></a>
## 3.ERROR: x86 emulation currently requires hardware acceleration!
**错误分析：**<br />1.电脑没有安装Intel HAXM软件（HAXM即Hardware Accelerated Execution Manager）（可以参考：[Intel官网的说明](https://software.intel.com/en-us/articles/intel-hardware-accelerated-execution-manager-intel-haxm)）<br />2.电脑没有启用虚拟技术<br />**1.安装Intel HAXM.**<br />一般电脑都是有安装Intel HAXM的，Android SDK中也有继承了这个软件，位置就在你的Sdk安装路径的extras目录下的intel包里<br />![](https://cdn.nlark.com/yuque/0/2019/png/250109/1554136334768-c7d8fb61-d84a-40c4-af48-017b0e1683fb.png#align=left&display=inline&height=227&originHeight=257&originWidth=844&size=0&status=done&width=746)<br />双击intelhaxm-android.exe。或者去官网下载[https://github.com/intel/haxm](https://github.com/intel/haxm)
<a name="c7387e29"></a>
#### 2.确保BIOS中的Configuration(配置)中的Virtual technoly 为Enable(打开)
查看你电脑主板进入Bios的方法，我的是联想的，直接捅一键还原按钮就行了。<br />找到Virtualiation Technology（名字不一定相同，但是一定有Virtual开头），看看是不是默认为Disabled。<br />按Enter，把它改为Enabled。<br />保存设置，重启电脑。<br />---------------------  
<a name="c9d6c6a8"></a>
## 4.如果右上角run按钮是灰色的，点击右边sync project那个按钮就好了![image.png](https://cdn.nlark.com/yuque/0/2019/png/250109/1554217399907-29ada396-c55d-4827-8102-ab59362ae7c1.png#align=left&display=inline&height=27&name=image.png&originHeight=38&originWidth=36&size=736&status=done&width=26)
<a name="d41d8cd9-1"></a>
## 
<a name="e32c97ef"></a>
## 5.unable to load script. make sure you are...
先在项目根目录\android\app\src\main目录下添加空文件夹assets，然后在根目录执行该命令。<br />再sync Project异步更新下代码，最后重新run就好了
```git
react-native bundle --platform android --dev false --entry-file index.js --bundle-output android/app/src/main/assets/index.android.bundle --assets-dest android/app/src/main/res
```
![image.png](https://cdn.nlark.com/yuque/0/2019/png/250109/1554221570160-07ae5a33-d374-4371-963f-42a136da6d18.png#align=left&display=inline&height=91&name=image.png&originHeight=125&originWidth=758&size=19683&status=done&width=551)

<a name="c59a3078"></a>
## 6.Could not connect to development server
模拟器运行时不需要执行 react-native run-android命令 ，如果运行了该命令关掉重试即可。无效的话考虑：出现该问题多半是因为react-native默认的8081端口被占用尝试更换端口。

<a name="1c13bd0b"></a>
## 7.（react-native老版本）
<a name="f920a330"></a>
### Could not find com.android.tools.build:aapt2:3.2.0-alpha14-4748712
在最顶层的build.gradle(project)修改
```javascript
allprojects {
    repositories {
        google() // 新增的
        mavenLocal()
        jcenter()
        maven {
            // All of React Native (JS, Obj-C sources, Android binaries) is installed from npm
            url "$rootDir/../node_modules/react-native/android"
        }
    }
}
```

