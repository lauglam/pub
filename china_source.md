# 国内源

## 设置 nodejs 国内源

### 临时更换

```shell
npm --registry https://registry.npm.taobao.org install express
```

### 永久使用

```shell
npm config set registry https://registry.npm.taobao.org
```

### 检查

```shell
npm config get registry
```

## 设置 archlinux 国内源

1. 设置 `mirroslist`

```shell
sudo nano /etc/pacman.d/mirrorlist
```

```text
## China
Server = https://mirrors.aliyun.com/archlinux/$repo/os/$arch

## China
Server = https://mirrors.ustc.edu.cn/archlinux/$repo/os/$arch
```

2. 设置 `pacman.conf`

```shell
sudo nano /etc/pacman.conf
```

```text
[archlinuxcn]
Server = https://mirrors.ustc.edu.cn/archlinuxcn/$arch
```

