## 系统安装
{: id="20210110110127-fjinus0"}

### 桌面版安装
{: id="20210110110127-cfs5k3r"}

首先是安装 Ubuntu 最新版本，从[官网](https://ubuntu.com/download/desktop)中寻找下载，https://ubuntu.com/download/desktop。
{: id="20210110110127-jhhviiw"}

你也可以从 Ubuntu 的[官方镜像站](http://cloud-images.ubuntu.com/?_ga=2.241655362.1756405896.1609845185-1525960103.1609845185)中寻找自己想要下载的镜像，http://cloud-images.ubuntu.com/?_ga=2.241655362.1756405896.1609845185-1525960103.1609845185。
{: id="20210110110127-p8vgm05"}

目前 20.04 TLS 的 64 位版本 arm 和 x86 都可以使用。
{: id="20210110110127-t4dadmc"}

按照[官网的指示](https://ubuntu.com/tutorials/install-ubuntu-desktop)一步步安装即可，https://ubuntu.com/tutorials/install-ubuntu-desktop 。
{: id="20210110110127-xlf7j0n"}

用 u 盘安装进固态硬盘需要对固态进行分区操作，需要分出 bios 区域(512m)、efi 系统分区(1024m)、swap 分区用于休眠（4G（不休眠）/20G（需休眠））和其他的直接省事 ext4 日志文件系统格式全分配为 `\` 拓展分区。
{: id="20210110110127-01204e8"}

### 服务器安装
{: id="20210110110127-86kh9cb"}

如果只使用命令行模式，则可以下载对于的[服务器版本](https://ubuntu.com/download/server)，https://ubuntu.com/download/server
{: id="20210110110127-a37guiw"}

按照[官方指导](https://ubuntu.com/tutorials/install-ubuntu-server#1-overview)进行安装，https://ubuntu.com/tutorials/install-ubuntu-s#1-overview#
{: id="20210110110127-42umi3c"}

# 常用软件安装
{: id="20210110110236-xwwg3hx"}

### v2ray 相关 vpn 安装
{: id="20210110110259-2td3aba"}

((20210110110411-eb83f2v "ubuntu-安装 v2ray 并配置"))
{: id="20210110112821-7qjisw1"}

### 截图软件安装
{: id="20210121190301-0wu2a3j"}

[flameshot ](https://github.com/flameshot-org/flameshot)是一个很好用的截图软件，并且不断的更新中![flameshotanimatedUsage.gif](assets/flameshot-animatedUsage.gif)
{: id="20210121191906-shnnuq5"}

```
# flameshot 一个支持自定义截图的截屏软件
sudo apt install flameshot
# 执行截图
flameshot gui
```
{: id="20210121190309-g0x2q0v"}

我们可以对默认的抓屏按键进行修改，当然也可以绑定自己的快捷键，这里我选择绑定自己的快捷键 `alt+4`
{: id="20210121190427-36e29vc"}

* {: id="20210121190433-deif0o0"}进入系统设置中的“键盘快捷键”
* {: id="20210121190425-v45v3z7"}页面中会列出所有现有的键盘快捷键，拉到底部就会看见一个 “+” 按钮
* {: id="20210121190425-ebyl8y5"}点击 “+” 按钮添加自定义快捷键并输入以下两个字段：
  * {: id="20210121190425-jzzlexh"}“名称”： 任意名称均可。
  * {: id="20210121190425-qvmp30x"}“命令”： `flameshot gui`
  {: id="20210121190425-beg1s0n"}
{: id="20210121190425-l1i0kjs"}

![flameshotsetting.png](assets/flameshot-setting.png)
{: id="20210121181355-37j3uuf"}

之后就可以使用快捷键愉快的截图啦。
{: id="20210121191638-b2rjd5z"}

{: id="20210121192538-1sf4clu"}

{: id="20210121192538-ep6poc2"}

### 网络下载应用安装
{: id="20210110110525-upk55qn"}

我们通过下载网络应用，在 ubuntu 中安装对应软件，
{: id="20210110111135-no5py7r"}

```
# 对无法双脚安装的应用进行安装
sudo dpkg -i  "software.deb"
# 如果提示依赖问题 安装所有依赖
sudo apt-get install -f
# 卸载通过
# 通过 dpkg -l soft* 去查找卸载软件的完整名称
sudo dpkg --remove softname

```
{: id="20210110111200-cbn5w01"}


{: id="20210105194423-yg7b5jv" type="doc"}
