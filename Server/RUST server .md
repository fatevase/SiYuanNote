# linux-gsm
{: id="20210228210707-yv8yyh7" updated="20210228210714"}

{: id="20210228210742-v6tk2cw"}

依赖安装
{: id="20210228210742-rae7ak1" updated="20210228210747"}

```
dpkg --add-architecture i386
apt update
apt install curl wget file tar bzip2 gzip unzip bsdmainutils python util-linux ca-certificates binutils bc jq tmux netcat lib32gcc1 lib32stdc++6 steamcmd lib32z1
```
{: id="20210228210714-mg8h2ig" updated="20210228210826"}

{: id="20210228211048-48mf53q"}

利用linux-gsm安装依赖
{: id="20210228211050-s7otc79" updated="20210228211635"}

```bash
./rustserver install
```
{: id="20210228211114-ahlhoi6" updated="20210228211124"}

{: id="20210228211102-xtbl3ht"}

新建用户
{: id="20210228211403-og0y0wr" updated="20210228211407"}

steamcmd只允许运行在非root权限下的用户中,所以需要新建用户
{: id="20210228211410-t41s8nj" updated="20210228211437"}

```

adduser steam
su - steam

wget -O linuxgsm.sh https://linuxgsm.sh && chmod +x linuxgsm.sh && bash linuxgsm.sh rustserver
```
{: id="20210228211437-le55egp" updated="20210228211514"}


{: id="20210228210707-lzb5b0v" type="doc"}
