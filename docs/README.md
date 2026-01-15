# 用 Github + Markdown 创建个人网站

本文档描述如何通过 Github + Markdown 创建网站。大致步骤如下：
1. 在 github 上创建 **账号 account**。已有账号了，可跳过此步骤。以下以账号 gdvzz 为例。
<!--  -->
2. 在 github 账号下新建 **仓库 repository**，用于存放网站的文档、图片等内容。以下以仓库 wsdemo 为例。
<!--  -->
3. 在 github 账号下添加 **SSH key**（以保证只有你能更新网站的内容）：
  - 在本地电脑生成 SSH key
  - 在本地电脑配置 github 主机信息
  - 在本地电脑测试是否能通过 ssh 连接到 github 账号
<!--  -->
4. 在本地电脑配置 github 仓库信息（以便从本地电脑不断更新网站内容）：
  - 初始化本地电脑目录
  - 配置 github 仓库信息

## 网站效果

待补充

## 在 github 上创建账号 account

## 在 github 账号下添加 SSH key

```
# github - gdvzz@outlook.com
Host githubvzz.com
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_ed25519_gdvzz_olk
```

```bash
~ % ssh -T git@githubvzz.com
Hi gdvzz! You've successfully authenticated, but GitHub does not provide shell access.
```

## 在本地电脑配置 github 仓库信息

```bash
~ % mkdir -p gdvzz/wsdemo
```

```bash
~ % cd gdvzz/wsdemo
~/gdvzz/wsdemo % git init
Initialized empty Git repository in /Users/george1442/gdvzz/wsdemo/.git/
```