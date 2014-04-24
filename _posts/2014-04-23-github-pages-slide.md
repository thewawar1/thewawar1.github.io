---
layout: post
title: "GitHub pages slides"
date: 2014-04-23 14:57
categories: tutorial
---


# Blog systems
1. wordpress


# What's github pages?
- GitHub Pages are public webpages freely hosted and easily published through our site.
- You can create and publish them online using the Automatic Page Generator.
- If you prefer to work locally, you can use the GitHub for Mac and Windows apps, or the command line. 

# 2 Steps
1. Write a post save as text file (markdown/html)
2. Push the post file to Github repository


# Getting started

## Setup

1. Create a github account
2. Create a repository: username.github.io


## Use Jekyll

1. Themes
   + [Jekyll Themes](http://jekyllthemes.org/)
   + [掌心 Themes](http://www.zhanxin.info/themes.html)
   
2. Comments
3. RSS
4. Markdown, Textile
   + [Markdown Syntax][markdown-syntax]
   + [Markdown 语法中文版][markdown-syntax-cn]
   
> Markdown 是一种轻量级标记语言，创始人为约翰·格鲁伯（John Gruber）和 已故天才黑客亚伦·斯沃茨（Aaron Swartz）。
> 它允许人们“使用易读易写的纯文本格式编写文档，然后转换成有效XHTML(或者HTML)文档, 这种语言吸收了很多在电子邮件中已有的纯文本标记的特。

5. Sample
 - [thewawar1.github.io](http://thewawar1.github.io)
 - [阳志平的网志](http://www.yangzhiping.com/)

## Put other things on it.
   images, zip, ....

  
# Commands

``` bash
    # Install Ruby
    wget http://cache.ruby-lang.org/pub/ruby/2.1/ruby-2.1.1.tar.gz
    tar -xf ruby-2.1.1.tar.gz
    cd ruby-2.1.1
    ./configure && make && make install

    # Install Jekyll & Create a jekyll blog
    gem install jekyll
    jekyll new {yourname}.github.io

    # Push your blog to Github
    cd youname.github.io
    git init
    git add .
    git commit -m "First commit"
    git remote add origin https://github.com/{yourname}/{yourname}.github.io.git
    git push origin master

```

[markdown-syntax]: https://daringfireball.net/projects/markdown/syntax "Markdown Syntax"
[markdown-syntax-cn]: http://wowubuntu.com/markdown/ "Markdown语法中文版"
[jekyll-doc]: http://jekyllrb.com/docs/quickstart/ "Jekyll documentation"
