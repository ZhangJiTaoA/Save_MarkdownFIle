# Git

1. 下载安装**git**

2. 设置用户名和邮箱，这台电脑上所有git仓库都会用这个配置。

   ```git
   git config --global user.name "username"
   git config --global user.email "xxx@xxx.com"
   ```

3. 新建一个本地版本库。

   ```git
   git init  //将当前目录变成git可以管理的仓库
   ```

   **系统自动创建了唯一一个master分支**

4. git版本管理如下图所示

​					![img](https://img-blog.csdnimg.cn/20201223105444452.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM0OTY0MTk3,size_16,color_FFFFFF,t_70)

​	**git分为三个区：工作区、暂存区、仓库分支**

5. 将需要提交的文件添加到暂存区。

   ```git
   git add filename  
   ```

6. 将**暂存区**中的内容提交到当前分支。

   ```git
   git commit -m "info"
   ```

7. **分支介绍。**

​	首先init后会创建一个**主分支**即master分支，可以使用指令创建子分支，再子分支提交后即在子分支上进行，将子分支和主分支合并后子分支的内容被合并到主分支上。

8. 分支指令

   ```git
   git branch "branchname"  // 创建一个分支
   git checkout "branchname"  // 切换到分支
   git checkout -b branchname  // 创建并切换
   git branch  // 查看分支
   git branch -d branchname  // 删除分支
   ```

9. 合并指令

   ```git
   git merge branchname  // 合并某个分支到当前分支
   ```

10. 远程仓库相关

11. ```git
    git remote add origin "链接ssh或https"  // 添加远程链接
    git remote -v  // 查看远程库详细信息
    git push origin master  // 将本地master推送到远程
    git pull //抓取分支
    git fetch //只是从远程拉下来，并没有合并，拉下来以后本地分支落后于远程分支
    git branch --set-upstream-to=origin  // 如果上面pull报错，设置远程分支。
    ```

12. 

13. 

7. 

8. 

9. 

10. **git其他指令。**

    ```git
    git log   // 查看提交日志
    git reset --hard HEAD^  // 回退版本，^表示上一个版本，^12表示上12个版本。
    git status  // 查看状态。
    git diff HEAD -- "filename"  // 查看filename文件工作区和版本库里的区别。
    git checkout -- "filename"  // 丢弃工作区的修改。
    rm "filename"  // 工作区中删除文件。
    git rm "filename" // 版本库中删除文件
    ```

11. 






















