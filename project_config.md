# 新建项目时的配置

新建项目相关的配置

## Git Commit 全局配置

[Angular 团队规范](https://github.com/angular/angular.js/blob/master/DEVELOPERS.md#-git-commit-guidelines)衍生而来的 [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/)

git 项目提交的信息进行配置，让提交信息可阅读性增加

提交格式：

```text
<type>(<scope>): <subject>
< 空一行 >
<body>
< 空一行 >
<footer>
```

* 安装 [Commitizen](https://github.com/commitizen/cz-cli#conventional-commit-messages-as-a-global-utility)

```shell
sudo npm install -g commitizen
```

* 全局安装适配器（也可以项目本地安装）

```shell
sudo npm install -g cz-conventional-changelog
```

* 将适配器路径写入`.czrc`文件

```shell
echo '{ "path": "cz-conventional-changelog" }' > ~/.czrc
```

* 使用`git cz`替代`git commit`

```shell
git cz
```

## Vue.ts 项目配置





