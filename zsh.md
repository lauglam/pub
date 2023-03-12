# 安装 zsh, 并使用 oh-my-zsh 配置 zsh

## 安装 zsh

```shell
sudo pacman -S zsh
```

## 安装 oh-my-zsh

```shell
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

## 安装 zsh-autosuggestions 插件

1. 把插件下载到本地的 `~/.oh-my-zsh/custom/plugins` 目录：

```shell
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

2. 在 `.zshrc` 中，把 `zsh-autosuggestions` 加入插件列表：

```text
plugins=(
    # other plugins...
    zsh-autosuggestions  # 插件之间使用空格隔开
)
```

3. 开启新的 Shell 或执行 `souce ~/.zshrc`


## 安装 zsh-syntax-highlighting 插件

1. 把插件下载到本地的 `~/.oh-my-zsh/custom/plugins` 目录：

```shell
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

2. 在 `.zshrc` 中，把 `zsh-syntax-highlighting` 加入插件列表：

```text
plugins=(
    # other plugins...
    zsh-autosuggestions
    zsh-syntax-highlighting
)
```

3. 开启新的 Shell 或执行 `souce ~/.zshrc`


