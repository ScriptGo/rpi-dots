# rpi-dots

Raspberry Pi OS 相关配置

## 安装

**安装过程略...**

## 配置

### 源

**更换源之前，请先确认系统的架构和版本**

```bash
uname -m         # 查看系统的架构
lsb_release -a   # 查看系统版本信息
```

1.备份源

```bash
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
```

2.编辑 `/etc/apt/sources.list` 文件

注释掉原有的源，加入下面的源:

```bash
# 默认注释了源码镜像以提高 apt update 速度，如有需要可自行取消注释
deb https://mirrors.tuna.tsinghua.edu.cn/debian/ bookworm main contrib non-free non-free-firmware
# deb-src https://mirrors.tuna.tsinghua.edu.cn/debian/ bookworm main contrib non-free non-free-firmware

deb https://mirrors.tuna.tsinghua.edu.cn/debian/ bookworm-updates main contrib non-free non-free-firmware
# deb-src https://mirrors.tuna.tsinghua.edu.cn/debian/ bookworm-updates main contrib non-free non-free-firmware

deb https://mirrors.tuna.tsinghua.edu.cn/debian/ bookworm-backports main contrib non-free non-free-firmware
# deb-src https://mirrors.tuna.tsinghua.edu.cn/debian/ bookworm-backports main contrib non-free non-free-firmware

deb https://mirrors.tuna.tsinghua.edu.cn/debian-security bookworm-security main contrib non-free non-free-firmware
# deb-src https://mirrors.tuna.tsinghua.edu.cn/debian-security bookworm-security main contrib non-free non-free-firmware

```

3.修改 rpi 源

编辑 `/etc/apt/sources.list.d/raspi.list` 文件

注释掉原有的源，加入下面的源:

```bash
deb https://mirrors.tuna.tsinghua.edu.cn/raspberrypi/ bookworm main
```

4.更新源

修改源后使用 `sudo apt update` 更新源列表使其生效。

### 更新系统

1.更新本地软件包列表

`sudo apt update`

2.将所有已安装的软件包升级到最新版本

`sudo apt full-upgrade`

### 字体

1.从源中安装

`sudo apt install fonts-noto fonts-noto-cjk fonts-noto-color-emoji fonts-firacode`

2.手动安装

将下载的字体复制到 `.local/share/fonts` 目录下，然后执行 `fc-cache -f -v` 即可。

### 输入法

1.安装

`sudo apt install fcitx5 fcitx5-rime`

2.配置

参考这个 [repo]()

### zsh

1.安装 zsh

```bash
sudo apt install zsh zsh-doc
```

2.安装 zsh 插件

```bash
sudo apt install zsh-syntax-highlighting zsh-autosuggestions
```

3.切换shell

`chsh -s $(which zsh)`

4.美化

`curl -sS https://starship.rs/install.sh | sh`

5.注销或重启系统

### 其他

`sudo apt install fzf fd-find bat ripgrep`
