#什么是git？

>git是分布式版本控制系统，其实可以这么理解，在我们的本地有一个代码库，写完代码后，会保存到本地库中，然后执行git命令，将代码上传到代码托管的网站上（coding,github,oschina等），每次更新代码都会有提交记录，记录每次修改的代码部分。可以多个分支多人协作开发，然后合并代码，提高开发效率。

#创建ssh（使用ssh进行clone代码，不需要输入密码）

>输入命令后三次回车即可

```shell

    ssh-keygen -t rsa -C email

    cat ~/.ssh/id_rsa.pub #查看生成的ssh
```



#配置全局变量

>生成ssh key后，将sshkey添加到github的sshkey中，然后使用git配置以下全局变量

```shell

git config --global  user.name name #用户名

git config --global  user.email email #邮箱

git config  -l #列举所有配置

```

#本地仓库与远程仓库
>首先在github上创建一个远程仓库，（如果在创建仓库的时候添加了.gitignore或者README.md的时候，本地仓库要先pull一次）然后在本地创建一个相同名称的文件夹（eg:learnGit）。
```shell
cd learnGit#进入到要变成本地仓库的文件夹
git init#初始化 自动创建唯一一个master分支
echo "hello world" > README.md#创建readme文件
git remote add origin git_url # origin 我们的远程库的名字，默认为origin git_url是我们远程仓库的路径
git add . #添加所有已改变的文件
git status #查看 文件状态  绿色的为已经添加到本地仓库的文件 红色的为未添加的文件
git commit -m "first commit" #把文件提交到本地仓库
git pull origin master # 拉取远程仓库的代码
git push origin master # 将改变的文件推送到远程仓库 orign 远程库的名字 master 分支
```
>以上你的第一次git操作基本完成了。这个时候去github上刷新你的仓库，就能够看到你刚刚提交的文件了。
#总结（默认已经配置了 ssh）
+ 初始化一个本地git仓库，将本地文件夹初始化为一个版本库
```shell
git init
```
+ 添加改变的文件
```shell
git add . /git add file_name #提交所有改变的文件或者只提交确定的文件
```
+ 将修改的文件提交到本地仓库
```shell
git commit -m "commit"
```
+ 关联到远程仓库
```shell
git remote add origin git_url
```
+ 拉取远程仓库中的文件
```shell
git pull origin master
```
+ 将修改的文件推送的远程仓库
```shell
git push origin master
```
+ git pull时出现 “refusing to merge unrelated histories” 执行以下命令后在git pull
```shell
git pull origin master --allow-unrelated-histories 
```

