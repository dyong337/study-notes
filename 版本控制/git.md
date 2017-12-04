git# Git
##	Git
##	上传到github仓库
	1、生成本地公钥，id-rsa.pub
		私钥，id-rsa
	指令：ssh-keygen -t rsa -C
	
	2、登录github，点自己头像，
		setting→ssh and GPG keys→New ssh key，打开刚刚创建的公钥，
		公钥的内容复制进去，点击add SSHkey
	
	3、ssh -T git@github.com可以查看公钥状态

	4、
	echo "# mianla" >> README.md
	git init
	git add README.md
	git commit -m "first commit"
	git remote add origin git@github.com:zhongjunhui/mianla.git
	git push -u origin master
	
	tips：更改url
		git remote set-url origin URL
	
	tips：如果你要让他可以commit，有两个办法：
		1、让他fork一份你的项目，改好了再pull request，你测试没问题后merge。
		2、你在项目settings的Collaborators这里，把他的github账号加入Collaborators。
	
	tips：忽略不必要的文件
		1、在需要创建  .gitignore 文件的文件夹, 右键选择Git Bash 进入命令行，进入项目所在目录。
		2、输入 touch .gitignore 在文件夹就生成了一个“.gitignore”文件。
	
##	回退
	1、如果需要回退到指定版本。
	git log			查看当前的提交版本信息
	git log -g		显示所有版本
					将需要回退到的那个版本的信息的commitID复制。

	git reset --hard 刚刚复制的版本号		即可回退到指定版本

	2、如果需要将暂存区的内容恢复到指定目录
	git checkout 文件夹名

	tips：该操作是git add的回退操作，将git add的内容释放。

##	分支
	git branch 分支名		创建分支
		eg:
			git branch -d 分支名			创建并切换到该分支
			git branch 分支名 版本号		创建一个分支，并回滚到指定版本号

	git checkout 分支名		切换到指定分支
		eg:
			git checkout master		切换到主分支

	git branch 			查看当前分支

	git merge 分支名
		tips:在master分支下使用该命令，可以将分支合并到master分支。
	
##	远程主机
	git remote 			显示所有远程主机名
	git remote show		

	git remote add 自定义名称 远程仓库地址		添加远程仓库地址，保存到自定义名称这个变量中

	git remote remove 自定义名称		将该自定义名称的远程仓库删除

##跟新本地版本库
git fetch origin dy
##拉取到本地
git pull origin dy  

##廖雪峰git笔记摘要:https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000
1. git
	是目前世界上最先进的分班时版本控制系统（没有之一）
2. 集中式版本控制系统（cvs（收费）、SVN（免费））
	1. 版本库是集中存放在中央服务器的，工作时，从中央服务区获取最新的版本，然后工作；工作完成，再把自己的活推送到中央服务器。
	2. 必须联网擦能工作。
3. 分布式版本控制系统
	1. 没有中央服务器，每个人的电脑上都是一个完成的版本；
	2. 安全性搞很多，每个电脑都有完整的版本库。而中央服务器出现问题，所有人没法干活
	3. 也有中央服务器，但是作用仅仅方便“交换”大家的修改；
	4. 强大的分支管理
	5. 快、简单、流行

5. 安装 
设置：默认配置(全局配置)
	git config --global user.name "Your Name"
	git config --global user.email "email@example.com"
	单独配置：等等等等等等等等等等等等等等
创建版本库(Repository)：
    mkdir learngit
	cd learngit 
	pwd     //显示当前目录 
	git init //把当前目录变成git可以管理的仓库
	文件 .git，这个目录是Git来跟踪管理版本库的,默认是隐藏的
	ls -ah //可以查看到隐藏目录
注意：
	1. 对于二进制文件，虽然也能由版本控制系统管理，但是没法跟踪文件的变化，只能把二进制文件每次改动串起来，也就只知道图片从100kb编程120kb，但是改了啥，版本控制系统不知道(图片，视频、word格式文档都是二进制文件)
	2. 编码：强烈推荐使用标准的UTF-8编码，避免编码冲突，又被素有平台支持；
		千万不要使用Windows自带的记事本编辑任何文本文件。原因是Microsoft开发记事本的团队使用了一个非常弱智的行为来保存UTF-8编码的文件，他们自作聪明地在每个文件开头添加了0xefbbbf（十六进制）的字符，你会遇到很多不可思议的问题，比如，网页第一行可能会显示一个“?”，明明正确的程序一编译就报语法错误，等等，都是由记事本的弱智行为带来的。建议你下载Notepad++代替记事本，不但功能强大，而且免费！记得把Notepad++的默认编码设置为UTF-8 without BOM即可：
添加文件到git:
	git add readme.txt //Unix的哲学是"没有消息就是好消息"
	git add file1.txt file2.txt
添加到仓库
	git commit -m "wrote readme file"

git status：可以查看仓库当前的状态，
git diff readme.txt:查看文件修改

	1. 要随时掌握工作区的状态，使用git status命令。

	2. 如果git status告诉你有文件被修改过，用git diff可以查看修改内容。

版本回退：

git log:显示最近到最远的提交日志
git log --pretty=oneline：简化输出信息
HEAD:标识当前版本
上一个版本：HEAD^
上上一个版本：HEAD^^
往上100个版本:HEAD~100
git reset:回退到命令
	git reset --hard HEAD^//回退到上一个版本
git reset --hard 3628184(commit id)		//回到指定版本

git reflog:记录了每一条命令

	小结


	HEAD指向的版本就是当前版本，因此，Git允许我们在版本的历史之间穿梭，使用命令git reset --hard commit_id。
	
	穿梭前，用git log可以查看提交历史，以便确定要回退到哪个版本。
	
	要重返未来，用git reflog查看命令历史，以便确定要回到未来的哪个版本。
	
	





	
