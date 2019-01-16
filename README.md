```
*新电脑中的环境搭建*

这部分应该要简单一点，如果你已经搭建过一个hexo博客的话。

新电脑上安装node.js和git。不赘述。git相关教程推荐廖雪峰老师的git教程，突然想到最近很火的考研神嘴张雪峰老师是什么鬼，哈哈哈。

安装hexo：npm install -g hexo-cli。

clone远程仓库到本地 git clone git@github.com:username/username.github.io.git。

根据packge.json安装依赖npm install。

本地生成网站并开启博客服务器：hexo g & hexo s。如果一切正常，此时打开浏览器输入http://localhost:4000/已经可以看到博客正常运行了。

*在两台电脑上的同步操作*

至此，迁移工作已完成，在两台电脑之间的同步操作如下：


git pull从远程hexo分支拉取最新的环境文件到本地，可以理解为svn的更新操作。比如在公司写了博客，回家在电脑上也要写需要先执行这一步操作。

文章写完，要发布时，需要先提交环境文件，再发布文章。按以下顺序执行命令：git add .、git commit -m "some descrption"、git push origin hexo、hexo g -d。
```
