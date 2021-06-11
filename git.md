# Git

# 剩余任务

- [x] ~~配置忽略文件、常见忽略模板~~
- [ ] 配置单个仓库ssh、多个ssh
- [ ] 修改author名称、邮箱

# 概述

:sparkles:所有资料均来自[^1]

**Git目录**

<center>
    <img style="background-color:white;border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://www.git-scm.com/book/en/v2/images/areas.png" width = "60%" alt=""/>
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">
      图1-Git目录
  	</div>
</center>


| 术语           | 实际 |  用途    |  模样  |
| -------------- | ---- | ---- | ---- |
| WorsDirectory  | 磁盘实际的文件夹 | 使用开发工具编写代码的区域 | 磁盘目录/ |
| StagingArea    | 磁盘文件夹下暂存区 | add后，文件存储的位置 | .git/index文件 |
| .git directory | 磁盘文件夹 | commit后，文件存储的位置 | 磁盘目录/.git目录 |
| Remote         | 仓库，代指远程仓库 | 远程仓库别名绰号 | .git/refs/remotes |
| Repository | 仓库区,包括本地仓库和远程仓库 | 本地仓库、远程仓库的别名绰号 | git/refs/heads/ |

<center>
    <img style="background-color:white;border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="http://www.ruanyifeng.com/blogimg/asset/2015/bg2015120901.png" width = "60%" alt=""/>
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">
      图2-Git目录
  	</div>
</center>



| 名称                                | <span style="width:35">含义</span> | 用途                                                         |
| ----------------------------------- | ---------------------------------- | ------------------------------------------------------------ |
| .git/                               |                                    | 根目录                                                       |
| hooks/                              |                                    | 存放一些shell脚本                                            |
| info/                               |                                    | 包含git仓库的一些信息                                        |
| logs/                               |                                    | 保存所有更新的引用记录                                       |
| objects/                            |                                    | 存放所有的 git 对象<br>哈希值一共40位，前 2 位作为文件夹名称，后 38 位作为对象文件名 |
| refs/                               | 文件夹                             | 存放引用                                                     |
| refs/heads                          | 本地分支文件夹                     | 存放存储了每个分支当前指向的commit id                        |
| refs/remotes/                       | 远程仓库分支文件夹                 | 子文件夹内，存放了多个远程仓库下的每个分支，并且该分支当前指向的commit id |
| refs/tags/                          | 存放里程碑内容                     | 子文件夹内，存放了多个远程仓库下的每个分支，并且该分支当前指向的commit id |
| COMMIT_EDITMSG                      |                                    |                                                              |
| <font color="red">**config**</font> | 配置文件                           | 保存当前仓库的配置信息                                       |
| description                         | 描述文件                           | 仓库的描述信息                                               |
| FETCH_HEAD                          |                                    |                                                              |
| HEAD                                | HEAD指针                           | 指向了当前分支                                               |
| index                               | 暂存区（stage）                    | 是一个二进制文件                                             |
| ORIG_HEAD                           |                                    |                                                              |
| packed-refs                         |                                    |                                                              |





# 创建

| 用途                       |                         |
| -------------------------- | ----------------------- |
| 将当前目录创建代码库       | git init                |
| 创建一个目录并且当作代码库 | git init [project-name] |
| 克隆远程到本地作为代码库   | git clone [url]         |

# 分支

## 分支查看

| 用途                       | 用法          |
| -------------------------- | ------------- |
| 列出所有本地分支           | git branch    |
| 列出所有远程分支           | git branch -r |
| 列出所有本地分支和远程分支 | git branch -a |


## 分支创建

| 用途                                                         | 用法                                        |
| ------------------------------------------------------------ | ------------------------------------------- |
| 新建一个分支，但依然停留在当前分支                           | git branch [branch-name]                    |
| <font color="red">新建一个分支，与指定的远程分支建立追踪关系</font> | git branch --track [branch] [remote-branch] |
| 新建一个分支，并切换到该分支                                 | git checkout -b [branch]                    |
| 新建一个分支，指向指定commit                                 | git branch [branch] [commit]                |

## 分支链接

| 用途                                       | 用法                                               |
| ------------------------------------------ | -------------------------------------------------- |
| 新建一个分支，与指定的远程分支建立追踪关系 | git branch --set-upstream [branch] [remote-branch] |
| 在现有分支与指定的远程分支之间建立追踪关系 | git branch --track [branch] [remote-branch]        |



## 分支切换

| 用途                                      | 用法                       |
| ----------------------------------------- | -------------------------- |
| 切换到指定分支，并更新工作区              | git checkout [branch-name] |
| <font color="red">切换到上一个分支</font> | git checkout -             |

## 分支合并

