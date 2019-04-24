# 简介
Git 是一个开源的分布式版本控制系统，借助git可以对文件进行版本管理，比如：
|版本|文件名|用户|说明|日期|
|---|---|---|---|---|
|1|service.doc|张三|删除了软件服务条款|7/12 10:38|
|2|service.doc|张三|增加了License人数限制|7/12 18:09|
|3|service.doc|李四|财务部门调整了合同金额|7/13 9:51|
|4|service.doc|张三|延长了免费升级周期|7/14 15:17|

Git 是 Linus Torvalds 为了帮助管理 Linux 内核开发而开发的一个开放源码的版本控制软件。

Git 与常用的版本控制工具 CVS，Subversion 等不同，它采用了分布式版本库的方式，不必服务器端软件支持。

# 工作流程

+ 克隆 Git 资源作为工作目录。
+ 在克隆的资源上添加或修改文件。 
+ 如果其他人修改了，你可以更新资源。
+ 在提交前查看修改。
+ 提交修改。
+ 在修改完成后，如果发现错误，可以撤回提交并再次修改并提交。

# Git与SVN的区别
1. Git 是分布式的，SVN 不是：这是 Git 和其它非分布式的版本控制系统，例如 SVN，CVS 等，最核心的区别。
2. Git 把内容按元数据方式存储，而 SVN 是按文件：所有的资源控制系统都是把文件的元信息隐藏在一个类似 .svn、.cvs 等的文件夹里。
3. Git 分支和 SVN 的分支不同：分支在 SVN 中一点都不特别，其实它就是版本库中的另外一个目录。
4. Git 没有一个全局的版本号，而 SVN 有：目前为止这是跟 SVN 相比 Git 缺少的最大的一个特征。
5. Git 的内容完整性要优于 SVN：Git 的内容存储使用的是 SHA-1 哈希算法。这能确保代码内容的完整性，确保在遇到磁盘故障和网络问题时降低对版本库的破坏。

# 参考
+ [官方手册](https://git-scm.com/docs)
+ [Git教程 from 廖雪峰](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)
+ [Git 教程 from 菜鸟教程](http://www.runoob.com/git/git-tutorial.html)
	+ [基本指令](http://www.runoob.com/git/git-basic-operations.html)
	+ [简明指南](http://www.runoob.com/manual/git-guide/)
+ [图解 from marklodato](http://marklodato.github.io/visual-git-guide/index-zh-cn.html)
