---
title: Hexo搭建个人博客教程
date: 2018-12-24 17:20:36
tags: Hexo
---

### 一.准备工作

​	1.安装Node.js   下载地址为：https://nodejs.org/en/download/，安装好后可以在cmd中输入node -v查是否安装成功，注意需要配置环境变量



​	![1545643608583](\1545643608583.png)

​	配置系统Path

​	![1545643863613](C:\Users\mao\AppData\Roaming\Typora\typora-user-images\1545643863613.png)

​	查看是否安装成功



​	![1545644249812](C:\Users\mao\AppData\Roaming\Typora\typora-user-images\1545644249812.png)



​	2.安装git 下载地址https://git-scm.com/downloads  安装成功后可以鼠标右键查看是否安装成功，也可以通过cmd查看git版本 ，git 使用右键git base输入命令，无需配置环境变量



​	![1545644550145](C:\Users\mao\AppData\Roaming\Typora\typora-user-images\1545644550145.png)

![1545644660563](C:\Users\mao\AppData\Roaming\Typora\typora-user-images\1545644660563.png)



​	3.你需要注册一个Github账号，注册好后新建一个仓库，仓库名字可以命名成xxx.github.io(例如：maoxiangyu.github.io)![1545644851621](C:\Users\mao\AppData\Roaming\Typora\typora-user-images\1545644851621.png)

![1545644912292](C:\Users\mao\AppData\Roaming\Typora\typora-user-images\1545644912292.png)

​	仓库创建好后，点击进入刚刚创建的仓库，点击setting

![1545646871383](C:\Users\mao\AppData\Roaming\Typora\typora-user-images\1545646871383.png)



​	页面向下翻到 GitHub Pages，复制 Your site is published at <https://maoxiangyu.github.io/>

你可以发可以直接访问

![1545646962826](C:\Users\mao\AppData\Roaming\Typora\typora-user-images\1545646962826.png)

​	好了，准备工作基本完成，开始搭建第一个Hexo个人框架吧

------



### 二.本地搭建与访问hexo

​	1.安装Hexo，使用cmd命令在一个合适的地方创建一个文件夹（比如d:/blog），然后进入blog文件输入npm install hexo -g 等待安装完成后，输入hexo -v查看是否安装成功

![1545647398012](C:\Users\mao\AppData\Roaming\Typora\typora-user-images\1545647398012.png)



​	2.初始化hexo ，cmd命令输入hexo init，等待初始化完成

![img](https://images2017.cnblogs.com/blog/1108615/201710/1108615-20171021230203912-509196411.png)

​	3.安装hexo组件，cmd命令输入hexo install，依然等待完成

![img](https://images2017.cnblogs.com/blog/1108615/201710/1108615-20171021231521646-1099473727.png)



​	4.生成网站静态文件到默认设置的 public 文件夹，hexo g 是 hexo generate 的缩写，命令效果一致。

​	![img](https://images2017.cnblogs.com/blog/1108615/201710/1108615-20171021231705474-1404994153.png)



​	5.好了，你的默认hexo博客已经生成了，是不是很简单很开心，那么现在再输入hexo  s 后访问

http://localhost:4000  见证奇迹哈

![1545647903675](C:\Users\mao\AppData\Roaming\Typora\typora-user-images\1545647903675.png)

​	如果出现hexo主题页面就是成功了，如下图只是一部分

![img](https://images2017.cnblogs.com/blog/1108615/201710/1108615-20171021232413224-1288183746.png)

------



### 三.将本地Hexo与Github进行关联

​	现在本地已经可以正常访问，我现在要做的是将hexo部署到Github上通过Github pages进行访问

​	1.点击鼠标右键，点击Git Base Here，使用git命令关联您的git用户名，以及邮箱

​	 git   config  --global   user.name "你的git用户名"

​	 git   config  --global   user.email  "你的git邮箱"  

​	![1545648689178](C:\Users\mao\AppData\Roaming\Typora\typora-user-images\1545652419784.png)



​	2.生成ssh key ，使用Git Base Here 输入  cd ~/.ssh命令进入ssh文件存放文件夹，再使用ls查看是否存在ssh文件，下图已经存在ssh文件

![1545648878644](C:\Users\mao\AppData\Roaming\Typora\typora-user-images\1545648878644.png)

​	

​	3.如果没有该文件，输入ssh-keygen -t rsa -C “你的git邮箱”，这里需要点击回车三次，生成密钥文件id_rsa和id_rsa.pub会保存在C:\Users\Administrator\.ssh，红线为存放路径，进入id_rsa.pub文件将内容复制出来，以便一会配置git使用

![1545652809786](C:\Users\mao\AppData\Roaming\Typora\typora-user-images\1545652809786.png)

 	输入eval "$(ssh-agent -s)"，添加密钥到ssh-agent

![1545652074276](C:\Users\mao\AppData\Roaming\Typora\typora-user-images\1545652074276.png)

 

 	再输入ssh-add ~/.ssh/id_rsa，添加生成的SSH key到ssh-agent

![1545652180760](C:\Users\mao\AppData\Roaming\Typora\typora-user-images\1545652180760.png)

​	

​	4.再次进入github，添加ssh key，步骤如图，随便起一个key 名字（例如blog），将3步骤复制的文件内容填入保存		![1545653212598](C:\Users\mao\AppData\Roaming\Typora\typora-user-images\1545653212598.png)



![1545653383649](C:\Users\mao\AppData\Roaming\Typora\typora-user-images\1545653383649.png)



​	

​	5.回到Git base here 中输入ssh -T git@github.com  查看是否添加ssh成功，如果你看到你的用户名，恭喜你成功了，如图

![1545654603780](D:\maoxiangyu.github.io\source\_posts\%5CUsers%5Cmao%5CAppData%5CRoaming%5CTypora%5Ctypora-user-images%5C1545654603780.png)



​	

