# 简介

GitHub 是一个基于 Git 的代码托管平台，付费用户可以建私人仓库，免费用户只能使用公共仓库，也就是代码要公开。

# 连接和克隆
```bash
$ ssh-keygen -t rsa -C "emailname" # 在本地创建ssh key
$ ssh -T git@github.com # 验证是否连接成功
$ git remote add origin git@github.com:yourName/yourRepo.git # 连接远程地址，origin是默认的repo名
$ git clone username@host:/path/to/repository # 克隆仓库到本地目录下（无需git init）
```

# 修改、提交和推送
在添加和提交完文件修改后的操作：
```bash
$ git push origin <branch> # 推送改动
$ git pull # 更新本地仓库至最新改动，等于 git fetch + git merge
	$ git fetch <repo> # 从远程仓库下载新分支与数据，执行完后需要执行git merge
	$ git merge <repo>/<branch> # 合并远程分支
```

# 其他命令
```bash
$ git remote # 显示连接的远程仓库
	$ git remote -v # 显示详细信息
	$ git remote rm <repo> # 删除与远程仓库的连接
```

