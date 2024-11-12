## 关于初始化和第一次push流程

首先在 https://start.spring.io/ 完成初步配置并生成文件下载movies.zip, 解压到acg-review-website目录下

github手动创建repository,不要readme

获得url https://github.com/Kurumiku0712/ACG-Review-Website.git

```
cd ..  
```

在D:\ProjectWorkspace\acg-review-website创建init仓库, movies文件夹为后端工程文件夹

```
git init
```

出现.git文件夹

使用以下命令将本地Git仓库与GitHub远程仓库连接：

```
git remote add origin https://github.com/Kurumiku0712/ACG-Review-Website.git
```

确保本地在main分支而不是master分支

```
git checkout -b main   
或
git branch -M main
```

如果你刚刚初始化了一个Git仓库，但还没有进行任何提交，`git branch` 命令可能不会显示任何分支信息

```
git add .
git status
```

```
git commit -m "Initial commit"
```

这时候可以查看分支了

```
git branch
或
git branch -a
```

再由本地push到远程的origin main

```
git push -u origin main
```

结果应当是github上面显示内容



如果github上面内容被其他人修改了, 要先git pull origin main解决冲突后git add .和git status和git commit -m "Merge conflict resolved"和git push origin main使得成功merge才能进行后面的push





## 关于删除文件

**情形一: 如果想要删除远程而保留本地磁盘的文件, 且使得该文件不再被git跟踪管理**

从暂存区移走单个文件用git rm, 如果是文件夹只用改成git rm -r --cached, 成功的话下一行会显示rm了这个文件或文件夹的所有文件

```
git rm --cached notes-acg-review-website.md
git status
```

手动创建.gitignore并写上notes-acg-review-website.md

```
git add .gitignore
git commit -m "Ignore notes-acg-review-website.md"
git push origin main
```

结果应当是github上面不再有notes-acg-review-website.md文件, 而本地磁盘不受影响



**情形二: 如果单纯想要删除远程 (文件资源管理器操作是否保留本地磁盘的文件即可)**

比如example.txt

```
git rm --cached D:\ProjectWorkspace\acg-review-website\example.txt
git status
```

千万不要习惯性git add . 又加上去了, 而应该直接

```
git commit -m "Remove example.txt"
git push origin main
```

结果应当是github上面不再有example.txt文件





git checkout -b feature/new feature

git add .

git status

git commit -m "Update"

git push origin feature/new feature

git checkout main

git merge feature/new feature

git push



git pull origin main --rebase

git push --set-upstream origin main

git branch -d test



git tag SWEN90007_2024_Part4_capybara

git push origin SWEN90007_2024_Part4_capybara

