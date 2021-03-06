---
title: Github Pages 搭建个人博客教程
date: 2018-04-04 10:16:00
categories:
- Github
tags:
- blog
---

不想再与主机服务商打交道？GitHub Pages 基于 Jekyll 构建，你可以轻而易举地在 GitHub 上免费发布网站——自定义域名等等。利用github实现个人博客的网站搭建，便于整理知识，不受第三方博客网站限制。

---

# 个人博客搭建教程

## 准备工作

> github.io web站点

    1、Github Pages插件
    https://pages.github.com/
    2、搭建教程
    http://cyzus.github.io/2015/06/21/github-build-blog/   

> 域名解析

     https://www.jianshu.com/p/d1fdf3316fc0

> 前端搭建

    1、选择主题
    http://jekyllthemes.org/
    2、推荐主题
    http://jekyllthemes.org/themes/jekyll-theme-next/
    3、github window 客户端
    https://desktop.github.com/

> 整体思路

    1、github创建xxx.gihub.io项目
    2、关联GitHubPage插件
    3、申请域名
    4、ping xxx.github.io 获取IP
    5、添加CNAME文件（可为空文件）
    6、阿里云免费域名解析 IP 解析方式设置为CNAME（若网站CNAME文件为空的话）
    7、github中自定义顶级域名
    8、添加第三方插件
        - 百度统计
        - 评论管理

## 相关资料

    1、gitalk 评论插件整合
    https://www.jianshu.com/p/9be29ed2f4b7
    - 注意：分类和文件名要使用英文，否则无法创建issue

    2、第三方服务集成教程
    http://theme-next.simpleyyt.com/third-party-services.html#facebook-sdk


## 更多

> 扫码关注“架构探险之道”，回复`文章名称`获取更多源码和文章资源

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190403222309957.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NpbmF0XzI4NjkwNDE3,size_16,color_FFFFFF,t_70)

> 知识星球(扫码加入获取源码和文章资源链接)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190403222322267.jpeg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NpbmF0XzI4NjkwNDE3,size_16,color_FFFFFF,t_70)
