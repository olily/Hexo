---
title: The Road of My Blog (One)
date: 2018-10-08 17:55:52
tags: 
- Hexo
- MyBlog

thumbnail: /gallery/img_4/dog.jpg
categories: MyBlog # 分类
---
-- ----------------------------
#### <font color=pink> 笑一笑，十年少 </font>
#### <font color=pink>xixixixi~xixixixi~xixixixi~xixixixi~xixixixi </font>
其实以前申请过一个Blog账号，可是当我第二次登陆的时候……竟然凉了
身边有大佬建议用hexo搭建一个，也就是一个git项目，然后巴拉巴拉
这么麻烦的Blog，一开始我是拒绝的
可是在瞎捣鼓两天之后，我的妈呀，怎么这么好看
那就继续瞎捣鼓吧
其实这几天，收获颇丰，作为一只小菜鸡~还是有那么一丢丢的成就感
好啦~开始我的博客之路吧（并不是边做边保存所以有些步骤没有图望原谅）
如果对各位道友有帮助的话,那就再好不过啦
-- ----------------------------

#### <font color=pink>General 概括</font>

######  Power by : HEXO
此Blog是基于HEXO开发的，其实我对hexo并不是很了解，以前也没接触过，之所以会用它原因如下：
   * *正好笔者以前开发过git项目（这也是一个项目）
   * *主题超多还很好看（颜值即正义）
   * *灵活性很强（想怎么改怎么改，没有喜欢的主题还可以自己创作）
   * *简单高效快捷（官网是这么说的，不过笔者暂时只有一丁点感觉） 
   * *强大的插件系统（只要你想，没有做不到）
   * *支持Markdown（ emmm~想不到说的了，反正就是挺好的）
   * *…………待笔者继续发现的优点 

