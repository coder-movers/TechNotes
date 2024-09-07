## 下载并配置

### 1. 下载

- 官网地址：[https://git-scm.com/download/win/](https://git-scm.com/download/win)
- 选择版本，默认安装

检查版本

```shell
git --version
```



### 2. 配置

配置用户名和邮箱，用户名和邮箱都可以随意写就行

```shell
git config --global user.name lix

git config --global user.email 1234@163.com
```



验证版本

```shell
git config user.name
git config user.email
```



## 回滚操作

### commit了但是还没push

1. 使用git log命令查看最近的commit记录，找到想回滚到的commit id，复制id
2. 输入q，退出查看日志
3. 使用git reset 命令回滚到指定的commit，此时代码会回到指定commit的状态

> 注意:
>
> - git reset命令默认是--mixed参数,即回滚commit但不删除工作区修改。可以加--hard强制回滚工作区修改。
> - 如果已经推送至远程,不能直接回滚本地commit,需要通过revert等操作





## Github拉取代码报错

**remote: Support for password authentication was removed on August 13, 2021. remote: Please see https://docs.github.com/en/get-started/getting-started-with-git/about-remote-repositories#cloning-with-https-urls for information on currently recommended modes of authentication. fatal: Authentication failed for 'https://github.com/KaustubhPatange/Inssocks.git/'**

这个错误提示是因为 GitHub 在2021年8月13日停止了密码身份验证，改为使用基于令牌的身份验证。这意味着需要生成一个访问令牌来访问 GitHub 存储库，而不是使用用户名和密码。

为了解决此问题，可以按照以下步骤生成一个访问令牌：

1. 登录 GitHub 帐户。
2. 点击头像，然后选择“Settings”（设置）。
3. 在左侧菜单中，选择“Developer settings”（开发人员设置）。
4. 在左侧菜单中，选择“Personal access tokens”（个人访问令牌）。
5. 点击“Generate new token”（生成新令牌）。
6. 给令牌起个名称，并选择需要访问的范围。
7. 点击“Generate token”（生成令牌）。
8. 复制生成的令牌并使用它进行身份验证。

一旦有了访问令牌，就可以使用以下命令从 GitHub 拉取代码：

```
git clone 仓库链接
```

当被提示输入用户名和密码时，输入 GitHub 用户名作为用户名，而将令牌用作密码。



## 清空本地缓存的GitHub用户名和密码

```shell
git credential-manager reject github.com
```



### 创建新分支

- 方法一
  1. 打开要创建分支的GitHub仓库页面。
  2. 点击仓库顶部的“Branch”下拉菜单按钮。
  3. 在下拉菜单中输入您希望创建的新分支的名称,然后按回车键。
  4. GitHub会自动基于当前仓库的主分支(通常是master)创建一个新分支。



- 方法二
  1. 在本地克隆仓库后,使用 `git branch <branchname>` 命令创建新分支。
  2. 使用 `git checkout <branchname>` 切换到新分支。
  3. 在新分支上进行代码修改和提交。
  4. 使用 `git push origin <branchname>` 将新分支推送到GitHub远程仓库。



