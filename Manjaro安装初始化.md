 
>Manjaro的安装使用过程，使用manjaro的18.1.5 stable版本
>注意:所有的安装都不要在root用户下,在登录用户下即可

### 准备工作
列出中国区镜像
```
sudo pacman-mirrors -i -c China -m rank
```

编辑`/etc/pacman.conf`文件，末尾添加
```
# 添加清华源（假设上面选的是清华源）
[archlinuxcn]
SigLevel= TrustedOnly
Server = https://mirrors.tuna.tsinghua.edu.cn/archlinuxcn/$arch
```
添加archlinux源
```
sudo pacman -Sy archlinuxcn-keyring haveged
sudo systemctl enable haveged
sudo systemctl start haveged
sudo pacman-key --init
sudo pacman-key --populate manjaro
sudo pacman-key --populate archlinux
sudo pacman-key --populate archlinuxcn
```
更新软件包源
```
sudo pacman -Syyu
```
包管理：安装yay
```
pacman -S yay
```

支持dep格式软件安装
```
step1、检查有没有安装 ``debtap

sudo pacman -Q debtap

没有就安装:yay -S debtap

step2、 升级debtap

sudo debtap -u

使用方法

sudo debtap xxxx.deb

安装时会提示输入包名，以及license。包名随意，license就填GPL吧

上述操作完成后会在deb包同级目录生成×.tar.xz文件，直接用pacman安装即可

sudo pacman -U x.tar.xz 
```

包管理：使用snap

```
sudo pacman -S snapd
sudo systemctl enable --now snapd.socket
sudo ln -s /var/lib/snapd/snap /snap
```

### 常用软件安装

1 wine
[参考文章](https://blog.csdn.net/zbgjhy88/article/details/85110956)

安装管理wine dll的工具
sudo pacman -S winetricks

打开wine的配置
winecfg

安装genmon工具，部分wine程序用到

安装gnome-settings-daemon：sudo pacman -S gnome-settings-daemon

设置gnome-settings-daemon自启动：
sudo  cp  /etc/xdg/autostart/org.gnome.SettingsDaemon.XSettings.desktop   ~/.config/autostart

sudo cp gsd-xsettings  ~/.config/autostart

```
1 playonlinux

```
管理wine软件的小工具
pacman -S playonlinux
```

1 输入法
[参考文章](https://zhuanlan.zhihu.com/p/80867772)

2 网易云音乐
```
sudo pacman -S netease-cloud-music
```
3 微信
```
yay -S deepin-wine-wechat

tim:

yay -S deepin-wine-tim
qq:


```

4 钉钉

[参考文章](https://looknews.cc/zh-my/keji/304229.html)
[linux版内测版](https://www.52pojie.cn/thread-1013773-1-1.html)
Deb包下载地址:
链接:https://pan.baidu.com/s/1LuDlmZBJvYYWhBBJVsYqhQ       提取码: 2dgg


5 docker
```
 Pacman 安装 Docker

sudo pacman -S docker

 启动docker服务

sudo systemctl start docker 

 查看docker服务的状态

sudo systemctl status docker

 设置docker开机启动服务

sudo systemctl enable docker
```

6 vpn


sudo pacman -S wine wine_gecko wine-mono
```

8 deep-wine

```
yay deepin-wine
```

9 webStorm

```
sudo snap install webstorm --classic
```
10 phpStorm

```
sudo snap install phpstorm --classic
```

11 golang
```
sudo pacman -S go liteide
vim ~/.profile
# set go environment
export GOROOT=/usr/lib/go
export PATH=$PATH:$GOROOT/bin
export GOPATH=$HOME/go
```