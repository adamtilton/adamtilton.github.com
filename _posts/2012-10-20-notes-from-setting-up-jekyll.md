---
layout: post
title: "Notes from setting up Jekyll."
description: ""
category: 
tags: [notes, jekyll]
---
{% include JB/setup %}

[1]: http://jekyllbootstrap.com/
[2]: http://www.archlinux.org/
[3]: https://github.com/mojombo/jekyll/wiki/
[4]:http://pewniak747.info/2009/12/22/jekyll_basics_tutorial/
[5]: http://cwoebker.com/posts/latex-math-magic 

This page is a work in progress as of {{ page.date | date: "%d %B %Y" }}.

## What is Jekyll?
I started from the [Jekyll Bootstrap][1], which describes
Jekyll as 

>Jekyll is a parsing engine bundled as a ruby gem used to build static
>websites from dynamic components such as templates, partials, liquid
>code, markdown, etc. Jekyll is known as 'simple, blog aware,
>static site generator'.

### Here are some Jekyll highlights

1. It is a ruby gem.
3. Jekyll is not blogging software. It will not provide any templates or
   design elements.
4. Jekyll is minimalistic and efficient. 
5. Non database is required.
6. Content can be hosted freely on github pages!


## How do I install Jekyll?

I am working on [Arch Linux][2]. I followed instruction from these
resources:

+ Install page on the [Jekyll git wiki][3]
+ This [Jekyll basics tutorial][4]
