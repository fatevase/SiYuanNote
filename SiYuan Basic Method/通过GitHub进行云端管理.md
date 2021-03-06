### 仓库同步
{: id="20210110111633-vtillwg"}

在界面上点击同步按钮后，思源笔记会通过 `git pull` 以及 `git push` 进行数据同步。如果遇到数据冲突，请使用 Git 工具来解决冲突，后续版本我们会逐步增加对 Git 操作的内置支持 TODO。注意：WebDAV 笔记本是不会同步的，因为 WebDAV 服务端本身就已经在云端了。我们选择使用 Git 实现版本管理不仅是因为 Git 的强大和稳定，更因为它是开放的。所以使用我们伺服的云端仓库并不是唯一的选择，你可以通过 `git remote add` 命令来添加其他远程仓库（比如 GitHub 仓库），然后通过 git 就可以和这些远程仓库进行同步了，操作细节请参考：
{: id="20210110111646-vq8yjjo"}

### 如何同步到 GitHub 仓库？
{: id="20210110111447-pjfuhss"}

1. {: id="20210110111538-wqtyznl"}在 GitHub 上创建一个仓库，并[配置 SSH](https://docs.github.com/cn/free-pro-team@latest/github/authenticating-to-github/connecting-to-github-with-ssh)
2. {: id="20210110111538-gyb7syt"}在笔记本文件夹下通过 `git remote add github git@github.com:user/repo.git` 配置远程仓库，其中：
   * {: id="20210110111538-s38dquw"}`github` 是远程仓库名，请勿使用 `origin`，因为 `origin` 是思源官方远程仓库名
   * {: id="20210110111538-4oxfy4z"}`user/repo` 请改为你自己的仓库名称
   {: id="20210110111538-0nh4agx"}
3. {: id="20210110111538-oayrgro"}通过 `git pull github main --allow-unrelated-histories` 从远程拉取
4. {: id="20210110111538-1u05k26"}通过 `git push github master` 推送远程 *master* 分支。请注意，GitHub 从 2020 年 10 月起新建的仓库默认分支名称为 *main*，使用该命令后远程仓库上会创建 `master` 分支，可在仓库 Settings - Branches 中将默认分支设置为 *master*
{: id="20210110111538-l5zot6n"}

### 如何删除不需要的历史记录以减少空间占用和提升性能？
{: id="20210110111601-rtmh4cn"}

1. {: id="20210110111601-9fkavid"}请确认云端数据已经完全拉取到本地，本地已经存有完整的数据
2. {: id="20210110111601-ua5glqy"}在设置 - 同步中删除云端仓库
3. {: id="20210110111601-k7ai8xf"}在文件系统上删除 .git 元数据文件夹
4. {: id="20210110111601-eumahxw"}重新启动思源笔记（会自动根据现有数据生成 .git 元数据文件夹）
5. {: id="20210110111601-x5vtbdh"}点击同步将数据同步到云端仓库
{: id="20210110111601-4gstwmn"}

{: id="20210110111601-u5o5yku"}


{: id="20210110111447-jbq19uz" type="doc"}
