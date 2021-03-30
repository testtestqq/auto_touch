# 手机端自动触摸工具

## 准备工作 + 读书APP自动翻页教程
### iOS
#### 工具
* Mac
* Xcode
* Python3、pip3

#### 安装WebDriverAgent
1. git clone https://github.com/facebook/WebDriverAgent.git
2. ./Scripts/bootstrap.sh
3. 打开`WebDriverAgent.xcodeproj`，在Xcode中设置好开发者apple id
4. 在Xcode中，Product -> **Test**，在手机上运行，在手机上打开一下刚安装的没有图标的WebDriverAgent，会自动关闭，然后在Xcode控制台会输出ServerURL: http://x.x.x.x:8100
5. brew install imobiledevice
6. iproxy 8100 8100
7. 浏览器访问`http://localhost:8100/status`看到json就说明运行成功

#### 安装python-wda
```
pip3 install --pre facebook-wda
```

#### 执行
以微信读书为例。在微信读书中打开一本书，然后终端执行：

```
git clone https://github.com/huowenxuan/auto_touch
cd auto_touch
python3 read_ios.py
```

### Android
### 工具
* Python3、pip3

### 电脑安装uiautomator2
```
pip3 install -U uiautomator2
```

### 执行

##### 1.设备打开usb调试
设置-关于手机，连续点击内核版本，开启开发者模式。开启后返回上层，进入其他设置-开发者选项，打开usb调试。

##### 2.adb连接电脑和设备
安装adb驱动；
可使用数据线连接，也可通过wifi使用无线adb
##### 3.通过电脑给手机安装atx-agent

①下载附件 https://wwe.lanzous.com/i6xMekeyf5i

②解压后打开位于当前文件夹的命令行窗口（即双击进入该文件夹，按住键盘shift+鼠标右键，打开命令行窗口）

③复制粘贴命令并按回车执行，每次执行1行

adb push atx-agent /data/local/tmp
adb shell chmod 755 /data/local/tmp/atx-agent
adb shell /data/local/tmp/atx-agent server -d
adb shell /data/local/tmp/atx-agent server -d --stop

##### 4.设备打开阅读界面，做好准备

##### 5.开启脚本，自动翻页
电脑的命令行窗口，先后执行以下三行代码

git clone https://github.com/huowenxuan/auto_touch
cd auto_touch
python3 read_android.py


#### 下面是注释，待调试。

```
git clone https://github.com/huowenxuan/auto_touch
cd auto_touch
```

如果通过USB控制，需要进入开发者选项，打开USB调试，执行：

```
python3 read_android.py
```

如果想通过WIFI控制，电脑和手机连接同一WIFI，先连接USB，执行上一步，让手机开启ATX服务后，关闭命令行，拔掉USB，再执行下面的命令。文件名后添加手机的ip地址

```
python3 read_android.py x.x.x.x
```

## 趣头条小视频自动上拉（仅限android）
打开趣头条app，点击小视频tab，执行：

```
python3 qutoutiao_android.py
```
