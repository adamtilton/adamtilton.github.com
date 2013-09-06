---
layout: post 
category: blog
title: "Notes from setting up Jekyll."
subtitle: ""
thumbnail: 
excerpt: "" 
tags: [notes, jekyll]
---
[1]: google.com


## What is Jekyll?

{% highlight css %}
code.has-jax {font: inherit; font-size: 100%; background: inherit; border: inherit;}
{% endhighlight %}

#### Finally, wrap your latex code in the *code* tags

This:
{% highlight latex%}
\begin{equation} 
    \begin{aligned} 
        \dot{x} & = \sigma(y-x) \\ 
        \dot{y} & = \rho x - y - xz \\ 
        \dot{z} & = -\beta z + xy 
    \end{aligned} 
\end{equation}
{% endhighlight %}

Becomes
`\[ \begin{aligned} \dot{x} & = \sigma(y-x) \\ \dot{y} & = \rho x - y - xz \\ \dot{z} & = -\beta z + xy \end{aligned} \]`






