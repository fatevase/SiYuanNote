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

用 u 盘安装进固态硬盘需要对固态进行分区操作，需要分出 bios 区域(512m)、efi 系统分区(1024m)、swap 分区用于休眠（4G（不休眠）/20G（需休眠））和其他的直接省事 ext4 日志文件系统格式全分配为`\`拓展分区。
{: id="20210110110127-01204e8"}

### 服务器安装
{: id="20210110110127-86kh9cb"}

如果只使用命令行模式，则可以下载对于的[服务器版本](https://ubuntu.com/download/server)，https://ubuntu.com/download/server
{: id="20210110110127-a37guiw"}

按照[官方指导](https://ubuntu.com/tutorials/install-ubuntu-server#1-overview)进行安装，https://ubuntu.com/tutorials/install-ubuntu-s#1-overview#
{: id="20210110110127-42umi3c"}

# 常用软件安装
{: id="20210110110236-xwwg3hx"}

### v2ray相关vpn安装
{: id="20210110110259-2td3aba"}

((20210110110411-eb83f2v "ubuntu-安装 v2ray 并配置"))
{: id="20210110112821-7qjisw1"}

{: id="20210121190302-3og7fqk"}

截图软件安装
{: id="20210121190301-0wu2a3j"}

```
# flameshot 一个支持自定义截图的
sudo apt install flameshot
```
{: id="20210121190309-g0x2q0v"}

{: id="20210121181355-37j3uuf"}

### 网络下载应用安装
{: id="20210110110525-upk55qn"}

我们通过下载网络应用，在ubuntu中安装对应软件，
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

{: id="20210121181355-kddr05w"}

{: id="20210121181355-ro1211e"}


{: id="20210105194423-yg7b5jv" type="doc"}
