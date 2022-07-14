



# Git 学习（三）---- GitHub 远程库操作



github 是外网，不太好访问，但是有办法



 [FastGithub下载及使用 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/428454772) 



##  使用GitHub 创建远程库



github 是全英文的，建议使用 Goole 浏览器访问，可以全文翻译



（1）进入GitHub个人主页 ，创建远程仓库



![1657535021839](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657535021839.png)



（2）创建仓库，自定义名字，是否选择公开，初始化仓库



![1657535475842](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657535475842.png)



（3）已经成功创建仓库了，可以看到 有 https 上传的仓库地址，ssh 上传的仓库地址



![1657535269889](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657535269889.png)



## 上传本地库中保存的文件到 远程库中



（1）之前已经在 本地中执行了 git add / git commit ,将 hello.txt 上传到本地库中了



![1657535617118](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657535617118.png)



（2）使用git push 命令将文件上传到 远程的 github仓库中



## git remote add [别名] [远程链接] 给远程仓库取别名



```bash
git remote add [别名] 远程地址
```



远程地址很长，所以有的时候就会选择起一个短一点的别名，push的时候直接写别名就行了，可写可不写



![1657535904827](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657535904827.png)



## git remote -v 查看当前远程仓库的别名



```bash
git remote -v 
```



![1657535923595](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657535923595.png)



因为远程库既可以拉取，也可以推送，所以出现了两个别名



push 的时候可以使用别名，clone、pull 也可以使用别名





## git push [远程库] [分支] 上传远程库



```bash
git push [远程库链接/别名] [分支branch]
```



上传的时候，最小单位是分支，需要指定本地库中的哪一个分支及进行推送。



在日志中可以看到推送百分百完成，master分支推送完毕



![1657536227314](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657536227314.png)



在中间可能需要验证 github 的身份账号，一种是账号密码登陆，一种是口令登录，尽量选择第一种



![1657536616810](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657536616810.png)

 

## 在 github中 查看推送

![1657536330521](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657536330521.png)

刷新后，看到推送的信息

![1657536360017](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657536360017.png)



## 在GitHub 在线修改代码，本地库更新



如果我们在github上对文本进行修改编辑，那么需要更新我们本地库的内容，需要保持一致

![1657536467083](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657536467083.png)



## git pull [远程链接/别名]  [分支] 拉取远程库代码到本地库中



```bash
git pull [远程库链接/别名] [分支]
```

拉取远程库代码的最小单位也是分支



到本地库进行拉取，拉取远程仓库的代码，对本地代码进行更新

![1657536704582](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657536704582.png)



此时查看本地库中hello.txt 文件，拉取成功

![1657536823878](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657536823878.png)





## git clone [远程链接] [分支名] 克隆远程仓库

```bash
git clone [远程仓库链接] [分支名]
```



远程仓库如果是 public,那么读权限是不受限制的，所以可以直接克隆，不需要登陆账号



在一个新建的文件夹下，我们把仓库中的项目给完整克隆下来



![1657536968157](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657536968157.png)



文件自动创建好，远程仓库的内容也被克隆下来了



![1657537055597](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657537055597.png)![1657537066119](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657537066119.png)





## git clone 操作干了哪些事情呢？



 （1）拉取远程库代码

（2）本地库初始化

（3）给拉取的代码分支起一个默认的别名（origin）



![1657537739446](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657537739446.png)



## GitHub 团队内协作



（1）领导leader的仓库，进入项目设置



![1657786528740](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657786528740.png)

（2）点开collaboration 合作者的选项，点击add peopel ,邀请合作者



![1657786589509](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657786589509.png)



（3）输入github用户名



![1657786612658](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657786612658.png)

（4）进行邀请



![1657786649795](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657786649795.png)



（5）邀请之后会生成一个 邀请函 pending invite,将邀请函复制下来（其实就是一个github链接）

![1657786669443](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657786669443.png)



（6）leader 将邀请函的链接通过钉钉、微信发给 程序员1， 程序员1 打开之后接收邀请，程序员1就拥有了push 这个远程代码仓库的权限了。

![1657786700355](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657786700355.png)



## GitHub 跨团队协作



（1）团队1 将自己的远程仓库链接发送给 团队2 ，团队2 点击fork，将别人的远程仓库 fork(叉)一份到自己的本地远程仓库来



![1657787150661](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657787150661.png)



（2）团队2在自己的本地仓库中可以看到粘贴了一份一样的仓库（forked来自于团队1）

![1657787235167](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657787235167.png)



（3）团队2 在自己的电脑上clone、修改、开发、上传到本地库，push到本地远程仓库

（4）修改过之后上传至本地远程仓库，点击pull request，拉取请求，给团队1对个话，说我写好了你们要不要。



点击pull request

![1657787346354](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657787346354.png)



团队2创建 pull request

![1657787461573](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657787461573.png)`

团队2 编辑request 的内容，发送pull request



![1657787484781](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657787484781.png)



（5）团队1打开Github 账户，处理pull request



点开pull request,发现团队2传递的信息

![1657787599579](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657787599579.png)



打开请求的内容，可以查看发送的信息，以及传递的文件代码进行审核，团队1 决定要不要merge 

![1657787660644](C:\Users\rain7\AppData\Roaming\Typora\typora-user-images\1657787660644.png)



如果有疑问，可以在下面发送消息支持双方对话，没问题团队1点击merge pull request 即可合并团队2代码

