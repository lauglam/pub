# Windows 下 Rust 的安装

记录 Rust 安装相关的流程、需要用到的命令和代码

## Windows 环境下使用 gnu 工具链

在 Windows 环境下，Rust 默认使用 MSVC 作为编译器。但安装 VS 空间占用大且没有必要，所以选用 MinGW

* 下载 Rust

> <https://www.rust-lang.org/>

* 点击安装，选择第 3 个选项

```shell
3) Don't install the prerequisites
   (if you're targetting the GNU ABI).
```

* 再选择第 2 个选项

```shell
2) Customize installation
```

* 输入

```shell
x86_64-pc-windows-gnu
```

## 安装 msys2

* 下载 msys2

> <https://www.msys2.org/>

* 使用命令安装 MinGW64

```shell
pacman -S mingw-w64-x86_64-toolchain
```

## 配置 cargo 国内源和 gnu 的 linker

* 打开 .cargo 目录，新建 config 文件

```text
[source.crates-io]
registry = "https://github.com/rust-lang/crates.io-index"
# 指定镜像
replace-with = '镜像源名' # 如：tuna、sjtu、ustc，或者 rustcc

# 注：以下源配置一个即可，无需全部

# 中国科学技术大学
[source.ustc]
registry = "git://mirrors.ustc.edu.cn/crates.io-index"

# 上海交通大学
[source.sjtu]
registry = "https://mirrors.sjtug.sjtu.edu.cn/git/crates.io-index"

# 清华大学
[source.tuna]
registry = "https://mirrors.tuna.tsinghua.edu.cn/git/crates.io-index.git"

# rustcc社区
[source.rustcc]
registry = "https://code.aliyun.com/rustcc/crates.io-index.git"

[target.x86_64-pc-windows-gnu]
linker = "C:\\msys2\\mingw64\\bin\\gcc.exe"
ar = "C:\\msys2\\mingw64\\bin\\ar.exe"
```
