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



	
