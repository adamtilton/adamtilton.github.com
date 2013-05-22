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
2. Jekyll converts dynamic content to static web pages, stored in the
   `_site` folder.
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

1. Install Ruby, if you don't have it.
2. Install jekyll
    1. `# gem install jekyll` 
3. Install markdown gem RDiscount.
    1. `# gem install rdiscount`
    2. Remeber to change the `_config.yml` to use rdiscount.
        1. `markdown: rdiscount`
4. Install pygments for syntax highlighting 
    1. `# pacman -S python-pygments` or `# pacman -S python2-pygments` 

## OK, It is installed. Now what?

### Create the appropriate directory structure. 
Mine looks like this, at the time of writing this post.

<pre>
.
|-- _includes
|-- _layouts
    |--default.html
    |--page.html
    `--post.html
|-- _plugins
|-- _posts
    `--2012-10-20-making-sense-of-Jekyll.md
|-- _site
|-- 404.html
|-- _config.yml
|-- CNAME
|-- README.md
`-- index.html
</pre>

### Update the _config.yml
I used the degault configuration from the [Jekyll wiki][3],
plus a few extra features.

permalink: /:categories/:year/:month/:day/:title 

<pre>
exclude: ["README.md"]
auto: true
pygments: true
markdown: rdiscount
safe: false
auto: false
server: false
server_port: 4000
production_url : adamtilton.com

destination: ./_site
plugins: ./_plugins

</pre>

### configure index.html
This page defines the landing page.


### Configuring `\( \LaTeX \)` Support

What is a blog without `\(LaTeX\)` Support? Luckily this isn't too hard
to setup. I follow the advice of [5][cwobker]. Here is a
summary: 

#### Put the following in your main layout file (i.e. `_layouts/default.html`)

{% highlight html%}
<!--- MathJax -->
<script type="text/javascript"
  src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML">
</script>
<script>
  MathJax.Hub.Config({
    tex2jax: {
      skipTags: ['script', 'noscript', 'style', 'textarea', 'pre']
    }
  });
  MathJax.Hub.Queue(function() {
      var all = MathJax.Hub.getAllJax(), i;
      for(i=0; i < all.length; i += 1) {
          all[i].SourceElement().parentNode.className += ' has-jax';
      }
  });
</script>
<!--- MathJax End -->
{% endhighlight %}

#### Put this is your css stylesheet.

{% highlight css %}
code.has-jax {font: inherit; font-size: 100%; background: inherit; border: inherit;}
{% endhighlight %}

#### Finally, wrap your latex code in the *code* tags

This:
<pre>
`\[ \begin{aligned} \dot{x} & = \sigma(y-x) \\ \dot{y} & = \rho x - y - xz \\ \dot{z} & = -\beta z + xy \end{aligned} \]`
</pre>

Becomes
`\[ \begin{aligned} \dot{x} & = \sigma(y-x) \\ \dot{y} & = \rho x - y - xz \\ \dot{z} & = -\beta z + xy \end{aligned} \]`






