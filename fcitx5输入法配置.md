## 安装 fcitx5 相关包


### 官方包安装

```shell
sudo pacman -S fcitx5-im fcitx5-chinese-addons fcitx5-pinyin-zhwiki fcitx5-pinyin-moegirl
```

- fcitx5-im: fcitx5-im 包组提供 fcitx5 包本体配置工具和必要的输入法模块
- fcitx5-chinese-addons: 包含与中文相关的 addon，例如拼音、双拼和五笔
- fcitx5-pinyin-zhwiki: 来自zh.wikipedia.org的词库
- fcitx5-pinyin-moegirl: 萌娘词库


### AUR包安装（可选）

```shell
yay -S fcitx5-pinyin-custom-pinyin-dictionary
```

- fcitx5-pinyin-custom-pinyin-dictionary: Fcitx5 自建拼音输入法词库，百万常用词汇量


### 添加开机执行脚本`enable_fcitx.sh`

```shell
sudo nano /etc/profile.d/enable_fcitx.sh
```

输入以下内容:

```shell
# https://wiki.archlinux.org/index.php/Fcitx
# https://wiki.archlinux.org/index.php/Fcitx5
im=fcitx
export GTK_IM_MODULE=$im
export QT_IM_MODULE=$im
export XMODIFIERS=@im=$im
export INPUT_METHOD=$im
export SDL_IM_MODULE=$im

```
