## 一 环境配置
     win10 + 虚拟机VMWare + ubuntu 16.03 LTS  
     android的编译必须要在linux 64位操作系统下

## 二 基础软件安装
    安装git就行：sudo apt-get install git

## 三 下载webrtc android 源码
```
1 准备好VPN或者自己搭建VPS，本人用的是VyprVPN
2 下载 depot_tools：git clone https://chromium.googlesource.com/chromium/tools/depot_tools.git
3 配置depot_tools环境变量：export PATH=/home/用户名/depot_tools:$PATH ，
4 下载源码：先创建一个目录比如webrtc，用于存放源码：mkdir webrtc 切换到webrtc目录下：cd webrtc 现在当前目录到了webrtc下，然后执行：
	fetch --nohooks webrtc_android
	gclient sync
```
## 四 配置环境
```
1 切换到src目录：
   cd src
2 安装编译需要的软件及配置：执行下面指令时建议关闭vpn会比较快
   /build/install-build-deps-android.sh（中途会出现安装ttf-xxx-xxx的授权界面，用tab键选中ok，点回车就行），
3 建立关联：gclient runhooks
4 配置环境变量：. build/android/envsetup.sh
```
## 五 编译源码
     1 创建工程：gn gen out/Debug --args='target_os="android" target_cpu="arm"'
     2 编辑工程：ninja -C out/Debug


详细说明请参考官网：https://webrtc.org/native-code/android


## Q&A

1、虚拟机如何全屏拉伸？</br>
A：虚拟机（M）-》安装VMware tool，安装完成后查看（v）-》自动调整大小-》拉伸客户机

2、虚拟机与主机间互传文件？</br>
A：主机下载安装FileZilla软件，获取虚拟机ip（虚拟机命令行ifconfig），输入主机，账号，密码（系统登陆账号名和密码）
   虚拟机命令行输入sudo apt-get install openssh-server安装ssh server
   FileZilla中点击连接即可以查看虚拟机中的文件
   
3、如何更新代码？</br>
A：进入webrtc/src目录，命令行git fetch，然后gclient sync
