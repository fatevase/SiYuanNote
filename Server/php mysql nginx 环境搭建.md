{: id="20210130003232-ywveokg"}

### 安装 nginx
{: id="20210130003232-lpqav6m"}

```shell
sudo apt-get intsall nginx
```
{: id="20210130003242-3a1m052"}

{: id="20210130001814-i5o1rk6"}

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
