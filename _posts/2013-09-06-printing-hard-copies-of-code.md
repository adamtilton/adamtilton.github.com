---
layout: post
category: blog
title: "Printing hard copies of code"
subtitle: "Printing syntax highlighted code"
thumbnail: 
excerpt: "" 
tags: [pandoc python printing pdf]
---

Put this is margins.sty
\usepackage[vmargin=1in,hmargin=1in]{geometry}

Run this command. Put code in code.md. Output written to code.pdf
pandoc -H margins.sty code.md -s --highlight-style pygments -o code.pdf
