---
layout: post
title: "Building a Custom Beamer Template"
description: ""
category: 
tags: [notes, design, beamer, latex, presentations]
---
[1]: http://www.drbunsen.org/designing-a-beamer-template-theme/
[2]: https://bitbucket.org/rivanvx/beamer/wiki/Home
[3]: https://github.com/drbunsen?tab=repositories
[4]: http://ctan.mackichan.com/macros/latex/contrib/beamer/doc/beameruserguide.pdf
[5]: http://www.hartwork.org/beamer-theme-matrix/
[6]: http://cameron.bracken.bz/beamer-template
[7]: https://github.com/wspr/fontspec/
[8]: http://www.woggie.net/2008/07/16/beamer-pdftex-and-xetex/
[9]: http://bloerg.net/2012/06/21/customizing-the-frametitle-of-beamer-presentation.html
[10]: 

# Outline

+ Starting at [drbrunsen][1]
    + [Stock beamer themes][5] are ugly.
    + He has a template on [github][3]
    + There is another nice template [here][6]
    + Read the beamer [documentation][4]
    + Element styilng is controlled through two templates
        + Inner template: block, enumerate, and itemize
        + Outer template: infolines and frame titles
    + Suggests learning about [color theory], no more than three colors
    + Use a sans-serif font
    + Use only two type faces and avoid comples ligature
    + Need to use xetex
        + Supports TrueType and OpenType fonts.
        + Use [fontspec][7] pacakge to change font
        + package xunicode provides unicode extras
        + package cltxtra provides some fixes for related fonts
        + microtype font package provides better font output:
        `\usepackage[final,expansion=true,protrusion=true,spacing=true,kerning=true]{microtype}` 

+ Beamer, PDFTeX and XeTeX
    + See this [blog][8]

+ Beamer Backgrounds
    + These are made as images.
    + The dimensions are 1512 X 1134
    + The frame title dimensions are 1512 X 200
    + The thin orange strip is 10

+ Customizing the frametitle
    + See this [blog post][9], doesn't work very well. Can't do a
      subtitle.
    + Instead overlay on an image and use a minipage to situate text
    + Control text spacing with setspace

+ Beamer appearance cheat sheet
