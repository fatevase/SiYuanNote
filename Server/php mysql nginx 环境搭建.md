{: id="20210130003232-ywveokg"}

### 安装 nginx
{: id="20210130003232-lpqav6m"}

```shell
apt install nginx

# 请确保80端口没有被其他服务占用
/etc/init.d/nginx start
```
{: id="20210130003242-3a1m052"}

Ubuntu 安装之后的文件结构大致为:
{: id="20210130003411-w3fhh32"}

* {: id="20210130003411-yon7d8r"}所有的配置文件都在/etc/nginx 下,并且每个虚拟主机已经安排在了/etc/nginx/sites-available 下 www.jb51.net
{: id="20210130003411-b6iiu9h"}

* {: id="20210130003414-l358dm1"}程序文件在/usr/sbin/nginx * 日志放在了/var/log/nginx 中
{: id="20210130003411-3ojw9wh"}

* {: id="20210130003415-nfspr1d"}并已经在/etc/init.d/下创建了启动脚本 nginx
{: id="20210130003411-uplwf34"}

* {: id="20210130003411-hgabzl2"}默认的虚拟主机的目录设置在了/var/www/nginx-default
{: id="20210130003411-g1avt6f"}

{: id="20210130003411-2hpgc00"}

{: id="20210130003411-3ikx2zv"}

### 安装 php7
{: id="20210130001815-ry9wdu3"}

ubuntu 20.04 使用 `apt install php` 自动会安装 php7.4
{: id="20210130001904-2gh1nh9"}

也可以使用
{: id="20210130002013-y6j6wuu"}

```shell
# 指定安装版本 
apt install php7.4

# php拓展
sudo -y apt install php7.4-dev   //phpize需要
sudo -y apt install php-pear     //pecl需要
sudo -y apt install php7.4-fpm php7.4-mysql php7.4-curl php7.4-json php7.4-mbstring php7.4-xml php7.4-intl
```
{: id="20210130002019-0tlkl1g"}

{: id="20210130002233-r9xnu4z"}

### 安装 mysql
{: id="20210130002234-aqzoayw"}

ubuntu 20.04 使用 `apt install mysql-server mysql-client` 自动会安装 5.7 版本
{: id="20210130002510-pie30mp"}

{: id="20210130002533-a9lz0p3"}


{: id="20210130001809-7h4gs4n" type="doc"}
