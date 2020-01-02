

### Git

- 别名   st 代替status

```
git config --global alias.st status   
```

- Vscode配置bash终端

  ```
  "terminal.integrated.shell.windows": "C:\\Program Files\\Git\\bin\\bash.exe",
      "git.enableSmartCommit": true,
      "git.path": "C:\\Program Files\\Git\\bin\\git.exe",
  ```

- 合并命令

  ```
  git add . && git commit -m "vuex學習" && git push origin master
  ```

- 仓库根路径下清除缓存

  ```
    m
  ```

  

#### 报错

1.

###### 错误码

```
error: Your local changes to the following files would be overwritten by merge:
```

###### 场景

远端厂库与本地仓库已经不同的基础上没有先pull而是直接更改，当想要pull时会出现代码被覆盖的情况，git不允许所以会报错

###### 解决

方法1：如果你想保留刚才本地修改的代码，并把git服务器上的代码pull到本地（本地刚才修改的代码将会被暂时封存起来）

```
git stash
git pull origin master
git stash pop
```

方法2、如果你想完全地覆盖本地的代码，只保留服务器端代码，则直接回退到上一个版本，再进行pull：

```sql
git reset --hard
git pull origin master
```

2.

- 执行git add . 后仍然报changes not staged for commit错误的解决方法 

![img](https://img-blog.csdn.net/20180808092855890?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2xvZ2FuX0xH/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70) 并且上传到仓库的文件夹是空的 

1、先强行删除clone来的目录下的 .git 文件夹

​     删除方式：在该目录下打开命令行工具，执行 **rd/s/q .git**命令

​    删除成功后执行**ls .git**命令提示如下内容说明删除成功

2、回到仓库根目录删除仓库中的空文件夹
    1）git rm -r --cached "PATH"
    2）git commit -m "remove empty folder"
    3）git push origin master
3、在仓库根目录重新提交代码
    1）git add .
    2）git commit -m "repush"
    3）git push origin master
