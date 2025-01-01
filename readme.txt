初始化一个Git仓库，使用git init命令。

添加文件到Git仓库，分两步：
Git add Untitled-1.txt
git commit -m "wrote a Untitled-1 file"
git status

git log
如果嫌输出信息太多，看得眼花缭乱的，可以试试加上--pretty=oneline参数：
git log --pretty=oneline

回退版本
git reset --hard HEAD^
--hard会回退到上个版本的已提交状态，而--soft会回退到上个版本的未提交状态，--mixed会回退到上个版本已添加但未提交的状态。
太多可以写成HEAD~100

git reflog用来记录你的每一次命令：
(use "git restore --staged <file>..." to unstage)
用git diff HEAD -- readme.txt命令可以查看工作区和版本库里面最新版本的区别：


git reset HEAD <file>可以


场景1：当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令git checkout -- file。

场景2：当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，第一步用命令git reset HEAD <file>（把暂存区的修改撤销掉（unstage），重新放回工作区），就回到了场景1，第二步按场景1操作。

场景3：已经提交了不合适的修改到版本库时，想要撤销本次提交，参考版本回退一节，不过前提是没有推送到远程库。

确实要从版本库中删除该文件，那就用命令git rm删掉，并且git commit
如果误删，以下代码可以还原。
 git checkout -- test.txt

 命令git rm用于删除一个文件

要关联一个远程库，使用命令git remote add origin git@server-name:path/repo-name.git；
 git remote add origin  git@github.com:dufeipengyou/learngit.git
关联一个远程库时必须给远程库指定一个名字，origin是默认习惯命名；
关联后，使用命令git push -u origin master第一次推送master分支的所有内容；
此后，每次本地提交后，只要有必要，就可以使用命令git push origin master推送最新修改；

git remote -v  查看远程数据库
git remote rm origin 删除本地和远程的绑定关系，需要删除远程的需要取github网址删除

git clone git@github.com:michaelliao/gitskills.git