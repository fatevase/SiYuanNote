# conda 基础使用

* conda activate name 激活某个环境
  conda deactivate 推出环境
* conda install [包名=版本号] 使用 conda 内置安装
* conda create -n name python=3.8 opencv=4.5.0 jupyter 创建某个环境
* conda remove -n name --all 移除某个环境
* vi /root/.condarc 镜像频道配置文件
* conda config --show 能够显示出所有 conda 的 config 信息
* conda config --show-sources
* conda config --remove channels url  删除镜像频道
* conda config --add channels url  添加镜像频道
* conda config --set auto_activate_base False 取消一开始就进入 base
* conda update -n base -c defaults conda 更新 conda
* conda clean --packages --tarballs 清理 conda 包缓存

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
