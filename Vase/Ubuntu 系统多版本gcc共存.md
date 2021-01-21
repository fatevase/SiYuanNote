# Ubuntu apt-get 软件多版本共存
{: id="20210121183236-ikzzz8z"}

由于使用过程中用到了低版本的gcc，这里做个示例，展示系统存在多版本软件时，对优先级进行设定。
{: id="20210121183301-bvnpiv8"}

在使用
{: id="20210121183405-znapi8o"}

```bash
# 安装低版本的gcc
sudo apt-get install gcc-7 g++-7

# 多版本软件设置默认优先级,数值越大优先级越高
sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-7 9
sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-9 1

# 检查当前gcc优先级
sudo update-alternatives --display gcc
```
{: id="20210121183413-f2tww2p"}


{: id="20210121183236-qx9uelp" type="doc"}
