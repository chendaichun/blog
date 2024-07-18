以下是常用的Git命令，涵盖了从初始化仓库、提交更改到协作开发的各个方面：

### 初始化和配置

1. **初始化仓库**
   ```sh
   git init
   ```
2. **配置用户信息**
   ```sh
   git config --global user.name "Your Name"
   git config --global user.email "you@example.com"
   ```

### 基本操作

3. **克隆仓库**
   ```sh
   git clone <repository_url>
   ```
4. **查看当前仓库状态**
   ```sh
   git status
   ```
5. **添加文件到暂存区**
   ```sh
   git add <file>
   git add .
   ```
6. **提交更改**
   ```sh
   git commit -m "Commit message"
   ```

### 查看历史

7. **查看提交历史**
   ```sh
   git log
   git log --oneline
   ```

### 分支操作

8. **创建新分支**
   ```sh
   git branch <branch_name>
   ```
9. **切换分支**
   ```sh
   git checkout <branch_name>
   ```
10. **创建并切换到新分支**
    ```sh
    git checkout -b <branch_name>
    ```

### 合并与重置

11. **合并分支**
    ```sh
    git merge <branch_name>
    ```
12. **解决合并冲突**
    - 编辑冲突文件，解决冲突。
    - 添加解决冲突后的文件。
    ```sh
    git add <file>
    ```
    - 提交合并。
    ```sh
    git commit
    ```

13. **重置到特定提交**
    ```sh
    git reset --hard <commit_hash>
    ```

### 远程仓库操作

14. **添加远程仓库**
    ```sh
    git remote add origin <repository_url>
    ```
15. **查看远程仓库**
    ```sh
    git remote -v
    ```
16. **推送到远程仓库**
    ```sh
    git push origin <branch_name>
    ```
17. **拉取远程仓库的更改**
    ```sh
    git pull origin <branch_name>
    ```

### 标签操作

18. **创建标签**
    ```sh
    git tag <tag_name>
    ```
19. **推送标签到远程仓库**
    ```sh
    git push origin <tag_name>
    ```

### 检查和恢复

20. **查看文件差异**
    ```sh
    git diff
    ```
21. **暂存文件的差异**
    ```sh
    git diff --staged
    ```
22. **恢复暂存区的文件到工作区**
    ```sh
    git checkout -- <file>
    ```
23. **取消暂存的文件**
    ```sh
    git reset HEAD <file>
    ```

### 其他有用的命令

24. **显示提交图表**
    ```sh
    git log --graph --oneline --all
    ```
25. **保存当前工作进度（贮藏）**
    ```sh
    git stash
    ```
26. **恢复贮藏的工作进度**
    ```sh
    git stash pop
    ```





### 高级命令（暂时还没学）

以下是一些常见的高级Git用法，可以帮助你更好地管理和优化代码仓库：

### 交互式重定基（Rebase）

1. **Rebase操作**
   ```sh
   git rebase <branch>
   ```
   这会将当前分支的更改应用到指定分支的顶部。

2. **交互式Rebase**
   ```sh
   git rebase -i <commit>
   ```
   你可以选择、编辑、合并或删除特定的提交。

3. **继续Rebase**
   ```sh
   git rebase --continue
   ```
   解决冲突后继续Rebase。

4. **中止Rebase**
   ```sh
   git rebase --abort
   ```
   取消Rebase并恢复到Rebase开始前的状态。

### 选择性挑选提交（Cherry-pick）

5. **挑选特定提交**
   ```sh
   git cherry-pick <commit_hash>
   ```
   将指定的提交应用到当前分支。

### 修正历史记录

6. **修正最后一次提交**
   ```sh
   git commit --amend
   ```
   允许你修改最近的提交信息或添加更多文件。

### 暂存区和工作区

7. **保存当前工作进度（贮藏）**
   ```sh
   git stash
   ```
   将当前工作目录的修改暂时存放起来，以便于切换分支或处理其他工作。

8. **查看贮藏的进度**
   ```sh
   git stash list
   ```

9. **应用贮藏的进度**
   ```sh
   git stash apply <stash@{n}>
   ```
   应用指定的贮藏条目，不删除贮藏记录。

10. **应用并删除贮藏的进度**
    ```sh
    git stash pop
    ```
    应用最近的贮藏条目并删除它。

### 子模块

11. **添加子模块**
    ```sh
    git submodule add <repository_url> <path>
    ```
    将一个Git仓库作为子模块添加到项目中。

12. **初始化子模块**
    ```sh
    git submodule init
    ```
    初始化本地配置文件，但不获取数据。

13. **更新子模块**
    ```sh
    git submodule update
    ```
    获取并检出子模块的最新版本。

### 重写提交历史（Filter-branch 和 BFG）

14. **使用Filter-branch重写历史**
    ```sh
    git filter-branch --tree-filter 'rm -f passwords.txt' HEAD
    ```
    在所有提交中删除文件`passwords.txt`。

15. **使用BFG Repo-Cleaner清理历史**
    - 下载BFG Repo-Cleaner: [BFG Repo-Cleaner](https://rtyley.github.io/bfg-repo-cleaner/)
    - 运行BFG Repo-Cleaner:
      ```sh
      java -jar bfg.jar --delete-files passwords.txt
      ```
    - 强制推送更改:
      ```sh
      git push --force
      ```

### 常用选项和快捷操作

16. **查看简化的提交历史**
    ```sh
    git log --oneline --graph --decorate --all
    ```

17. **强制推送**
    ```sh
    git push origin <branch> --force
    ```

18. **拉取时进行Rebase**
    ```sh
    git pull --rebase
    ```

19. **清理未跟踪的文件和目录**
    ```sh
    git clean -fd
    ```

### 额外技巧

20. **查看贡献者**
    ```sh
    git shortlog -s -n
    ```

21. **查看每行代码的最后修改**
    ```sh
    git blame <file>
    ```

22. **查找引入某个问题的提交**
    ```sh
    git bisect start
    git bisect bad
    git bisect good <commit>
    ```
    然后根据提示继续操作，最后找到引入问题的提交。

这些高级命令和技巧能帮助你更高效地管理Git仓库，处理复杂的版本控制需求。