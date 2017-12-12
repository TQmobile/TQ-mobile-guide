## 一 环境配置
     win10 + 虚拟机VMWare + ubuntu 16.03 LTS  
     android的编译必须要在linux下

## 二 基础软件安装
    安装git就行：sudo apt-get install git

## 三 下载webrtc android 源码
     1 准备好VPN或者自己搭建VPS，本人用的是VyprVPN
     2 下载 depot_tools：git clone https://chromium.googlesource.com/chromium/tools/depot_tools.git
     3 配置depot_tools环境变量：export PATH=/home/用户名/depot_tools:$PATH ，
     4 下载源码：先创建一个目录比如webrtc，用于存放源码：mkdir webrtc 切换到webrtc目录下：cd webrtc 现在当前目录到了webrtc下，然后执行：
	fetch --nohooks webrtc_android
	gclient sync
     5 切换到src目录：cd src
     6 安装编译需要的软件及配置 ：执行下面指令时建议关闭vpn会比较快
     	/build/install-build-deps.sh
     	/build/install-build-deps-android.sh（中途会出现安装ttf-xxx-xxx的授权界面，用tab键选中ok，点回车就行）
     7 建立关联：gclient runhooks
     8 配置环境变量：. build/android/envsetup.sh
## 四 编译源码
     1 创建工程：gn gen out/Debug --args='target_os="android" target_cpu="arm"'
     2 编辑工程：ninja -C out/Debug


详细说明请参考官网：https://webrtc.org/native-code/android
