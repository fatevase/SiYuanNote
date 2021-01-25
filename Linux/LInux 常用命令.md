## 系统相关
{: id="20210125120818-uzxvbag"}

### 查看系统内核版本
{: id="20210125120831-1v4x4f0"}

>  uname -r
> {: id="20210125120926-lojh8cx"}
{: id="20210125120901-3wcuc0o"}

```shell
用法：uname [选项]...
输出一组系统信息。如果不跟随选项，则视为只附加 -s 选项。

  -a, --all                以如下次序输出所有信息。其中若 -p 和
                             -i 的探测结果不可知则被省略：
  -s, --kernel-name        输出内核名称
  -n, --nodename           输出网络节点上的主机名
  -r, --kernel-release     输出内核发行号
  -v, --kernel-version     输出内核版本
  -m, --machine            输出主机的硬件架构名称
  -p, --processor          输出处理器类型（不可移植）
  -i, --hardware-platform  输出硬件平台或（不可移植）
  -o, --operating-system   输出操作系统名称
      --help		显示此帮助信息并退出
      --version		显示版本信息并退出
```
{: id="20210125120914-80kr61x"}

### 查看系统完整信息
{: id="20210125121005-i6qqin6"}

> cat /etc/os-release
> {: id="20210125121100-sotf5jb"}
{: id="20210125121058-7c9umi9"}

```shell
(base) vase@vase:~/software/vscode$ cat /etc/os-release
NAME="Ubuntu"
VERSION="20.04.1 LTS (Focal Fossa)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 20.04.1 LTS"
VERSION_ID="20.04"
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
VERSION_CODENAME=focal
UBUNTU_CODENAME=focal
```
{: id="20210125121007-l3hq0rs"}


{: id="20210125120818-o302py1" type="doc"}
