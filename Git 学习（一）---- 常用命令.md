

# Git 学习（一）---- 常用命令



## 设置用户签名



只需要操作一次，设置一次



```bash
git config --glocal user.name [name] # 设置name签名
```



```bash
git config --global user.email [email]  # 设置 email 签名
```



查看git运行的文件目录中的gitConfig文件



![1657383147884](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657383147884.png)



![1657383159804](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657383159804.png)



如果设置成功有显示



![1657382926346](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657382926346.png)



&emsp;&emsp;签名的作用就是区分不同的操作者身份，用户签名信息在每个版本的提交信息中能够查看到，确认每次提交是谁提交的。



- 注意：这里设置用户签名和将来登录 GitHub（或其他代码托管中心）的账号没有任何关系。



## git init 初始化本地库（工作区）



我们建一个新的文件夹，用来练习git的操作。GitRespository文件夹中，在创建一个文件夹project001保存项目代码。



![1657383758253](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657383758253.png)



在 project001 文件夹下打开 git bash ,然后执行 git init,进行初始化 



```bash
# 在文件夹中打开gitBash
rain7@RAIN-Computer MINGW64 /d/GitRespository/project001

$ git init # 将这个文件夹进行初始化
Initialized empty Git repository in D:/GitRespository/project001/.git/

#返回结果说明当前目录下生成了一个空的git仓库 生成了一个 /.git文件夹

rain7@RAIN-Computer MINGW64 /d/GitRespository/project001 (master)

#此时 project001 作为一个master
```



当前文件夹project001生成了一个隐藏的文件夹， .git/ ,里面的文件不要修改

![1657383894901](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657383894901.png)



git bash中能够使用 linux的相关命令



```shell
rain7@RAIN-Computer MINGW64 /d/GitRespository/project001 (master)
$ ll -a
total 4
drwxr-xr-x 1 rain7 197121 0 Jul 10 00:23 ./
drwxr-xr-x 1 rain7 197121 0 Jul 10 00:21 ../
drwxr-xr-x 1 rain7 197121 0 Jul 10 00:23 .git/
```



在git bash中也能查看到 隐藏的文件信息，同时linux指令都能够使用





## git status 查看本地库状态



查看状态的指令

```bash
git status
```



输入完之后，返回的日志中输入三条语句



![1657466573534](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657466573534.png)



在当前文件夹中创建一个文件



![1657466737917](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657466737917.png)



当前目录已经有了一个文本文件，我们再来查看本地库状态

hello.txt 为红色，说明此时只是在工作区，未被git追踪到（这个文件只需追踪一次即可）

![1657466369805](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657466369805.png)





## git add 将工作区文件保存到暂存区



```bash
git add [fileName]
```



![1657466882390](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657466882390.png)



## git rm --cached  [fileName] 删除暂存区文件



```bash
git rm --cached  [fileName]
```

![1657467010623](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657467010623.png)



## git commmit  提交本地库

![1657386240332](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657386240332.png)



hello.txt 文件已经保存到暂存区，我们要将暂存区文件上传到本地库



使用命令 ,日志信息必填

```bash
git commit -m "日志信息" 文件名
```



![1657389112522](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657389112522.png)



&emsp;&emsp;如果不填日志信息，那么会跳出这个界面，提示请对于你的改变输入一些日志，如果日志为空那么这次提交将被放弃，然后我们就用vim编辑器在下面写入信息



![1657389163460](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657389163460.png)



最后按 esc 退出编辑模式，：wq保存退出，此时输出信息提示成功



下面是按照正常的方式提交日志信息

![1657467173230](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657467173230.png)

此时再次查看 本地库状态，提交成功，没有修改

![1657467266901](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657467266901.png)





## git log 查看日志（提交信息）



查看提交信息有两个命令



```bash
git reflog # 查看版本信息
```



![1657467327781](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657467327781.png)



有版本号（前七位），指针的指向当前分支，以及提交的日志记录



 ```bash
git log # 查看版本详细信息，更加详细，有签名有日期，有完整的版本号
 ```



![1657467341694](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657467341694.png)



有完整的版本号，指针的指向当前分支，签名，日志记录



## 修改文件信息



&emsp;&emsp;如果我们在本地库中的文件，之前的版本进行了修改，（比如说代码功能进行了拓展，需要再次提交一个新的版本），我们对工作区的文件进行了修改，对hello.txt 文件进行了修改



![1657467506239](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657467506239.png)



此时修改过时候，我们再来查看本地库状态

![1657467533152](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657467533152.png)



显示 hello.txt 进行了修改，需要使用 git add [filename]或者 git commit -a 进行再次提交缓存区更新



![1657467681512](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657467681512.png)



更新完之后，查看日志信息，会显示每次提交的记录



![1657467724184](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657467724184.png)



&emsp;&emsp;最后工作区保留的是当前版本（可以用过版本切换来使得工作区的文件拿到不同版本的内容），git通过指针保存各种版本修改。



 ##  一个分支下的版本穿梭 



```bash
git reset --hard [version]
```



当前版本（第二次提交的版本），工作区的文件内容



![1657470061962](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657470061962.png)



我们把文件版本 穿梭到第一次提交时候的 版本



（1）查看以前提交生成的版本号



![1657470187135](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657470187135.png)

我们在之后输入版本号的时候，只需要输入前几位，保证版本号唯一即可



（2）穿梭版本，指定版本号进行穿梭



![1657470244715](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657470244715.png)



提示 head指针现在指向了第一次提交到版本



![](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657470415837.png)



同时查询日志，也可发现，版本发生变化，移动到了b47fed 这个版本



![1657470447757](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657470447757.png)



（3）查看工作区文件，内容回退到之前版本

![1657470549547](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657470549547.png)