| 用途                           | 用法                     |
| ------------------------------ | ------------------------ |
| 合并指定分支到当前分支         | git merge [branch]       |
| 选择某一个分支的commit id，合并进当前分支 | git cherry-pick [commit] |

## 分支删除

| 用途         | 用法                                   |
| ------------ | -------------------------------------- |
| 删除分支     | git branch -d [branch-name]            |
| 删除远程分支 | git push origin --delete [branch-name] |



# 标签

标签在频繁发版的时候作用挺大的

| 用途                      | 用法                                 |
| ------------------------- | ------------------------------------ |
| 列出所有tag               | git tag                              |
| 新建一个tag在当前commit   | git tag [tag]                        |
| 新建一个tag在指定commit   | git tag [tag] [commit]               |
| 删除本地tag               | git tag -d [tag]                     |
| 删除远程tag               | git push origin :refs/tags/[tagName] |
| 查看tag信息               | git show [tag]                       |
| 推送指定tag至远程分支     | git push [remote] [tag]              |
| 推送所有tag               | git push [remote] --tags             |
| 新建一个分支，指向某个tag | git checkout -b [branch] [tag]       |



# 增加

| 用途                                     | 用法                                         |
| ---------------------------------------- | -------------------------------------------- |
| 增加指定路径的文件或文件夹至暂存区       | git add [file1] [file2] ...<br>git add [dir] |
| 增加所有文件至暂存区                     | git add .                                    |
| 增加至暂存区，并逐个确认                 | git add -p                                   |
| 删除工作区文件，并且将删除记录存入暂存区 | git rm [file1] [file2] ...                   |
| 改名工作区文件，并且将改名记录存入暂存区 | git mv [file-original] [file-renamed]        |

# 提交

| 用途                                     | 用法                                        |
| ---------------------------------------- | ------------------------------------------- |
| 将暂存区内容提交至仓库区                 | git commit -m [message]                     |
| 将暂存区的指定内容提交至仓库区           | git commit [file1] [file2] ... -m [message] |
| 提交时显示所有diff信息                   | git commit -v                               |
| 新的commit，替代上一次提交               | git commit --amend -m [message]             |
| 重做上一次commit，并包括指定文件的新变化 | git commit --amend [file1] [file2] ...      |

# 查看

