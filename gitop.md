```git
git init

git clone 克隆仓库


git add .
git commit -m "初始化"

git remote add origin [网址]
查看关联
git remote (-v 详细信息)
git remote set-url [仓库名] [新url]

推送
git push (-u设置分支为默认分支)

查看状态
git status

git diff：查看更新的详细信息命令
git rm：删除命令

git branch：查看分支命令
git branch (branchname)：创建分支命令
git checkout (branchname)：切换分支命令
git merge：合并分支命令
git branch -d (branchname)：删除分支命令
git branch -m (branchname)：修改分支名称命令

修改本地初始化分支名
git config --global init.defaultBranch main

git fetch、git pull：提取远程仓仓库

git pull(可加--rebase) [仓库] [分支名]


git log:查看历史记录
commit hash值 (当前版本位置)
Author: 作者
Date: 时间
备注
git log --pretty=oneline 简洁

git reset --hard HEAD^ 版本回退，几个^回退几个版本
git reset --hard HEAD~n版本回退n个
git reset --hard [索引值]

git reset --soft  ：1.仅在本地版本库移动指针。
git reset --mixed : 1.移动本地版本库的指针；2.重置暂存区。（默认的参数）
git reset --hard  : 1.移动本地版本库的指针；2.重置暂存区；3.重置工作区。
```