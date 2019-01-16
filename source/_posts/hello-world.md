title: Hexo安装使用
date: 2019-01-15 08:00:00
toc: true #是否显示文章目录
categories: "hexo" #分类
tags:   #标签
	- centOS
	- hexo
top: 100
---
## 什么是hexo?
Hexo 是一个快速、简洁且高效的博客框架。Hexo 使用 Markdown（或其他渲染引擎）解析文章，在几秒内，即可利用靓丽的主题生成静态网页。既然如此便捷，那下面我们开始安装使用吧！

### 准备环境
说明：本人使用的主机是centos7.3
1. 安装[node.js](http://www.runoob.com/nodejs/nodejs-install-setup.html) ，输入node -v 和 npm -v会正确显示出版本号
![upload successful](/images/image.png)
2. 安装[git](https://git-scm.com/book/zh/v1/%E8%B5%B7%E6%AD%A5-%E5%AE%89%E8%A3%85-Git)，安装完成后在命令提示符中输入git --version验证是否安装成功。
3. 注册[Github账号](https://github.com/)，并创建项目，具体步骤如下：
>打开https://github.com/并登陆，新建一个项目，如下所示：

>![upload successful](/images/image1.png)

>输入项目名称，后面一定要加.github.io后缀，注意项目名称要和自己的github用户名相同
>![upload successful](/images/image2.png)
> 点击create repository然后项目就建成了，点击Settings，向下拉到最后的GitHub Pages，点击Choose a theme选择一个主题后，再回到 GitHub Pages，点击生成的链接*https://chenhexiang2017.github.io/*，就会出现自己的网页啦，效果如下：

![upload successful](/images/image3.png)

>到此前面的准备工作就算结束了，下面开始安装hexo.




### 安装Hexo
使用xshell连接主机，在/home文件夹下创建文件夹blog(文件夹路径可以自定义)
``` bash
$ cd /home/blog
$ npm install hexo-cli -g
$ npm install hexo --save
$ hexo -v   #验证是否安装成功
```
输入hexo init初始化文件夹，接着输入npm install安装必备的组件。

这样本地的网站配置搞定后，输入hexo g生成静态网页，然后输入hexo s打开本地服务器，然后浏览器打开[http://ip:4000/](javascript:;)，就可以看到博客页面啦。


### 连接Github与本地
```bash
$ git config --global user.name "chenhexiang2017"
$ git config --global user.email "1305673350@qq.com"
```
用户名和邮箱根据你注册github的信息自行修改。

然后生成密钥SSH key：
```bash
$ ssh-keygen -t rsa -C "1305673350@qq.com"
```
输入eval "$(ssh-agent -s)"，添加密钥到ssh-agent。

再输入ssh-add ~/.ssh/id_rsa，添加生成的SSH key到ssh-agent。

打开github，在头像下面点击settings，再点击SSH and GPG keys，新建一个SSH，名字随便。

打开view /root/.ssh/id_rsa.pub，，将其中的内容复制到新建的SSH中。

输入ssh -T git@github.com，如果出现了自己的用户名说明成功了。

![upload successful](/images/image4.png)

修改博客的配置_config.yml文件（vi /home/blog/_config.yml）
```
deploy:
  type: git
  repository: https://github.com/chenhexiang2017/chenhexiang2017.github.io.git
  branch: master

```
repository修改为自己的github项目地址。

部署到github:
```
hexo clean && hexo g && hexo d
```
访问上面GitHub Pages生成的链接*https://chenhexiang2017.github.io/*就可以了。


### Hexo安装next Gemini主题及相关优化
在博客更目录下安装主题：`git clone https://github.com/iissnan/hexo-theme-next themes/next`

在根目录下的配置文件_config.yml里设置主题：`theme: next`

**接下来我们就可以来按需配置主题内容了，所有内容都在themes/next文件夹下的_config.yml文件里修改**。

1. 菜单栏 menu `||后面是fontAwesome对应的名称`

```
menu:
  首页: / || home
  标签: /tags/ || tags
  #categories: /categories/ || th
  归档: /archives/ || archive
  关于: /about/ || user
  #schedule: /schedule/ || calendar
  #sitemap: /sitemap.xml || sitemap
  #commonweal: /404/ || heartbeat

```
2.主题风格 schemes

根据自己的喜好进行设置

```
# Schemes
#scheme: Muse
#scheme: Mist
#scheme: Pisces
scheme: Gemini

```
