---
layout: post
title: Robots.txt Please Explain
categories: [Please Explain]
tags: [dev, tools, geek, tips n tricks]
share: true
comments: true
---

# The Web Robots Pages

## About /robots.txt

### In a nutshell

Web site owners use the /robots.txt file to give instructions about their site to web robots; this is called _The Robots Exclusion Protocol_.

It works likes this: a robot wants to vists a Web site URL, say http://www.example.com/welcome.html. Before it does so, it firsts checks for http://www.example.com/robots.txt, and finds:


    User-agent: *
    Disallow: /


The "`User-agent: *`" means this section applies to all robots. The "`Disallow: /`" tells the robot that it should not visit any pages on the site.

There are two important considerations when using /robots.txt:

* robots can ignore your /robots.txt. Especially malware robots that scan the web for security vulnerabilities, and email address harvesters used by spammers will pay no attention.
* the /robots.txt file is a publicly available file. Anyone can see what sections of your server you don't want robots to use.

So don't try to use /robots.txt to hide information.

See also:

### The details

The /robots.txt is a de-facto standard, and is not owned by any standards body. There are two historical descriptions:

In addition there are external resources:

The /robots.txt standard is not actively developed. See [What about further development of /robots.txt?][1] for more discussion.

The rest of this page gives an overview of how to use /robots.txt on your server, with some simple recipes. To learn more see also the [FAQ][2].

### How to create a /robots.txt file

#### Where to put it

The short answer: in the top-level directory of your web server.

The longer answer:

When a robot looks for the "/robots.txt" file for URL, it strips the path component from the URL (everything from the first single slash), and puts "/robots.txt" in its place.

For example, for "`http://www.example.com/shop/index.html`, it will remove the "`/shop/index.html`", and replace it with "`/robots.txt`", and will end up with "http://www.example.com/robots.txt".

So, as a web site owner you need to put it in the right place on your web server for that resulting URL to work. Usually that is the same place where you put your web site's main "`index.html`" welcome page. Where exactly that is, and how to put the file there, depends on your web server software.

Remember to use all lower case for the filename: "`robots.txt`", not "`Robots.TXT`.

See also:

#### What to put in it

The "/robots.txt" file is a text file, with one or more records. Usually contains a single record looking like this:


    User-agent: *
    Disallow: /cgi-bin/
    Disallow: /tmp/
    Disallow: /~joe/


In this example, three directories are excluded.

Note that you need a separate "Disallow" line for every URL prefix you want to exclude -- you cannot say "Disallow: /cgi-bin/ /tmp/" on a single line. Also, you may not have blank lines in a record, as they are used to delimit multiple records.

Note also that globbing and regular expression are **not** supported in either the User-agent or Disallow lines. The '*' in the User-agent field is a special value meaning "any robot". Specifically, you cannot have lines like "User-agent: *bot*", "Disallow: /tmp/*" or "Disallow: *.gif".

What you want to exclude depends on your server. Everything not explicitly disallowed is considered fair game to retrieve. Here follow some examples:

##### To exclude all robots from the entire server


    User-agent: *
    Disallow: /



##### To allow all robots complete access


    User-agent: *
    Disallow:


(or just create an empty "/robots.txt" file, or don't use one at all)

##### To exclude all robots from part of the server


    User-agent: *
    Disallow: /cgi-bin/
    Disallow: /tmp/
    Disallow: /junk/


##### To exclude a single robot


    User-agent: BadBot
    Disallow: /


##### To allow a single robot


    User-agent: Google
    Disallow:

    User-agent: *
    Disallow: /


##### To exclude all files except one

This is currently a bit awkward, as there is no "Allow" field. The easy way is to put all files to be disallowed into a separate directory, say "stuff", and leave the one file in the level above this directory:


    User-agent: *
    Disallow: /~joe/stuff/


Alternatively you can explicitly disallow all disallowed pages:


    User-agent: *
    Disallow: /~joe/junk.html
    Disallow: /~joe/foo.html
    Disallow: /~joe/bar.html

---

[Source](http://www.robotstxt.org/robotstxt.html "Permalink to The Web Robots Pages")


[1]: faq/future.html
[2]: faq.html
  
