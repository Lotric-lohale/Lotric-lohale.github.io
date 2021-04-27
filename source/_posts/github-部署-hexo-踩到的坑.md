---
title: github 部署 hexo 5.4 blog 踩到的坑
date: 2021-04-26 11:07:34
tags: 'others'
---
1. Hexo 前端资源报错 404 
>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;这个是要的原因是 github 建库时，没有按照教程使用 username.github.io 命名仓库有关，方便的话，通过仓库 settings - options - Repository name 修改下仓库名即可。</br>
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;但是有的人头铁，说我仓库不能按照那个规则命名怎么办呢。这个也是有解决办法的。通过查看报错信息可知，这个js、css等前端资源报错是因为路径使用绝对路径，只需要把斜杠删除就正常，笨点的方法可以在执行 hexo generate 之后，找到根目录的public文件夹下的index.html文件，把斜杠去掉。</br>
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;上面手动删除的方法也太笨了。可以通过修改打包插件，让打包出来的文件路径就是去掉斜杠的。</br>```npm install hexo-renderer-stylus@0.1 --save```</br>
> 通过把打包文件降级可以实现，打包出来的文件前面不带斜杠，前面的命令执行完成后，直接打包发布即可
2. hexo 主题不生效
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 主题文件下载下来后，themes文件下，主题文件夹的名称必须和_config.yml的theme 配置的名称一致。有的已经这么配置还是不生效怎么办？建议放弃，有的主题打包后文件都不正常了，这种主题折腾太麻烦了。