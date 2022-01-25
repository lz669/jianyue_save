> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [blog.csdn.net](https://blog.csdn.net/zhuoyuedelan/article/details/104153418)

> 简书对 markdown 的支持非常好, 而 [github](https://so.csdn.net/so/search?q=github&spm=1001.2101.3001.7020) 恰好也是非常鼓励使用 markdown 格式, 这次我们尝试将简书的文章, 搬到 GitHub 平台.

> 我以前在简书发布过的一篇 " [图虫遇爬虫](https://www.jianshu.com/p/93e163865ae7) ", 这篇文章有代码, 有内容, 很适合迁移到 GitHub, 今天就以它为例

在本地生成一对秘钥 (以 [Ubuntu](https://so.csdn.net/so/search?q=Ubuntu&spm=1001.2101.3001.7020) 为例)
-----------------------------------------------------------------------------------------

*   进入到. ssh 目录下

```
cd ~/.ssh/
```

*   生成一对秘钥

```
ssh-keygen -t rsa -C "lijianzhao1208@gmail.com"
```

*   为秘钥起个名字 (可直接回车跳过)
    
      
    ![](https://img-blog.csdnimg.cn/img_convert/1ff09d5951087a62f91b9dbe165729a6.png) 秘钥起个名字

*   将公钥内容添加到 github(实现免密向远程仓库提交代码)

> 复制公钥 (github.pub) 内容

> ![](https://img-blog.csdnimg.cn/img_convert/4519cd68bdbce87ff4d92eb20bca1503.png) 复制公钥 (github.pub) 内容

> 登录 github, 并粘贴公钥内容

> ![](https://img-blog.csdnimg.cn/img_convert/1d8f1d1a53e173c16fe2689b1f48a257.png) github 主页

> ![](https://img-blog.csdnimg.cn/img_convert/bbc3db82869937ec38bbacaa8d6abc0e.png) 添加容器

> ![](https://img-blog.csdnimg.cn/img_convert/ff4253db7ea4164aca89c4dea6dd9718.png) 添加公钥

> ![](https://img-blog.csdnimg.cn/img_convert/14c4d561640dcd19782c9ca3ce85312a.png) 添加完成

在 github 建立一个仓库
---------------

> ![](https://img-blog.csdnimg.cn/img_convert/fd54a42f6b37b559addcd344b7194f6c.png) 建立新仓库

创建新仓库
-----

> ![](https://img-blog.csdnimg.cn/img_convert/3a784637ddedf3c0723906d6186455cd.png) 创建新仓库

> ![](https://img-blog.csdnimg.cn/img_convert/0b51f89c4e13c4ecb2811f1a96f0cfc6.png) 仓库创建成功

> 新仓库的位置为:  
> `https:github.com/用户名/新仓库名`

从本地 (Ubuntu16.04 环境), 获取远程仓库
----------------------------

```
git clone git@github.com:zhaoolee/TuChong.git
```

> ![](https://img-blog.csdnimg.cn/img_convert/6f635e38a6365233b2d391da78a5737d.png) 获取远程仓库内容

将简书内容添加到 README.md 文件中
----------------------

*   打开简书后台编辑页面

> ![](https://img-blog.csdnimg.cn/img_convert/4b4a76fb231c0d6d28f332d6627b3259.png) 打开简书后台编辑页面

*   复制内容

> ![](https://img-blog.csdnimg.cn/img_convert/ea6236b7f23229920da139c97e3b2a79.png) 复制内容

*   将内容添加到 README.md

> ![](https://img-blog.csdnimg.cn/img_convert/724b6918a8f9992cbd38e730d914cada.png) 粘贴

> ![](https://img-blog.csdnimg.cn/img_convert/021f383471fe4f37d82bc87aae4fc2c0.png) 粘贴成功

*   将代码文件添加到 TuChong 目录

> ![](https://img-blog.csdnimg.cn/img_convert/fb1443f7a78483003629e3c5ed6b6bc5.png) 拖拽文件

*   将更新的内容添加到本地仓库

> ![](https://img-blog.csdnimg.cn/img_convert/9b7e04597430aa504a74d9db7d6173c9.png) 添加到本地仓库

将本地仓库内容提交到 github 仓库
--------------------

*   添加远程仓库

`git remote add TuChong git@github.com:zhaoolee/TuChong.git`

*   正式提交代码

```
git push -u TuChong master
```

> ![](https://img-blog.csdnimg.cn/img_convert/25367bf70d854d2bbc2e802c96788db6.png) 推送成功

> ![](https://img-blog.csdnimg.cn/img_convert/dc5be6d96f63277c07b2dd941e5a9cb7.png) 查看 github 更新

[Github 显示效果](https://link.jianshu.com?t=https%3A%2F%2Fgithub.com%2Fzhaoolee%2FTuChong)对比[简书显示效果](https://www.jianshu.com/p/93e163865ae7)
-----------------------------------------------------------------------------------------------------------------------------------------

> ![](https://img-blog.csdnimg.cn/img_convert/55ff38254652e3c0cbb85aee909203f7.png) Github 与 jianshu

Github 还能更个性化些
--------------

*   上面的显示完全依赖于 README.md 文件的内容, github 提供了将 README.md 文件内容独立为网页的功能 (网页还预制了个性化主题)

> ![](https://img-blog.csdnimg.cn/img_convert/d998dcfe5d48255e1c78a2f1072c563f.png) 进入 settings

*   选择主题

> ![](https://img-blog.csdnimg.cn/img_convert/8b2397d191e57a7fc4e881c94c0e6ac9.png) 选择主题

*   可选主题

> ![](https://img-blog.csdnimg.cn/img_convert/fb3bb456c1e2dd0f62fda92f4b9edc09.png) 主题系列 1

> ![](https://img-blog.csdnimg.cn/img_convert/faf968eec57c1aa0b068332923e55ccd.png) 主题系列 2

个性化主题效果 [预览链接](https://link.jianshu.com?t=https%3A%2F%2Fzhaoolee.github.io%2FTuChong%2F)
----------------------------------------------------------------------------------------

> ![](https://img-blog.csdnimg.cn/img_convert/f3585e499fd06069f10c0a8e5e6a9476.png) 个性化主题效果

> 如果你想使用 python 自动化完成仓库创建, 并在新仓库上传一些稳定关联的资源, 参考这篇 [Github 变身网络硬盘](https://www.jianshu.com/p/d053ffa892a8)