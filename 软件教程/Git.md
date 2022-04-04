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
