# Git 学习（二）---- 分支及协作开发



## 分支理解及概述



&emsp;&emsp;分支是什么？ 分支可以理解成对某一分支的副本.



&emsp;&emsp;比如说我们默认创建的分支就是 master，master的代码得一直在线上运行，如果出现了紧急bug，那么创建一个副本（分支 hot-fix），在副本上进行随意修改。master 合并 最终 hot-fix 的版本，达到优化bug且不影响程序线上运行的效果。



![1657471025308](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657471025308.png)





&emsp;&emsp;在版本控制过程中，同时推进多个任务，每个任务都创建分支，开发分支的代码不会影响主线分支的运行。底层通过指针引用实现。



![1657471435782](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657471435782.png)



## 分支的好处



1、同时并行推进多个功能的开发，提高开发的效率



2、各个分支在开发的过程中互不影响，如果某一个分支开发失败，不会对其他分支造成影响，直白的分支删除重新开始即可。



## 分支（branch）的相关操作







### （1）查看分支

```bash
git branch -v
```

可以查看所有分支及当前所在的版本

![1657471748885](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657471748885.png)



&emsp;&emsp;master 前面有个 * 号，同时为绿色，表示当前指向的是 master 分支，同时后面显示该分支当前处在的版本, 创建分支 hot-fix 和当前分支内容是一样的，可以看作是当前master的副本



### （2）git branch 创建分支



```bash
git branch [分支名]
```



创建了当前分支 master 的分支(副本) hot-fix



![1657471965526](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657471965526.png)



创建分支 hot-fix, 可以在 hot-fix 进行独立开发，最终合并即可。



### （3）git checkout 切换分支



```bash
git checkout [分支名]
```



在执行先查看所有分支的状态

![1657472070848](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657472070848.png)

head 指向 master



执行切换分支，查看状态

![1657472199829](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657472199829.png)



此时的状态，画个图



我们在刚创建 hot-fix 分支，相当于 hot-fix 指向了 master之前的版本，拥有了之前master的内容

![1657472307904](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657472307904.png)



切换到了 hot-fix 分支，head 指针发生改变



![1657472396399](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657472396399.png)





如果在 hot-fix 分支上开发代码形成新的版本，首先master 无法直接拿到，必须master来合并才行

![1657473036561](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657473036561.png)



### （4）git merge 合并分支



```bash
git merge [分支名]
```



&emsp;&emsp;我们模拟 hot-fix 分支修改bug，改变hello.txt 内容,注意此时是在 hot-fix 分支上进行修改，之后我们还需要提交到本地库,才算提交成功，hot-fix 有了新的版本



![1657473106976](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657473106976.png)



此时 hot-fix 分支已经修改完毕了，生成了新的版本，（bug修改完毕）



![1657473238946](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657473238946.png)



master 作为上线的项目，需要把修复好的代码作为自己的下一个版本更新，就需要合并 hot-fix 这个分支



（1）切换回 maser 分支



![1657473378618](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657473378618.png)



切换成master分支后，当前版本依然为master的之前的版本，需要合并进行更新



![1657473468777](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657473468777.png)



（2）合并 hot-fix 分支



```bash
git merge hot-fix
```



![1657473792467](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657473792467.png)



发现，合并之后，master最新版本即为 hot-fix 的提交的版本，同时查看文件，master更新成功！

![1657473860164](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657473860164.png)

head指针指向 master，同时 master 因为合并 指向hot-fix 的最新版本作为 自己的最新版本。





### （5）合并冲突





&emsp;&emsp;如果master 又更新了，hot-fix 也更新了，而且更新的内容不同，master合并的时候本应该直接拿 hot-fix的最新版本，但是此时合并不知道要哪个更新的版本了！不知道要谁了，所以需要我们手动进行选择。我们在再根据需要在文本编辑器中进修修改即可。





## 团队间协作开发



一个团队的代码开发人员是怎么进行协作开发呢？



![1657474536557](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657474536557.png)

都是从远程仓库（GitHub、Gitee）拿代码

clone 是从0到1，从一无所有开始拿到所有代码

pull 相当于有之前的版本，从远程仓库进行更新一波



&emsp;&emsp;程序员1 在本地开发一个程序之后，放到远程代码仓库了，让其他人进行其他功能模块的开发。程序员2 通过 远程代码仓库 clone下来 之前开发的程序到自己的本地库中，自己进行开发，开发完之后，提交上传到 远程代码中心（团队之间上传需要协作权限），程序员1 看别人开发完了，自己又想在开发的好一点，从代码中中心pull下来代码（更新），在进行后续的开发。



## 跨团队协作开发



![1657475388417](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657475388417.png)



![1657475374379](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657475374379.png)

