## Dock 工作流程
{: id="20210125122452-xwfw293"}

![Docker Architecture Diagram](assets/docker-architecture.svg)
{: id="20210125122454-r5xeh3u"}

{: id="20210125122453-dwqq1qy"}

## 安装 Docker
{: id="20210125115557-u24f4jq"}

环境准备: Linux , ssh
{: id="20210125121754-16llpue"}

用到的网站:
{: id="20210125121840-8kid908"}

* {: id="20210125121817-fzhlyqk"}[docker 教程](https://www.bilibili.com/video/BV1og4y1q7M4?p=6):https://www.bilibili.com/video/BV1og4y1q7M4?p=6
* {: id="20210125121817-cjhfsly"}[docker-document](https://docs.docker.com/):https://docs.docker.com/
{: id="20210125121817-nfsboj9"}

> 以下以 Ubuntu20.04LTS 进行安装操作,具体其他操作系统查看[官方文档](https://docs.docker.com/engine/install/):https://docs.docker.com/engine/install/
> {: id="20210125123139-4ezav4e"}
{: id="20210125122149-7nuf439"}

### 卸载旧版本
{: id="20210125120608-h9durcg"}

```shell
sudo apt-get remove docker docker-engine docker.io containerd runc

```
{: id="20210125122218-64qqkr9"}

{: id="20210125122218-jt7r0km"}

### 安装新版本
{: id="20210125121420-k9qs1e8"}

```shell

sudo apt-get update

sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common
sudo apt-get install docker-ce docker-ce-cli containerd.io
```
{: id="20210125122221-7gmzse0"}

{: id="20210125122220-nipf8g5"}

### 设置镜像库
{: id="20210125121431-6l1jkwb"}

{: id="20210125122143-ae327nl"}


{: id="20210125115524-zotzeow" type="doc"}