献上HEXO官网：
[hexo.io](https://hexo.io)
[hexo.io/zh-cn（中文）](https://hexo.io/zh-cn/) 

######  Theme : Miccall
这个主题是笔者一眼就相中的主题，简单大方超好看，主页（嘘！图是偷来的）如下：
<img src="http://onh0umlhz.bkt.clouddn.com/githubhexothemereadmemain.png" width="80%" />
主题的作者也是一枚大佬啊，如果有感兴趣的道友可以去大佬Blog看看，笔者也不能随意透露大佬的个人信息啦，不过大佬文章颇丰强烈建议道友瞧一瞧，或许就有你感兴趣的点呢
献上大佬的主页：[miccall.tech](http://miccall.tech)
献上主题：[github.com/miccall/hexo-theme-Mic_Theme](https://github.com/miccall/hexo-theme-Mic_Theme)

######  author : olily
笔者是一枚各方面都很菜很菜的小菜鸡，就不介绍啦~
直接进入正文

---------------------

#### <font color=pink>Contents 目录</font> 
- 准备工作
- 环境搭建
- Blog初见面

---------------------

##### <font color=pink>准备工作</font> 
###### 1. 注册github账号
- 直接进入该网址进行注册： https://github.com/
- 注册成功后验证邮箱（new repository点击即可验证）
<img src="https://s1.ax1x.com/2018/10/09/iJO78S.png" width = 80%>
###### 2. 安装git版本工具
Windows系统需下载，Mac系统自带git可不用下载
下载地址：https://git-scm.com/downloads  
测试：`git --version`，显示版本号即成功
###### 3. 下载安装node.js
hexo基于node.js，所以在下载hexo之前需要先保证node.js环境
下载地址：http://nodejs.cn/download 
测试：`node -v` 、`mpm -v`，显示版本号即成功
###### <font color=pink>温馨提示：</font> 
npm 源地址下载的话，速度特别慢，伤神费时，毕竟国外的服务器嘛
所以可以用淘宝镜像，简单地说就说服务器架在国内下载速度更快
任意目录下执行如下命令即可：
`npm config set registry http://registry.npm.taobao.org/ `
感兴趣的道友可以直接百度“npm淘宝镜像”
献上官网：[npm.taobao.org/](http://npm.taobao.org/)
###### 4. 安装hexo
首先在本地创建一文件目录
根据自己的情况，此文件夹即存放搭建博客的所有文件以及以后编写的博客
建议文件路径不宜太深，直接置于DCE盘即可
笔者电脑未分盘，文件路径如下`C:\file\Hexo`
直接在`C:\file\Hexo`下面点击鼠标右键，选中git bash here
执行如下命令：``
    npm install hexo-cli -g
``
执行完之后，该目录下就会有如下文件：
###### <font color=pink>温馨提示：</font> 
如果已经安装hexo后千万不要再执行一遍安装hexo命令，血的教训o(╥﹏╥)
如果已经这样做了也没有关系，笔者血的教训也为道友备好了
献上一血传送门： [重装hexo及备份.传送门](http://olily.github.io)

---------------------

##### <font color=pink>环境搭建</font>
###### 1. 创建github项目
- 进入到github页面，点击github头像图标开始创建项目
<img src="https://s1.ax1x.com/2018/10/09/iJOHgg.png" width = 80%>
- 按照如下步骤开始创建项目，项目名称最好按照如此格式减少很多不必要的麻烦（username.github.io）
<img src="https://s1.ax1x.com/2018/10/09/iJOvEq.png" width = 80%>

###### 2. 初始化hexo
- 在`C:\file\Hexo`下输入打开git bash执行命令`hexo init`，初始化该文件夹
出现“Start blogging with Hexo！”就代表成功啦（别急着关闭bash哦）
- 执行`npm install`命令安装相关组件、
- 再安装一个扩展：`npm install hexo-deployer-git --save`
- 执行`hexo g` 生成 == hexo generate
- 执行`hexo s` 启动hexo == hexo server
<img src="https://s1.ax1x.com/2018/10/09/iJOODs.png" width = 80%>
访问该网址，就可以看到hexo的主页图片啦
如果打不开有可能是端口冲突，执行命令`hexo s -p 4001`(任意修改)可修改端口号再次打开哦 
###### <font color=pink>温馨提示：</font> 
访问本地页面的时候hexo server 不可以按ctrl+c停止服务，否则会报404

###### 3. 将Hexo与Github page相联系起来
- 设置git的user name和email
在hexo文件夹下执行打开bash,与之对应修改为你的用户名和邮箱就ok
执行`git config --global olily`和`git config --global 1135569701@qq.com` 
- 配置ssh
 * 在hexo文件夹下执行如下命令生成密钥对，邮箱替换成自己的
中途如果有输入直接空格，或者你的秘钥但一定要记住
`ssh-keygen -t rsa -C 1135569701@qq.com`
在"C:\Users\ `username` .ssh"路径下可以看到生成的公私钥对`username`为你的用户名
<img src="https://s1.ax1x.com/2018/10/09/iJOXbn.png">
 * 复制本地公钥：执行`ssh-copy-id`（待会可以ctrl+v啦,别急着关闭bash哦）
 * 进入你的github页面`https://github.com/olily/olily.github.io`，如图进入添加ssh页面
<img src="https://s1.ax1x.com/2018/10/09/iJOLuj.png" width = 80%>
 * 将复制的公钥粘贴到此处，如图勾选即可
<img src="https://s1.ax1x.com/2018/10/09/iJOI4f.png" width = 80%>
 * 成功后会出现如下信息
<img src="https://s1.ax1x.com/2018/10/09/iJOxU0.png" width = 80%>
 * 回到.ssh目录下，执行`eval "$(ssh-agent -s)" `添加密钥到ssh-agent
 * 再执行`ssh-add ~/.ssh/id_rsa`添加生成的ssh key到ssh-agent
 * 测试是否成功：执行`ssh -T git@github.com`如果看到Hi+用户名，就说明成功啦

至此ssh部分就已经完全配置成功啦
###### 4. 配置Deployment
- 在hexo目录下找到_config.yml文件，subline打开
- 文末修改`deploy`值，如下
<img src="https://s1.ax1x.com/2018/10/09/iJOTC8.png" width = 80%>
（repo值是你的仓库地址）
<img src="https://s1.ax1x.com/2018/10/09/iJO5UP.png" width = 80%>

至此就已经配置完毕啦，现在让我们来试试我们的博客吧

---------------------

##### <font color=pink>Blog初见面</font> 
- 新建一篇博客，再hexo文件目录下执行：`hexo new post "fistblog"`即可新生成一篇博客在_posts目录下
- 执行`hexo d -g`即可完成部署
- 登录你的blog地址`olily.github.io`访问你的文章

---------------------

哇hhhhhhh终于可以有自己的blog了啊，是不是跟我一样兴奋激动.jpg呢
好啦，至此hexo+github博客搭建就完成啦，如果跟我喜欢一样的主题可以继续跟我走哟
在此献上笔者的主页：
<img src="https://s1.ax1x.com/2018/10/09/iJX6I0.png" width = 80%>
<img src="https://s1.ax1x.com/2018/10/09/iJXyaq.png" width = 80%>

<font color=pink>xixixixixixi~</font>
<font color=pink>望各位道友能原谅这突兀的粉色，满足我的少女心</font>
<font color=pink>笔芯ღ( ´･ᴗ･` )</font>
























