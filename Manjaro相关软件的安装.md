# Manjaro 相关软件的安装

Manjaro 系统安装相关的问题、命令和代码

## 安装 Yay AUR 助手

```shell
sudo pacman -S yay base-devel
```

## 安装思源中文字体

```shell
sudo pacman -S adobe-source-han-sans-cn-fonts
```

## Manjaro 安装 snap

* pacman 安装 snap

```shell
sudo pacman -S snapd
```

* snapd.socket 开机启动

```shell
sudo systemctl enable --now snapd.socket
```

* snapd.apparmor 开机启动

```shell
sudo systemctl enable --now snapd.apparmor
```

* 设置 snap 链接

```shell
sudo ln -s /var/lib/snapd/snap /snap
```

* 重启系统，然后安装 snap-store snap-store-proxy snap-store-proxy-client

```shell
sudo snap install snap-store snap-store-proxy snap-store-proxy-client
```

## Nodejs 安装

### 安装 nvm

* 安装 nvm 管理 nodejs 多版本

```shell
yay -S nvm
```

* 往 . zshrc 里写入 nvm 脚本

```shell
echo 'source /usr/share/nvm/init-nvm.sh' >> ~/.zshrc
```

* 重启 zsh

```shell
source ~/.zshrc
```

* 使用 nvm 安装 nodejs 长期支持版

```shell
nvm install --lts
```

* 查看

```shell
# nodejs版本
node -v
# npm版本
npm -v
# nodejs列表
nvm list
# 当前nodejs
nvm current

```

## 安装 VMware tools

 Manjaro 原本的版本与官方冲突

* 卸载原本的

```shell
sudo pacman -R open-vm-tools
```

* 拉取仓库并安装

```shell
#克隆仓库
git clone https://github.com/rasa/vmware-tools-patches.git

#进入目录
cd vmware-tools-patches

#执行脚本
sudo ./patched-open-vm-tools.sh
```
