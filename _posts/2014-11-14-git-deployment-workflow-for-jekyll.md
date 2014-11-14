---
title: Workflow to GitHub Deployment with Jekyll
description: The short guide.
---

Grunt is always running when I’m writing or designing. It handles a few things, as defined in my Gruntfile.

This is my process: 
  - SVGMin to minify my SVG files and remove unnecessary code
  - SVG2PNG to make PNG copies of my SVG files
  - Sass to make authoring my stylesheets easier
  - Autoprefixer to prefix CSS properties and values as needed
  - Jekyll to build my site into static HTML files
  - Finally, a “watch” task to watch my files for changes and perform the above tasks

Jekyll builds my site in a `_site` directory, which is ignored by Git so that I don’t end up with duplicate content and unnecessary bloat on GitHub.

When my post or design changes are in a state I’m happy with, I commit my changes and push to GitHub.

> “Simples”
- Meerkat
