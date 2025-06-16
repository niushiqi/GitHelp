# 具体使用方法

1. 配置ssh key 在本地创建ssh key
    ```java
    $ ssh-keygen -t rsa -C "your_email@youremail.com"
    //后面的your_email@youremail.com改为你的邮箱，之后会要求确认路径和输入密码，我们这使用默认的一路回车就行。成功的话会在用户下生成.ssh文件夹，进去，打开id_rsa.pub文件，复制里面的key（全部内容）。回到github，进入Account Settings，左边选择SSH Keys，Add SSH Key，title随便填，粘贴key。为了验证是否成功，在git bash下输入：
    $ ssh -T git@github.com
    //如果是第一次的会提示是否continue，输入yes就会看到：You’ve successfully authenticated, but GitHub does not provide shell access 。这就表示已成功连上github。
    ```
1. 设置username和email，因为github每次commit都会记录他们。
    ```java
    $ git config --global user.name "your name"
    $ git config --global user.email "your_email@youremail.com"
    ```

1. 建立远程仓库：要使用git，首先得有一个远程仓库吧，下面是在自己的主页中新建一个远程仓库。建立远程仓库之后会有这样一个页面，点击箭头所指按钮，拷贝仓库地址（这个地址一会要用）。

1. 常用命令
    ```java
    git init //当前的目录变成可以管理的git仓库，生成隐藏.git文件。
    git add XX //把xx文件添加到暂存区去（XX可以使 单独的一个 . 表示添加工作区所有文件）
    git commit -m "XX" //提交文件 XX是这次提交的注释。
    git remote add origin https://github.com/用户id/远程仓库名.git //关联一个远程库
    git push -u(第一次要用-u 以后不需要) origin master //把当前master分支推送到远程库
    git status //查看仓库状态
    git diff XX //查看XX文件修改了那些内容
    git log //查看历史记录
    git log —author=niushiqi //按照名字来看log
    git log -pretty=oneline //查看精简的历史记录
    git log -2 //显示几条记录
    git log -p — 文件名 //显示某个文件所有改动
    git log —graph //显示图表
    git log —name-status //显示文件对应的改动 
    git reset --hard HEAD^/git reset -hard HEAD~ //回退到上一个版本(如果想回退到100个版本，使用git reset –hard HEAD~100)
    git reset HEAD readme.txt //暂存区的修改撤销掉
    git reset -hard 版本号 //回退到任意一次提交状态,-hard会影响工作区
    git reflog //查看历史记录的版本号
    git checkout -- XX //把XX文件在工作区的修改全部撤销(仅仅修改，未add，未commit)。
    git rm XX //删除XX文件
    git clone https://github.com/用户id/远程仓库名.git //从远程库中克隆到本地
    git pull origin master //从远程获取最新版本并merge到本地
    git fetch origin master //相当于是从远程获取最新版本到本地，不会自动merge
    git merge origin/master //进行合并
    git cherry-pick  0128660c08e325d410cb845616af355c0c19c6fe //将某一提交merge进来
    ```

1. 说明
Git的版本库里存了很多东西，其中最重要的就是称为stage（或者叫index）的暂存区，还有Git为我们自动创建的第一个分支master，以及指向master的一个指针叫HEAD。

1. 分支管理/标签管理

1. 常见问题
    1.出现Merge branch 'dev' of github.com:qdraul/chatmore into dev
        解决方法：https://www.cnblogs.com/Sinte-Beuve/p/9195018.html
