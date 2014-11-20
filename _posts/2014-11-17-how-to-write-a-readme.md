---
layout: post
title: "How to Write a Great README"
share: true
comments: true
category: Tips n Tricks
tags: [geek, open-source, readme]
---
As many other have blogged before me, a good README should be simple and succinct, but a great README can save time and encourage developers to look more at your project, especially if it's for something like command-line parameter parsing library.

Here's what I think it should include:

- name of the projects and all sub-modules and libraries (sometimes they are named different and very confusing to new users)
- descriptions of all the project, and all sub-modules and libraries
- 5-line code snippet on how its used (if it's a library)
- copyright and licensing information (or "Read LICENSE") 
- instruction to grab the documentation
- instructions to install, configure, and to run the programs
- instruction to grab the latest code and detailed instructions to build it (or quick overview and "Read INSTALL")
- list of authors or "Read AUTHORS"
- instructions to submit bugs, feature requests, submit patches, join mailing list, get announcements, or join the user or dev community in other forms
- other contact info (email address, website, company name, address, etc)
- a brief history if it's a replacement or a fork of something else
- legal notices (crypto stuff)

Apache HTTP Server has a simple yet good README. Another good one I found available online is GNU Make's README.

As per formatting, I would say stick to the Unix traditions as much as possible, and/or use markdown especially for github projects, which renders README.md as html.

- ASCII characters only, if the README is written in English
- write it in English if possible, and ship translated version with two-letter language code extension like README.ja
- 80 characters or less per line
- single empty line between paragraphs
- dashes under the headers
- indent using whitespace (0x20) not tab

###Putting it all together...


{% highlight markdown %}
Documentation
GNU make is fully documented in the GNU Make manual, which is contained
in this distribution as the file make.texinfo.  You can also find
on-line and preformatted (PostScript and DVI) versions at the FSF's web
site.  There is information there about ordering hardcopy documentation.

  http://www.gnu.org/
  http://www.gnu.org/doc/doc.html
  http://www.gnu.org/manual/manual.html 
{% endhighlight %}

###Wikipedia defines as:

>A readme (or read me) file contains information about other files in a directory or archive and is very commonly distributed with computer software.

and it lists the following contents:

>- configuration instructions
- installation instructions
- operating instructions
- a file manifest
- copyright and licensing information
- contact information for the distributor or programmer
- known bugs
- troubleshooting
- credits and acknowledgements
- a changelog


That's it for now, but I have another post about readme file soon. They are very important to the developer and assist with planning and keeping on track.
