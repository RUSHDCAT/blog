# 部署博客

## 第一步：安装Git & node.js

分别上官网安装即可



## 第二步：安装hexo

任意位置Shift+右键调出Powershell，输入命令：

```
npm install -g hexo
```



## 第三步：Clone Blog文件夹

在所需位置，调出Powershell，输入命令：

```
git clone git@github.com:kyoma95/Blog.git
```

电脑上没有SSH key则可参考：[SSH key设置](https://www.cnblogs.com/chuyanfenfei/p/8035067.html)



## 第四步：部署

如果是在一个空文件夹下部署新博客，由于我们在前面已经全局安装了hexo，所以可以直接在该文件夹下调出Powershell，输入：

```
hexo init
```

这一步是从别人的github上把博客的框架clone下来。



但是如果我们这样照搬的话，会报如下错误：

```
ERROR Local hexo not found in F:\Blog
ERROR Try running: 'npm install hexo --save'
```

然而，我们在任意其他文件夹下输入：

```
hexo -v
```

都是正常的。这大概是我们直接从我的github上clone了Blog文件夹，具体原因我也搞不清楚。

于是我们只好按照指示，输入命令：

```
npm install hexo --save
```

这时，Blog中就会出现node_modules文件夹，hexo的命令就都可以用了。

我们马上生成静态文件：

```
hexo g
```

然后就可以愉快地调出sever进行测试了：

```
hexo s
```

进行完修改后，将内容部署到网站上：

```
hexo d
```



## 第五步：使用Git备份

每次在对Blog文件夹进行修改前，使用都要先进行分支合并，以便与github上的版本保持一致：

```
git pull
```

修改后，调用下面两条命令向Git提交修改：

```
git add .
git commit -m "xxx"
```

然后将本次地修改推送到github上：

```
git push
```

Git教程：[Git教程](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)

教程中包含了第一次在自己电脑上建立Blog文件夹后上传到github的方法。

需要注意的是，上传后我们会发现，哎呀怎么少了好多文件夹啊，这是因为Blog文件夹中有一个文件.gitignore，忽略了部署后我们可以调用hexo命令在本地生成的文件。