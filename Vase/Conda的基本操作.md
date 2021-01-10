# conda 基础使用
{: id="20210110124639-evix931"}

* {: id="20210110124653-76r3bj0"}conda activate name # 激活某个环境
  conda deactivate # 推出环境
* {: id="20210110124653-927t3tr"}conda install [包名=版本号] # 使用 conda 内置安装
* {: id="20210110124653-3mnnl5k"}conda create -n name python=3.8 opencv=4.5.0 jupyter # 创建某个环境
  * {: id="20210110131228-w5g6bai"}conda env create -f env.yaml 也可以创建环境
  {: id="20210110131228-3fndy37"}
* {: id="20210110124653-c445hfp"}conda remove -n name --all 移除某个环境
* {: id="20210110124653-9j4dsie"}vi /root/.condarc # 镜像频道配置文件
* {: id="20210110124653-gmuf9zk"}conda config --show # 能够显示出所有 conda 的 config 信息
  * {: id="20210110124653-a7pfg7s"}conda config --show-sources
  {: id="20210110131321-ok7dplv"}
* {: id="20210110124653-myvlu7w"}conda config --remove channels url  删除镜像频道
* {: id="20210110124653-6y7plqb"}conda config --add channels url  添加镜像频道
* {: id="20210110124653-6sltndf"}conda config --set auto_activate_base False 取消一开始就进入 base
* {: id="20210110124653-v1aek02"}conda update -n base -c defaults conda # 更新 conda
* {: id="20210110124653-z8py9p3"}conda clean --packages --tarballs # 清理 conda 包缓存
* {: id="20210110131218-ynz8xnf"}
{: id="20210110124653-qlemso6"}

```
show_channel_urls: true
channels:
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/pytorch/
  - https://mirrors.bfsu.edu.cn/anaconda/pkgs/main/
  - https://mirrors.bfsu.edu.cn/anaconda/pkgs/free/
  - http://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/msys2/
  - http://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge
  - http://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
ssl_verify: true
```
{: id="20210110124653-1uqpo06"}

{: id="20210110131515-iobjz89"}

ubuntu 安装conda后要手动将conda加入系统环境
{: id="20210110131517-i8a3xx8"}


{: id="20210110124639-ubr0y74" type="doc"}
