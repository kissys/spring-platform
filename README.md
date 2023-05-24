
实现Gitee和Github仓库的同步操作
https://blog.csdn.net/muxuen/article/details/125360459

https://blog.csdn.net/weixin_44893902/article/details/125147574



https://blog.csdn.net/qq_55558061/article/details/124117445


一、从远程仓同步更新到个人仓（分支）

1、git clone -b xxx分支 xxx个人仓地址（clone个人仓分支到本地）

2、cd xxx/（进入clone项目的根目录）

3、git remote -v（查看origin upstream）
      git remote add upstream xxx远程仓地址（添加上游代码库）

4、git fetch upstream（获取原仓库的更新）

5、git branch（看当前在xxx分支）

6、git merge upstream/xxx分支（将远程仓更新同步到了个人仓）

二、提交代码

1、git add .（添加文件到暂存区）
2、git commit -m "提交描述信息"（提交暂存区到本地仓库）
3、git push（上传远程代码并合并）

三、回退操作

1、用git log查看历史提交记录，然后用git reset --hard commit_id回退（要回退到某个提交之前的版本，就要复制某个提交前一次的提交commit_id）。这个的结果是本地的代码就回退成功了。
2、执行git push origin 分支 --force，这个的结果是远程仓库的提交就回退成功了。

四、合并commit提交

1、用git log查看历史提交记录，查看到具体的提交信息，按q退出。然后执行git rebase -i HEAD~n（n是从当前HEAD开始的前n次提交，要合并几次提交，n就修改为几），第一个commit为pick不修改，后面commit的pick修改为s或squash，报存并退出，然后git push或git push -f。
