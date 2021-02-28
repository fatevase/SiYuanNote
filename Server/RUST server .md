# linux-gsm
{: id="20210228210707-yv8yyh7" updated="20210228210714"}

{: id="20210228210742-v6tk2cw"}

依赖安装
{: id="20210228210742-rae7ak1" updated="20210228210747"}

```
dpkg --add-architecture i386
apt update
apt install curl wget file tar bzip2 gzip unzip bsdmainutils python util-linux ca-certificates binutils bc jq tmux netcat lib32gcc1 lib32stdc++6 steamcmd lib32z1 python3 cpio libsdl2-2.0-0:i386
```
{: id="20210228210714-mg8h2ig" updated="20210228213922"}

{: id="20210228211048-48mf53q"}

如果已经安装了对应的gsm启动文件,可以利用linux-gsm安装依赖
{: id="20210228211050-s7otc79" updated="20210228211657"}

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

```
{: id="20210228211437-le55egp" updated="20210228211706"}

{: id="20210228211707-zeajbsd"}

下载并启动
{: id="20210228211707-jichjzu" updated="20210228211734"}

```bash
mkdir /home/steam/rust && cd /home/steam/rust/
wget -O linuxgsm.sh https://linuxgsm.sh && chmod +x linuxgsm.sh && bash linuxgsm.sh rustserver
./rustserver install
```
{: id="20210228211715-xajwlt8" updated="20210228212555"}

{: id="20210228211720-wslbkg6"}

{: id="20210228212654-48lfibn"}

{: id="20210228212654-429s4gq"}

docker 一键安装
{: id="20210228211721-f69etvi" updated="20210228212702"}

```bash
docker pull gameservermanagers/linuxgsm-docker


$ mkdir -p ~/lgsm && sudo chown -R 750:750 ~/lgsm
$ docker run -d --name lgsm-docker -p <server-ports>:<server-ports>  --restart always --net=host --hostname LGSM -it -v "~/software/lgsm:/home/lgsm/" gameservermanagers/linuxgsm-docker
```
{: id="20210228212702-6ef967t" updated="20210228213025"}


{: id="20210228210707-lzb5b0v" type="doc"}