| 用途                                                         | 用法                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| 显示今天你写了多少行代码                                     | git diff --shortstat "@{0 day ago}"                          |
| 显示当前分支的版本历史                                       | git log                                                      |
| 搜索提交历史，根据关键词                                     | git log -S [keyword]                                         |
| 会显示每次提交所引入的差异                                   | git log -p -2<br>-p是按照补丁格式输出<br>-2是显示的最近几笔提交数量 |
| 会显示最近指定时间开始的提交                                 | git log --since=2.weeks<br>指定2周前                         |
| 显示有变更的文件                                             | git status                                                   |
| [显示有变更的文件夹及子文件](http://schacon.github.io/git/git-status.html) | git status -u<br>git status --untracked-files                |
| 显示指定文件的版本历史                                       | git log --follow [file]                                      |
| 显示过去5次提交                                              | git log -5 --pretty --oneline                                |
| 显示所有提交过的用户，按提交次数排序                         | git shortlog -sn                                             |
| 显示指定文件是什么人在什么时间修改过                         | git blame [file]                                             |



# 编辑

## 编辑当前代码库配置

```bash
git config -e 
```

编辑全局代码库配置

```bash
git config -e [--global]
```

# 同步

| 用途                                   | 用法                             |
| -------------------------------------- | -------------------------------- |
| 下载远程仓库的所有变动                 | git fetch [remote]               |
| 显示所有远程仓库                       | git remote -v                    |
| 显示某个远程仓库的信息                 | git remote show [remote]         |
| 增加一个新的远程仓库，并命名           | git remote add [shortname] [url] |
| 取回远程仓库的变化，并与本地分支合并   | git pull [remote] [branch]       |
| 上传本地指定分支到远程仓库             | git push [remote] [branch]       |
| 强行推送当前分支到远程仓库，即使有冲突 | git push [remote] --force        |
| 推送所有分支到远程仓库                 | git push [remote] --all          |


# 撤消

| 用途                                                        | 用法                       |
| ----------------------------------------------------------- | -------------------------- |
| <font color="red">恢复暂存区的指定文件到工作区</font>       | git checkout [file]        |
| 恢复暂存区的所有文件到工作区                                | git checkout .             |
| 重置暂存区的指定文件，与上一次commit保持一致，但工作区不变  | git reset [file]           |
| 重置暂存区与工作区，与上一次commit保持一致                  | git reset --hard           |
| <font color="red">暂时将未提交的变化移除，稍后再移入</font> | git stash<br>git stash pop |




# 配置

## 命令配置信息

### 查看配置信息

方式1：

```shell
git config --list
```

可以用于查询所有能找到的配置。

!> 如果有重复变量，则使用每一个变量的最后一次赋值

方式2：

```shell
 git config --show-origin <key>
```

如 git config --show-origin rerere.autoUpdate

### 查看config的帮助

```shell
git config
```

### 查看help的帮助

```shell
git help
```

查看指定命令的帮助

```shell
git help <verb>
git <verb> --help 
```

示例

```shell
 git help diff
```

**效果**

会自动弹出diff的使用文档，而且是本地文件哦。

### 配置单个仓库的秘钥

?>git config 配置的 3 个级别

```js
--system # 系统级别，位于 /etc/gitconfig 下对影响该系统下所有用户
--global # 用户级别，位于 ~/.gitconfig 下，仅影响该用户
--local  # 仓库级别，位于仓库的 .git/config ， 仅影响该仓库
 注意 ： git config [--local] user.name "xxx" 默认就是 --local 可不填
```

**1.生成新的id_rsa文件**

```shell
ssh-keygen -t rsa -C "xxx@xx.com" -b 4096 
```

生成后手动修改名字为github_rsa

**2.添加密钥至ssh中**

```powershell
ssh-add C:/Users/username/.ssh/github_rsa # 添加
ssh-agent bash # 如果出现错误提示 Could not open a connection to your authentication agent
```

**3.测试SSH配置是否可用**

```shell
ssh -T gti@gtihub.com #如果仓库地址是github，测试这个
```



### **配置用户信息**

| 名称               | 公式                                               |
| ------------------ | -------------------------------------------------- |
| 配置全局名称       | git config --global user.name "John Doe"           |
| 配置全局邮箱       | git config --global user.email johndoe@example.com |
| 配置当前项目的名称 | git config  user.name "John Doe"                   |
| 配置当前项目的邮箱 | git config  user.email johndoe@example.com         |

### 配置忽略模板

参考[^3]

**方式1编辑文件**,位置在`根目录.git\info\exclude`

?>必须写针对根目录的全路径

**方式2编辑器插件如AndroidStudio、VStudio**

以androidstudio为例

安装：File->Settings ->Plugins-search .ignore-> install and restart

创建：File->New->ignore.file->select target template

**模板语法**

`空格`不匹配任意文件，可作为分隔符，可用反斜杠转义

`# `开头的文件标识注释，可以使用反斜杠进行转义

`! `开头的模式标识否定，该文件将会再次被包含，如果排除了该文件的父级目录，则使用 ! 也不会再次被包含。可以使用反斜杠进行转义

`/ `结束的模式只匹配文件夹以及在该文件夹路径下的内容，但是不匹配该文件

`/ `开始的模式匹配项目跟目录
如果一个模式不包含斜杠，则它匹配相对于当前 .gitignore 文件路径的内容，如果该模式不在 .gitignore 文件中，则相对于项目根目录

`** `匹配多级目录，可在开始，中间，结束

`? `通用匹配单个字符

`[] `通用匹配单个字符列表

### 配置提交模板

commit模板参考[^2]

**步骤1：在任意位置创建gitmessage.txt文件**

按照如下格式编辑内容

```js
<type>(<scope>): <subject>
<BLANK LINE>
<body>
<BLANK LINE>
<footer>
      
```

**type: commit 的类型（必填）**

```js
feat: 新特性
fix: 修改问题
refactor: 代码重构
docs: 文档修改
style: 代码格式化的修改如缩进/去空格/增删分号, 注意不是 css 修改
test: 测试用例修改
chore: 不修改src或者test的其他修改, 比如构建流程, 依赖管理.
perf: 提高性能的改动
ci: 与CI持续集成的服务的有关改动
scope: commit 影响的范围（选填）, 比如: route, component, utils, build…
subject: 提交简述（必填）
```

**scope**

```js
scope用于说明 commit 影响的范围，比如数据层、控制层、视图层等等，视项目不同而不同。

例如在`Angular`，可以是`$location`, `$browser`, `$compile`, `$rootScope`, `ngHref`, `ngClick`, `ngView`等。

如果你的修改影响了不止一个`scope`，你可以使用`*`代替。
```

**subject（必填）**

```js
  subject`是 commit 目的的简短描述，不超过50个字符。
  
  其他注意事项：
  
  - 以动词开头，使用第一人称现在时，比如change，而不是changed或changes
  - 第一个字母小写
  - 结尾不加句号（.）
```

**body: commit 具体修改内容（选填）**
可以分为多行

**footer: 一些备注（选填）**
通常是 BREAKING CHANGE 或修复的 bug 的链接.

如公司定制：

```js
# header
fix: HomeActivity onCreate (/packname/activity/HomeActivity)
# body
Added new view to HomeActivity
- forward popstate event if available
- forward hashchange event if popstate not available
- do polling when neither popstate nor hashchange available
#footer
Closes #351,#233,#222
```

**步骤2：配置当前仓库使用模板**

```js
[commit]
        template = D:/worspace/.gitmessage.txt
```

每家公司可以定制自己的commit格式，如华为、海尔是偏向这种风格的

```js
[提交类型]:
[修改对象]:
[影响范围]：
[修改描述]:
[变化]:
```

推荐直接以下复制到txt里

```xml
<type>(<scope>): <subject>
<BLANK LINE>
<body>
<BLANK LINE>
<footer>

#<type>
#feat: 新特性
#fix: 修改问题
refactor: 代码重构
#docs: 文档修改
#style: 代码格式化的修改如缩进/去空格/增删分号, 注意不是 css 修改
#test: 测试用例修改
#chore: 不修改src或者test的其他修改, 比如构建流程, 依赖管理.
#perf: 提高性能的改动
#ci: 与CI持续集成的服务的有关改动
#scope: commit 影响的范围（选填）, 比如: route, component, utils, build…
#subject: 提交简述（必填）

#<scope> 
#scope用于说明 commit 影响的范围，比如数据层、控制层、视图层等等，视项目不同而不同。
#例如在`Angular`，可以是`$location`, `$browser`, `$compile`, `$rootScope`, `ngHref`, `ngClick`, `ngView`等。
#如果你的修改影响了不止一个`scope`，你可以使用`*`代替。
#subject（必填）
#subject`是 commit 目的的简短描述，不超过50个字符。
# 其他注意事项：
# - 以动词开头，使用第一人称现在时，比如change，而不是changed或changes
#  - 第一个字母小写
# - 结尾不加句号（.）

#<body>
#可以未多行

#<footer>
#通常为bug链接
#Change描述
```



### 配置提交者姓名

```shell
git commit --amend --author "xxx@abc.cn"
```

### 修改git已提交记录的author和email

把`OLD_EMAIL`、`CORRECT_NAME`、`CORRECT_EMAIL`改成自己的新旧邮箱用户名即可

```shell
#!/bin/sh

git filter-branch --env-filter '

OLD_EMAIL="old@old.com"
CORRECT_NAME="newname"
CORRECT_EMAIL="newname@newname.com"

if [ "$GIT_COMMITTER_EMAIL" = "$OLD_EMAIL" ]
then
    export GIT_COMMITTER_NAME="$CORRECT_NAME"
    export GIT_COMMITTER_EMAIL="$CORRECT_EMAIL"
fi
if [ "$GIT_AUTHOR_EMAIL" = "$OLD_EMAIL" ]
then
    export GIT_AUTHOR_NAME="$CORRECT_NAME"
    export GIT_AUTHOR_EMAIL="$CORRECT_EMAIL"
fi
' --tag-name-filter cat -- --branches --tags
```

执行该sh脚本即可

### 配置编辑器

```shell
git config --global core.editor "'D:/program/Notepad++/notepad++.exe' -multiInst -notabbar -nosession -noPlugin"
```



## 手动编辑配置文件

**C:/Users/username/.gitconfig配置**

```
[user]
	name = 
	email = 
[core]
	quotepath = false

```



**/.git/config配置**

```shell
[core]
	repositoryformatversion = 0
	filemode = false
	bare = false
	logallrefupdates = true
	symlinks = false
	ignorecase = true
[remote "origin"]
	url = https://gitee.com/xxx.git
	fetch = +refs/heads/*:refs/remotes/origin/*
[branch "master"]
	remote = origin
	merge = refs/heads/master
```

客户端默认使用git bash

## 配置支持中文显示

方式1

!>可以解决git bash 中文乱码

```shell
窗口右键->Options->Text->Locale改为zh_CN，Character set改为UTF-8
```

方式2

!>可以解决git bash 中文乱码

```shell
git config --global core.quotepath false 
```

方式3

!>可以解决commit包含中文，自动乱码的情况

```shell
git config --global i18n.commitencoding utf-8    #如果是GBK 请换成gbk
git config --global i18n.logoutputencoding utf-8   #如果是GBK 请换成gbk
export LESSCHARSET=utf-8
```

方式4

!>有时候乱码是因为原文件编码格式是错误的，如git提交模板经常读取乱码

另存为改源文件的编码即可：使用记事本打开->另存为->选择编码设置为Utf-8

# 参考

?><br>
[^1]: [Git - 关于版本控制](https://www.git-scm.com/book/zh/v2/起步-关于版本控制)  <br>
[^2]: [Commit message 和 Change log 编写指南](http://www.ruanyifeng.com/blog/2016/01/commit_message_change_log.html) <br>
[^3]: [Google gitignore模板](https://github.com/github/gitignore) <br>
 
