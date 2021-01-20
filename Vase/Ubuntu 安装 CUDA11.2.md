# Anacoda + CUDA 安装
{: id="20210120125837-d110pqb"}

{: id="20210120125843-7rh8x0t"}

首先是miniconda的安装
{: id="20210120130012-lyar9jj"}

先去conda官网下载对应系统的[最新版本miniconda](https://docs.conda.io/en/latest/miniconda.html)，linux操作系统下载.sh的执行文件
{: id="20210120130030-6vxy9fx"}

![20210120130210的屏幕截图.png](assets/20210120130223-gqskbms-2021-01-20 13-02-10 的屏幕截图.png)
{: id="20210120130150-mnqmpsh"}

命令行模式下给下载的文件执行权限,并执行
{: id="20210120223711-ceaqcit"}

```bash
sudo chmod +x filename.sh
# 执行当前目录下的filename.sh 脚本
./filename.sh
```
{: id="20210120223759-o2xkhnn"}

{: id="20210120223750-hhzkwz7"}

根据提示安装好conda后，此时环境变量并没有配，需要手动把conda加入环境变量中即可
{: id="20210120224135-v3v6c33"}

linux 环境变量配置的地方有几处如 `~/.bashrc` 和`~/.profile`，个人建议装在profile中配置自己的环境变量。
{: id="20210120224232-278f3p2"}

```bash
nano ~/.profile
#在底端添加
export PATH=$PATH:condapath/conda
# 一般conda默认安装在~/minicondaX 里，我这边修改后的示例为
# export PATH=$PATH:~/software/miniconda3/bin

# 之后执行 source指令激活修改后的环境变量
source ~/.profile
# 测试是否
```
{: id="20210120224727-dmr9laa"}

ubuntu20.04 tls只支持cuda11以上版本 所以目标安装cuda11.2最新版本
{: id="20210120125843-e616g1f"}

{: id="20210120125918-a8zk86z"}


{: id="20210120125837-xlp5tbq" type="doc"}
