---
title: Hexo 新手总结
time: 2017-09-27 23:27:13
categories:
  - Hexo
tags:
  - hexo
  - next
---

最近因为一个 [Hexo](https://hexo.io/) 的主题 [NexT](http://theme-next.iissnan.com/)，由 jekyll 转到 Hexo，但是在安装过程中遇到很多问题，其中 [liguanghee](https://liguanghe.github.io) 的这篇 [hexo 博客的神坑及本质原因](https://liguanghe.github.io/2017/05/22/blogRebuilt/) 给我了很大帮助，综合整理一下遇到的问题，为后来人省些麻烦。

## Hexo 与 Jekyll 区别

| Jekyll | Hexo |
| :---: | :---: |
| 在 github 网站中生成页面 | 在本地生成后，上传到网站上 |
| master 即可 | 两个分支 |

和 [hexo 博客的神坑及本质原因](https://liguanghe.github.io/2017/05/22/blogRebuilt/) 重复的内容我就不在这里 copy/paste 了，我对遇到的问题做几点说明：

1. 当下载 NexT 主题后，需要把主题文件夹里的 .git 删除掉，这个 .git 文件夹一般是隐藏的，你可以通过在 windows 设置显示隐藏文件夹来找到或者通过命令行 `ls -a` ，然后 rm 掉 .git 文件夹。
2. 由于 Hexo 是在本地编译，然后上传到 github pages，如果发现本地文件与 github pages 上显示的内容不一致，在部署前执行 `hexo clean` 。
3. 在 root 目录下的 .yml 文件中设置好如下内容：

   ```
   # URL
   ## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
   url: https://<username>.github.io
   root: /
   permalink: :year/:month/:day/:title/
   permalink_defaults:

   # Deployment
   ## Docs: https://hexo.io/docs/deployment.html
   deploy:
     type: git
     repo: https://github.com/<username>/<username>.github.io.git
     branch: master
   ```

4. 所有的更新都要在 gh-pages branch 上完成。

5. 添加新界面:

```
$ cd your-hexo-site
$ hexo new page tags
```

然后确认 tags page 的 yaml 头是否是如下,如果不是改成这样

fileName: source/tags/index.md

```
---
title:
date: 2017-02-17 17:19:25
type: "tags"
---
```



