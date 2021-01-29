# V2ray 自建
{: id="20210122032926-8edhlc9"}

#### 摘要
{: id="20210125120003-gbnbdau"}

建议使用 websocket 进行链接,安全性对比 tcp 高不少,要求更高的安全性可以选择 ws+tls 的 https 证书形式
{: id="20210125120017-io3ys5x"}

{: id="20210130011955-1jap17s"}

## 必要环境安装
{: id="20210125120032-otaj13d"}

> 安装 nginx：apt update && apt install -y nginx
> {: id="20210122032926-a630m9z"}
>
> 安装 v2ray：wget https://github.com/v2fly/fhs-install-v2ray/blob/master/install-release.sh && bash install-release.sh
> {: id="null"}
{: id="20210122032926-0inqpys"}

{: id="20210130011955-zt0xy0p"}

## 解析域名
{: id="20210122033201-urfi1ux"}

ws 操作需要解析一个域名到自己的 vps 中, 随便买一个即可.如果需要加入 tls 加密,则需要在申请个 https 的证书,这个证书有脚本自动获取,也可以手动,这里我推荐手动,因为脚本会有失误的时候,且每 3 个月过期一次,手动申请的有效期一年,也就是 1 年只需要操作一次即可.
{: id="20210122033236-wcqgzsu"}

[这里也有自动申请的方式](https://neko.re/archives/112.html)
{: id="20210122033202-jm1hlgy"}

## 配置 Nginx
{: id="20210122032926-wpmkbtz"}

```bash
安装 nginx：apt update && apt install -y nginx
安装 v2ray：wget https://install.direct/go.sh && bash go.sh
安装 Certbot：
OS 不同，方法不同，参考 https://certbot.eff.org/
```
{: id="20210122033431-umlsf85"}

{: id="20210130011955-gc9sv6z"}

安装好 Nginx 后, cd 到 /etc/nginx/conf.d，添加文件 v2ray.conf，填入以下内容，文中 example.com 修改为你解析到 vps 的域名
{: id="20210122032926-ecles8h"}

```
vim /etc/nginx/conf.d/v2ray.conf
```
{: id="20210122032926-bjtmfhq"}

```
server {
  listen  443 ssl;
  ssl on;
  ssl_certificate       /etc/v2ray/v2ray.crt;
  ssl_certificate_key   /etc/v2ray/v2ray.key;
  ssl_protocols         TLSv1 TLSv1.1 TLSv1.2;
   ssl_ciphers           HIGH:!aNULL:!MD5;

  server_name           example.com;  #replace with your self webname
  
  location / {
      default_type application/json;
      add_header Content-Type "text/plain;charset=utf-8";
      return 200 "OK~!";
    }

        location /ray { # keep the same path with v2ray conf
        proxy_redirect off;
        proxy_pass http://127.0.0.1:10000; # same port
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection "upgrade";
        proxy_set_header Host $http_host;

        # Show realip in v2ray access.log
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        }
}
```
{: id="20210122032926-0z3he9g"}

之后使用 `nginx -t ` 测配置是否正确,正确后 `systemctl restart nginx` 启动服务,
{: id="20210122032926-0fok6su"}

> 要注意如果不是配置 tls 则不需要服务器监听 443 端口,正常 80 即可,不需要配置证书相关.
> {: id="20210122032926-5ygfbos"}
{: id="20210122032926-nuhv8nw"}

## 配置 V2ray
{: id="20210122032926-otlzbh1"}

```
/etc/v2ray/config.json
```
{: id="20210122032926-omlh8s7"}

[UUID 在线生成](https://www.uuidgenerator.net/)
{: id="20210122034012-ji70uqu"}

{: id="20210130011955-wsm9e5i"}

```json
{
    "inbounds": [
        {
            "port": 10000,
            "listen": "127.0.0.1",
            "protocol": "vmess",
            "settings": {
                "clients": [
                    {
                        "id": "xxxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
                        "alterId": 64
                    }
                ]
            },
            "streamSettings": {
                "network": "ws",
                "wsSettings": {
                    "path": "/ray" # the path is same with your nginx web path
                }
            }
        }
    ],
    "outbounds": [
        {
            "protocol": "freedom",
            "settings": {}
        }
    ]
}

```
{: id="20210122032926-ygr5fnm"}

{: id="20210130011955-d5f2ava"}

## 客户端连接
{: id="20210122033802-a4w50e0"}

客户端连接的时候设置 path 为 ray，开启底层传输安全（tls），地址即为你的域名，用户 id 即为你的 uuid
{: id="20210122033802-0lm3s4e"}

{: id="20210130011955-9mpyac5"}


{: id="20210122032910-k292ue1" type="doc"}
