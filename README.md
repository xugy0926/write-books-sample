# 介绍

我只是想构建一个WIKI平台，但我又不想花时间去写一个编辑文章的功能。如何借助gitbook的写作平台来写作，然后把内容自动同步到我的服务器，再由我的服务器提供数的阅读展示呢？

![](/assets/wiki.png)

##### wiki服务器

1. 可配置wiki源的git仓库信息。
2. 监听webhook事件，更新对应git仓库的内容。
3.  存储git仓库的内容。

##### 前端

1. wiki 配置页面（管理员权限，配置页面的目的是和设置webhook的仓库进行一一对应）。
2.  wiki展示（可解析gitbook文件结构模式，UI上做轻微定制）

##### github和gitbook

github和gitbook可以之前相互同步，并且可以做到双重备份。无论是直接编辑github上的内容还是编辑gitbook上的内容都可以。

# 步骤

#### 1. 用github存储

直接clone项目[write-books-sample](https://github.com/xugy0926/write-books-simple.git)，write-books-sample作为一本书的基础结构。后面写任何东西直接在上面该即可。

clone到自己的项目后，可以把项目名改成自己想要的名字

#### 2. 将write-books-ample同步到gitbook上

同步到gitbook上是为了保证我们可以用gitbook提供的写书客户端来写书。一旦github上的write-books-sample同步到gitbook的某个项目，这两个项目就有了一一对应的关系。任意一边的改动都会同步到对方。

#### 3. 将github项目hook到我们第三方的服务上

第三方服务是你自己开发的服务器，该服务器会监听你项目的变化，重新拉取项目并自动生成html。这样可以保证用户可以实时看到书的新内容。

