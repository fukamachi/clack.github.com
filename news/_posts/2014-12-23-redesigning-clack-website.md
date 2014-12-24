---
layout: news
title:  "Redesigning the Clack website"
author: Fernando Borretti
date:   2014-12-23 11:49:52
tags:   []
---

Earlier this month, I took some time to [port][pull] the Clack website to
[Jekyll][jekyll], port the documentation to Markdown and give the site a
complete redesign with [Sass][sass].

<!-- sep -->

This site was originally written entirely in raw HTML. My first step was to
[port][jekyll-port] the existing content to Jekyll, simply moving the common
elements of each page to `_includes` and `_layouts`. Afterwards, I started
aggressively rewriting old parts of the site until I got to where we are now.

We now use [highlight-lisp][hl] for syntax highlighting of Lisp code. This is
less general, and doesn't allow us to, for example, highlight HTML or CSS, but
it does a better job of highlighting Common Lisp than other systems.

The tutorial, which was written in raw HTML, has been ported to Markdown to make
maintaining and writing it easier. The Japanese version of the tutorial was
dropped because, not being a Japanese speaker, I could have broken it during
transformation and never realized.

This change adds two new sections to the site:

* The News section, which was added with this redesign with the goal of having a
  central location to make announcements relating to Clack.
* A [section][security] to the tutorial on reporting security issues, which will
  become increasingly important as Clack continues to grow in users.

The next obvious step is to revise and complete the tutorial, and then
optionally translate the finished version to Japanese and other languages.

If you want to contribute, just [fork][repo] and hack away!

[pull]: https://github.com/clack/clack.github.com/pull/11
[jekyll]: http://jekyllrb.com/
[sass]: http://sass-lang.com/
[jekyll-port]: https://github.com/clack/clack.github.com/pull/10
[hl]: https://github.com/orthecreedence/highlight-lisp
[security]: http://clacklisp.org/tutorial/16-security.html
[repo]: https://github.com/clack/clack.github.com
