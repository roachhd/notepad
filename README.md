this is my notepad
==================

The personal notepad of Katie Ball. Katie is a web developer and game maker, who also love PhotoShop, her kids, dogs and The Tiges. She studied at RMIT and Swinburne Universities in Melbourne Australia, have made heaps of websites and web apps, published 3 apps across all the major app stores.
I'm currently loving `Jekyll`, `Grunt`, `GitHub` and all things open source ❤️

------------------------------------------

#Workflow to GitHub Deployment with Jekyll 
######short guide

- Grunt is always running when I'm writing or designing. It handles a few things, as defined in my `Gruntfile`, namely: 
  - SVGMin to minify my SVG files and remove unnecessary code
  - SVG2PNG to make PNG copies of my SVG files
  - Sass to make authoring my stylesheets easier
  - Autoprefixer to prefix CSS properties and values as needed
  - Jekyll to build my site into static HTML files
  - Finally, a â€œwatchâ€ task to watch my files for changes and perform the above tasks
- Jekyll builds my site in a  _site  directory, which is ignored by Git so that I donâ€™t end up with duplicate content and unnecessary bloat on GitHub.
- When my post or design changes are in a state I'm happy with, I commit my changes and push to GitHub.

--------------------------------+----

###my notes for my notepad haha

#####Front Matter

     Categories     |   Tags
------------------- | ------------------
web-development     | reference
Design              | git
Game-Development    | photoshop
Workflow            | docs
Life Hack           | tips n tricks
                    | quick reference

-----------------------------------------

```yaml
---
layout: post
title: Theme Elements
description: "Just about everything you'll need to style in the theme."
headline: 
category: theme
tags: [docs]
mathjax: true
chart: 
imagefeature: cover6.jpg
comments: false
share: true
---
```

#####Good Cover Images:
```yaml
images/cover10.jpg
images/cover3.jpg
```

---------------------------------
