---
layout: post
title: "3 Bits for a Great Bug Report"
description: "The 3 basic steps to submitting a Good bug report, plus other tips"
category: Web-development
tags: [geek, how-to, dev]
imagefeature: false
comments: false
share: true
---
Every good bug report needs exactly three things:

 1. _Steps to reproduce the bug_
 2. _What you expected to see_
 3. _What you saw instead_

Seems easy, right? Maybe not.

First thing you must do is explain the steps to reproduce the bug. Nobody will be able to fix the issue if they can't reproduce the bug. "The program crashed and left a smelly turd-like object on the desk." That's nice, honey. I can't do anything about it unless you tell me what you were doing leading up to the crash and resulting turd. Now, I admit that there are two cases where it's hard to get exact steps to repro. Sometimes you just don't remember, or you're just transcribing a bug from "the field." The other time it's OK not to have repro steps is when the bug happens sometimes but not all the time, but you should still provide repro steps, with a little annotation that says that it doesn't happen too often. In these cases, it's going to be really hard to find the bug, but we can try.

If you don't specify what you expected to see, I may not understand why this is a bug. The splash screen has blood on it. So what? I cut my fingers when I was coding it. What did you expect? Ah, you say that the spec required no blood! Now I understand why you consider this a bug.

And finally, describe what you happened instead. This one is kinda obvious, but just be a descriptive as possibe and privide any supporting evidence.


-----------------------------


If you are developing code, even on a team of one, without an organized database listing all known bugs in the code, you are simply going to ship low quality code. On good software teams, not only is the bug database used universally, but people get into the habit of using the bug database to make their own "to-do" lists, they set their default page in their web browser to the list of bugs assigned to them.

*GitHub Issues is simply an awesome way to track bugs and To Do list.*
