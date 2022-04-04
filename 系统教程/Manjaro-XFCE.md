# Manjaro-XFCE

## 系统安装

安装时断网以免因为网络不通畅造成进度卡在 93%

### 虚拟机安装

#### VirtualBox

- 分区可选带休眠分区

## 系统设置

### 换源

执行命令后选择速度最快的命令即可

```bash
pacman-mirrors -i -c China -m rank
```

### 安装中文输入法

三个包分别为 Fcitx5 、Fcitx5 中文拓展和根据中文维基百科创建的中文词库

```bash
sudo pacman -S fcitx5-im fcitx5-chinese-addons fcitx5-pinyin-zhwiki
```

启用 Fcitx5 需要添加环境变量

```bash
sudo nano /etc/environment
```

添加以下内容

```text
GTK_IM_MODULE=fcitx
QT_IM_MODULE=fcitx
XMODIFIERS=@im=fcitx
INPUT_METHOD=fcitx
SDL_IM_MODULE=fcitx
GLFW_IM_MODULE=ibus
```
