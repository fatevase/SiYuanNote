## Dock 工作流程
{: id="20210125122452-xwfw293"}

### DOcker 与虚拟机的区别
{: id="20210125233920-q39gnal"}

![Docker](http://udn.yyuap.com/doc/docker_practice/_images/docker.png)![传统虚拟化](http://udn.yyuap.com/doc/docker_practice/_images/virtualization.png)
{: id="20210125233921-1djadhv"}

{: id="20210125234004-yp0t9qg"}

### Docker 纵览
{: id="20210125233936-ajvlhy5"}

在 Docker 的术语里，一个只读层被称为镜像，一个镜像是永久不会变的。
{: id="20210125234213-iyfquiy"}

{: id="20210125234219-fg7i9qi"}

{: id="20210125234219-rv1u5ul"}

![Docker Architecture Diagram](assets/docker-architecture.svg)
{: id="20210125122454-r5xeh3u"}

{: id="20210125233255-d45yypf"}

## 安装 Docker
{: id="20210125115557-u24f4jq"}

环境准备: Linux , ssh
{: id="20210125121754-16llpue"}

用到的网站:
{: id="20210125121840-8kid908"}

* {: id="20210125121817-fzhlyqk"}[docker 教程](https://www.bilibili.com/video/BV1og4y1q7M4?p=6):https://www.bilibili.com/video/BV1og4y1q7M4
* {: id="20210125121817-cjhfsly"}[docker-document](https://docs.docker.com/):https://docs.docker.com/
* {: id="20210125234031-8gmjvn2"}[docker 中文文档](http://www.dockerinfo.net):http://www.dockerinfo.net
{: id="20210125121817-nfsboj9"}

> 以下以 Ubuntu20.04LTS 进行安装操作,具体其他操作系统查看[官方文档](https://docs.docker.com/engine/install/):https://docs.docker.com/engine/install/
> {: id="20210125123139-4ezav4e"}
{: id="20210125122149-7nuf439"}

### 卸载旧版本
{: id="20210125120608-h9durcg"}

```shell
sudo apt-get remove docker docker-engine docker.io containerd runc
# 如果需要彻底卸载docker 包括docker下载的镜像,则执行如下命令
sudo rm -rf /var/lib/docker
```
{: id="20210125122218-64qqkr9"}

{: id="20210125233255-uhi470k"}

### 安装新版本
{: id="20210125121420-k9qs1e8"}

```shell

# 更新 apt-get
sudo apt-get update

# 安装 apt 依赖包，用于通过HTTPS来获取仓库:
sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common

# 加Docker官方GPG key:
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

# 设定 stable版本的镜像存储库(用于下载Docker)
sudo add-apt-repository \
   "deb [arch=amd64] http://mirrors.aliyun.com/docker-ce/linux/ubuntu \
   $(lsb_release -cs) \
   stable"

# 安装安装最新版本的 Docker Engine-Community 和 containerd 
sudo apt-get install docker-ce docker-ce-cli containerd.io
```
{: id="20210125122221-7gmzse0"}

> 在设定 docker 镜像存储库时,官方指定的仓库为:https://download.docker.com/linux/ubuntu
> {: id="20210125225103-nb6wki7"}
>
> 这里我改为的是 aliyun 的国内镜像仓库用于加速下载;
> {: id="20210125225103-8zhwcg4"}
>
> 加入并验证 Docker GPG key 并不是必须的步骤,只需要在 apt-get 添加 `--nogpgcheck`
> {: id="20210125225118-rctb1wm"}
>
> 通过 `sudo docker run hello-world`, 进行测试 docker 是否正常工作.
> {: id="20210125231755-v9bed15"}
{: id="20210125224958-pehyirv"}

{: id="20210125233255-9tn4n5t"}

### 更新
{: id="20210125225002-zcpmze0"}

```shell
# 更新docker 需要卸载旧版本后安装新版本
```
{: id="20210125225012-no97jdi"}

### 小结
{: id="20210125225001-ipm3x7f"}

这一套 Docker 命令行安装还不如自己手动下载 deb,用 `sudo dpkg -i /path/to/package.deb` 来的方便.
{: id="20210125225754-bam5tcj"}

ubuntu 的 deb 安装包地址:[https://download.docker.com/linux/ubuntu/dists/](https://download.docker.com/linux/ubuntu/dists/)
{: id="20210125231511-l8thx6s"}

通过 `lsb_release -a` 查看自己系统版本的代号,在对应代号后下的/pool/stable/里下载符合自己系统的
{: id="20210125230035-inmw7ls"}

`containerd.io_x.deb`,`docker-ce-cli_x.deb`,`docker-ce_x.deb`,并手动 dpkg 安装.
{: id="20210125231431-7earg33"}

![dockerdebdonwload.png](assets/docker-deb-donwload.png)
{: id="20210125230132-0xp28vy"}

{: id="20210125233255-7d118td"}

### 设置镜像库
{: id="20210125121431-6l1jkwb"}

{: id="20210125233255-a5cnl6j"}


{: id="20210125115524-zotzeow" type="doc"}
