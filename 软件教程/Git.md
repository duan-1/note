# Git 学习笔记

## 软件配置

使用 `git config` 配置环境变量。环境变量决定了 Git 在各个环节的具体工作方式和行为，可以存放在以下三个不同地方

- /etc/gitconfig 文件：用于所有用户的配置，使用 --system 选项。Windows 则在 Git 安装路径下。
- ~/.gitconfig 文件：用户目录下的配置文件只适用于该用户，使用 --global 选项。Windows 一般位于 C:\User\~ 下。
- 工作目录下的 .git/config 文件：只适用于工作目录。

每一级的配置都会覆盖上层的相同配置。

### 用户信息

配置个人的用户名称和电子邮件：

```bash
git config --global user.name xxx
git config --global user.email xxx
```

### ·配置默认分支

```bash
git config --global init.defaultBranch <名称>
```

### 查看配置信息

```bash
git config -l / --List
```

### 配置密钥

参见 Github 官方文档，[Generating a new SSH key and adding it to the ssh-agent](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)

Linux 环境下需要将私钥添加到 ssh-agent，可以使用如下命令：

```bash
ssh-add ~/.ssh/example
```

但是每次重新启动时就需要重新添加一次，则可以修改文件`~/.ssh/config`（没有可以自行创建），向其中添加以下内容即可。

```text
#github
Host github.com
Hostname github.com
PreferredAuthentications publickey
IdentityFile ~/.ssh/github
```

## 命令说明

### init

将当前目录作为仓库初始化，使用示例：

```bash
git init
```

## 小技巧

- 在 Github 添加过密钥后，使用 ssh 方式与仓库进行通信就不会像 HTTPS 那样每次操作都需要输入密码。
  