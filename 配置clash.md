## 安装 Clash

### 准备工作


* 下载 clash

```text
https://github.com/Dreamacro/clash/releases
```

下载完解压，将程序改名为 clash


* 下载 clash dashboard

```text
https://github.com/Dreamacro/clash-dashboard/tree/gh-pages
```

下载完解压，将文件夹改名为 dashboard


* 启动 Clash（让它创建配置文件）

```shell
./clash -d .
```

它会在当前目录自动下载`cache.db` `Country.mmdb` 和 `config.yaml`文件


* 下载订阅和配置信息（这会覆盖 clash 下载的默认 `config.yaml` 文件）

```shell
sudo wget -O config.yaml [订阅地址]
```


* 打开 clash 订阅配置文件: `config.yaml`，设置外部管理ui

```shell
external-ui: dashboard
```


* 建立开机启动服务配置文件: `clash.service`

```shell
sudo nano ./clash.service
```

输入以下内容:

```text
[Unit]
Description=clash daemon

[Service]
Type=simple
User=root
ExecStart=/usr/bin/clash -d /etc/clash/
Restart=on-failure

[Install]
WantedBy=multi-user.target
```

保存退出


* 全局代理脚本: `enable_proxy.sh`

```shell
sudo nano ./enable_proxy.sh
```

输入以下内容:

```shell
proxy="http://127.0.0.1:7890"
export http_proxy=$proxy
export https_proxy=$proxy
export ftp_proxy=$proxy
export no_proxy="localhost,127.0.0.1,::1"
```


* 将上面所有文件放进 clash 文件夹，具体结构如下：

```text
clash
├─ clash  # 主程序
├─ config.yaml  # 订阅配置文件
├─ cache.db  # 自动下载的
├─ Country.mmdb  # 自动下载的
├─ clash.service  # clash开机启动配置文件
├─ enable_proxy.sh  # clash全局代理脚本
└─ dashboard  # 存放外部管理ui的文件夹
   ├─ assets
   ├─ index.html
   └─ ...
```

### 移动到正确位置


* 将 clash 程序移动到 `/usr/bin/` 目录下

```shell
sudo mv ./clash/clash /usr/bin/
```


* 将 enable_proxy 脚本文件移动到 `/etc/profile.d/` 目录下（开机后系统会自动执行该目录下的用户脚本）

```shell
sudo mv ./clash/enable_proxy.sh /etc/profile.d/
```


* 将 clash 文件夹移动到`/etc/` 目录下，方便后续管理

```shell
sudo mv ./clash /etc/
```


* 将开启启动配置 clash.service 链接到 `/etc/systemd/system/` 目录下

```shell
sudo ln -s /etc/clash/clash.service /etc/systemd/system/
```


### 设置 Clash 开机启动


* 启动 clash

```shell
sudo systemctl start clash.service
```


* 查看 clash 状态

```shell
sudo systemctl status clash.service
```


* 设置 clash 开机自启动

```shell
sudo systemctl enable clash.service
```


* 以下为 clash 相关的管理命令

```shell
# 启动Clash
sudo systemctl start clash.service

# 重启Clash
sudo systemctl restart clash.service

# 查看Clash运行状态
sudo systemctl status clash.service
```


### 配置定时更新订阅（可选）

* 先撸个脚本，别忘了设可执行权限

```shell
#!/bin/bash

# 设置clash路径
clash_path="/etc/clash"

# 停止clash
systemctl stop clash.service

# 取消代理
unset https_proxy

# 如果配置文件存在，备份后下载，如果不存在，直接下载
if [ -e $clash_path/config.yaml ]; then
	mv $clash_path/config.yaml $clash_path/configbackup.yaml
	wget -O $clash_path/config.yaml "[你的订阅链接]"
else
	wget -O $clash_path/config.yaml "[你的订阅链接]"
fi

# 重启clash
systemctl restart clash.service

# 重设代理
export https_proxy="http://127.0.0.1:7890"
```


* 设置定时任务

```shell
sudo crontab -e
```


* 填入以下内容

```shell
//每月1号和15号的4点30分开始更新
30 4 1,15 * * sh [脚本目录]/[脚本名称]
```


* 重启crontab，使配置生效

```shell
sudo systemctl restart cron.service
```


* 查看代理是否正常工作

```shell
curl www.google.com
```
