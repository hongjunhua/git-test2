一、基本操作

1、git --version

2、ls -a  查看文件夹下的内容列表

3、git init 在此文件夹下初始一个仓库

4、ls -a 查看是否多一个 .git的隐藏文件夹

5、git status 查看文件状态是否被追踪

6、git add index.html 命令将文件内容添加到索引(将修改添加到暂存区)。也就是将要提交的文件的信息添加到索引库中。

​	再次书写 git status  就可以看到

​	git有四种状态：

​		untracked:为被追踪

​		Modified:工作区修改了某个文件 但是没有添加到暂存区

​		Staged:把工作区修改的文件添加到了暂存区但是没有提交到版本库

​		Committed:表示数据被安全的储存在本地库中



​	git的三层结构：

​		working directory:工作区

​		staging index:暂存区

​		git directory(Respository):版本库

7、git config --global user.name lipeihua 配置邮箱和帐号

8、git config --global user.email lipeihua0922@163.com

9、git commit -m 'first commit' 提交

10、git log  查看git提交日志



11、git add .  将所有文件提交到暂存区



//修改index.html文件以后

1、git stauts  //modified:   index.html

2、git add index.html

3、git commit -m 'modify index.html'



//再次修改index.html

1、git commit -am 'modify index.html'







二、回退操作

修改index.html 作为最终版本

1、git commit -am 'version 1.0.0'

2、git status

3、git  log --oneline 参数可以将每条日志的输出为一行

但是发现不是最终版本 于是修改index.html

4、git add index.html

4、git commit --amend   改写提交  打开的是vim编辑器   s编辑  esc :eq  保存并退出 取消了上次的提交 保存档次提交

5、git log --oneline



再次修改index.html

7、git status  //发现有变化

8、git checkout -- index.html   检查返回原来

9、git status

再次打开修改的页面 发现已经返回

10、git checkout -- .  也可以使用进行返回所有的





再次修改index.html  为版本2.0

1、git add .

2、git status

此时 发现这次修改不是2.0  想撤销暂存区的内容 恢复以前信息

3、git reset HEAD index.html  //HEAD是头指针 也可以直接使用

##### 4、git status

5、git checkout -- index.html

6、git status



7、git reset cc1d1f06a82 index.html   将某一次拉回暂存区

8、git checkout -- index.html   将暂存区拉到工作区

9、git commit -m 'reste rewirte'

10、git status



再次修改index.html

git add .

git reset HEAD index.html

git checkout -- index.html

发现修改的还原



三、删除操作

在本地删除文件  然后

1、git status

2、git add .

也可以

1、git rm index2.html

2、git status

直接就提交到缓存区了



如果修改了style.css的文件再执行

 git rm style.css

这时会报错，所以可以使用

git rm --cached style.css   在不小心将不需要追踪的文件添加到暂存区 向删除暂存的文件但是不想删除工作区的文件时使用

显示成功  但是工作区的style.css还在

再次 git status







再次：

git reset HEAD style.css

git checkout style.css

git status

git rm -f style.css //无论是否修改  都直接删除



重命名：两种的区别在于是否直接拉到暂存区

mv index.html index1.html

git mv style.css style1.css



四：git分支

git branch  查看分支  *代表当前分支
git branch +（）  创建分支
git checkout +（） 切换分支
git branch  -d +（） 删除分支