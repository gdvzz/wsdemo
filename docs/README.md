# 用 Github + Markdown 创建个人网站

本文档描述如何通过 Github + Markdown 创建个人网站。

- 网页内容。在本地电脑上通过编写 markdown 文档实现的。
- 网页更新。本地电脑执行 `git push` 推送到 github.com 即可。
- 网站访问。在浏览器输入 `<github账号名>.github.io/<该账号下的一个仓库名>`。

网站样例请访问：[https://gdvzz.github.io/wsdemo/](https://gdvzz.github.io/wsdemo/)

## 主要步骤



主要步骤如下：
- [创建 github 账号account](#创建-github-账号account)。已有账号了，可跳过此步骤。
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

本文以如下信息为样例：
- 账号：`gdvzz`
- 仓库：`wsdemo`

## 创建账号（account）

创建 github 账号（account），此处从略。有几点信息：

- 可注册新邮箱，专门用于创建 github 账号
- 创建基本完成时，要做 visual puzzle 或 audio puzzle，证明





## 新建仓库（repository）

登录 github 网站后新建**仓库（repository）**:
- 输入**仓库名称（Repository name）**，比如 `wsdemo`
- 可以写一些**描述（Description）**
- **Choose visibility**：`Public`

然后按底部按钮 **Create repository** 即可。如下图所示：
[![new_repo](./readme.assets/new_repo.png)](./readme.assets/new_repo.png)

## 添加 SSH key

需要在 github 账号下添加 ssh key，以保证只有授权用户才能更新网站内容。

### 生成 ssh 密钥对

根据参考资料 [^1]，执行如下命令，生成新的 key。

```bash
~/gdvzz/wsdemo % ssh-keygen -t ed25519 -C "gdvzz@outlook.com"
Generating public/private ed25519 key pair.
Enter file in which to save the key (/Users/george1442/.ssh/id_ed25519): id_ed25519_gdvzz_olk
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in id_ed25519_gdvzz_olk
Your public key has been saved in id_ed25519_gdvzz_olk.pub
The key fingerprint is:
SHA256:... gdvzz@outlook.com
The key's randomart image is:
...
```

> **说明：**
> - 命令中的 `"gdvzz@outlook.com"`，请换成你自己的邮箱（一般是用于注册 github 账号的邮箱）。
> - `Enter file in which to save the key: `，要保存为其他文件名，则要输入完整的路径名，否则保存在当前目录下。

通过上述命令生成了 ssh 密钥对，共 2 个文件，如下所示。以 `.pub` 结尾的文件是公钥，稍后粘贴到 github 账号的配置中。`id_ed25519_gdvzz_olk` 是私钥，请如同口令密码之类的保存好，不要让其他人知道。

```
~/.ssh % ls -la *ed25519*
-rw-------  1 george1442  staff  411 Jan 15 13:28 id_ed25519_gdvzz_olk
-rw-r--r--  1 george1442  staff   99 Jan 15 13:28 id_ed25519_gdvzz_olk.pub
```

### 添加公钥到 githuab账号下

1. 回到 github 网站，点击右上角账号图标，再选择 **设置（setting）**。

2. 在设置页面，找到
![account_sshkeys](./readme.assets/account_sshkeys.png)

```bash
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
在 `~/gdvzz/wsdemo/docs` 目录中，编辑生成文档 `README.md`。

```bash
~/gdvzz/wsdemo % git status
~/gdvzz/wsdemo % git add .
~/gdvzz/wsdemo % git branch -M master
~/gdvzz/wsdemo % git remote add origin git@githubvzz.com:gdvzz/wsdemo.git
~/gdvzz/wsdemo % git push -u origin master
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 4 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (4/4), 1000 bytes | 1000.00 KiB/s, done.
Total 4 (delta 0), reused 0 (delta 0), pack-reused 0
To githubvzz.com:gdvzz/wsdemo.git
 * [new branch]      master -> master
branch 'master' set up to track 'origin/master'.
```

## 更新网站


## 编写说明

- **图片**
  - 建议使用 tinyPNG 压缩，上传压缩后的版本到个人网站。tinyPNG：[中文官网](https://tinify.cn/)，[英文官网](https://tinypng.com/)。
  - 压缩后效果几乎不变，但图片文件变小了，在打开网站显示时会更快。

## 其他说明

1、校园网内访问 github，时灵时不灵。当连接不上时，可尝试断开校园网的 wifi 后再重连，一般就可以了。本文档涉及的 github 相关操作，都是连校园网的 wifi 完成的。

2、校园网内可访问演示网站 `https://gdvzz.github.io/wsdemo/`。如果是手机 5G 网络访问，可能无法访问。

## 参考资料

[^1]: [Generating a new SSH key and adding it to the ssh-agent](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent), Github Docs
