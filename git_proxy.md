# 设置 Git 代理

## Git 设置代理（如果有使用全局代理则不需要）

```shell
git config --global http.proxy 'http://127.0.0.1:7890'
git config --global https.proxy 'http://127.0.0.1:7890'
```


## 取消代理

```shell
git config --global --unset http.proxy 'http://127.0.0.1:7890'
git config --global --unset https.proxy 'http://127.0.0.1:7890'
```


## 保存 token 凭证

下次 push 时输入的帐号和密码 (此处密码为 token ) 将自动保存

[生成 token ](https://github.com/settings/tokens)

```shell
git config --global credential.helper store
```
