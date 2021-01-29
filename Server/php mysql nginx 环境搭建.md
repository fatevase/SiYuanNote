{: id="20210130001814-i5o1rk6"}

### 安装 php7
{: id="20210130001815-ry9wdu3"}

ubuntu 20.04 使用 `apt install php` 自动会安装最新版 php7.4
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

11 建议直接使用 `apt install php` 安装
{: id="20210130002234-aqzoayw"}


{: id="20210130001809-7h4gs4n" type="doc"}
