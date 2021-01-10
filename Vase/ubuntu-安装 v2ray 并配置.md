# clash install and using
{: id="20210110104536-6ilxlsb"}

首先是下载[clash for linux](https://github.com/Dreamacro/clash/releases) https://github.com/Dreamacro/clash/releases
{: id="20210110104536-7kkren0"}

安装好后放到自己软件的文件夹 如/home/username/software/clash
{: id="20210110104536-y5ikz6h"}

在对应的 clash 文件夹下解压对应的压缩包 如下命令：` gzip -d 'clash.gz'`。
{: id="20210110104536-v06ezc1"}

此时 clash 文件并没有权限，将 clash 整个文件夹赋予执行权限：`chmod +x ./clash`。
{: id="20210110104536-7qal0tt"}

之后在解压好的文件夹下尝试运行 clash ：` ./clash`。
{: id="20210110104536-p0px70o"}

当提示
{: id="20210110104536-b6oxyjj"}

> INFO[0022] HTTP proxy listening at :127.0.0.1:7890
> {: id="20210110104536-2zxz1sb"}
>
> INFO[0000] SOCKS proxy listening at : 127.0.0.1:7891
> {: id="20210110104536-esy6j8q"}
>
> INFO[0000] RESTFul API listening at:127.0.0.1:9090
> {: id="20210110104536-p0y5a86"}
{: id="20210110104536-u6hxeeo"}

则表示 clash 正常安装并打开了。
{: id="20210110104536-wuhcej1"}

当然配置文件为你在其他平台购买的配置文件，如果第一次没有配置文件会自动生产默认的配置文件，如果系统中没有 MMDB，clash 会自行进行下载和安装。
{: id="20210110104536-9vjwiwl"}

![image.png](assets/20210109204500-qh3t2y7-image.png)
{: id="20210110104536-90yal67"}

在正式使用 clash 前，我们需要配置对应的 clash 代理端口和 clash 的配置文件，之后在文件夹下放好对应的 config.yaml。注意  此时 clash 的配置文件目录在`~/.config/clash`下。
{: id="20210110104536-qk7ua8j"}

重新启动 clash 即可通过[clash 控制台](https://clash.razord.top/#/settings)：clash.razord.top/ 进入控制面板进行操作。
{: id="20210110104536-ptt0rcf"}

注意控制台输入的端口与给出的'restful API '一致才可登陆正常
{: id="20210110104536-lem3xz5"}

![image.png](assets/20210109204451-31nyjyr-image.png)
{: id="20210110104536-3brcna8"}

{: id="20210110104616-jjbbs63"}

# Qv2ray install and using 
{: id="20210110104617-dtvjid5"}

Qv2ray相对于clash有具体的图形界面，并且可以在ubuntu中下载并使用![20210110104753的屏幕截图.png](assets/20210110104804-6n426dt-2021-01-10 10-47-53 的屏幕截图.png)
{: id="20210110104628-59ho73s"}

安装好qv2ray后，我们需要对其v2ray核心进行配置，首先是下载[v2ray-core](https://hub.fastgit.org/v2fly/v2ray-core/releases)，https://hub.fastgit.org/v2fly/v2ray-core/releases
{: id="20210110104813-eztyb8u"}

下载后解压到对应的qv2ray核心中，如![20210110105123的屏幕截图.png](assets/20210110105142-66zp561-2021-01-10 10-51-23 的屏幕截图.png)
{: id="20210110104934-av3wzus"}

检查v2ray核心设置是否正确后就可以正常使用了。
{: id="20210110104929-go0idjb"}

{: id="20210110105521-q2cf67s"}

{: id="20210110105521-09ffggp"}


{: id="20210109195132-pnk1oil" type="doc"}
