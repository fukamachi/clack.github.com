---
title: Introduction
layout: tutorial
---

Clack is a web application environment for Common Lisp, inspired by Python's
WSGI, Ruby's Rack, and Perl's Plack. By abstracting HTTP into simple APIs, Clack
enables your web applications to be portable and be reusable.

If you are familiar with web application development, you may have noticed the
reason why this type of software is so important--web applications are in beta
forever.

## Enlargement of systems

It means we have to improve our applications on daily basis. In the process of
the improvement, it is common that you have to add features which are completely
out of your consideration during its initial design phase. Web applications will
be enlarged.

In this type of situation, it is really hard or even impossible for you to add
new functionalities into your application if you built it as one big rock which
doesn't have good layer or modular architecture. This is why components of your
application should be loosely coupled so as to make their dependencies as clear
and simple as possible.

## Technologies change fast

On top of that, there is another issue. The Web evolves fast. Most technologies
are likely to be changed or replaced within a few years.

This fact makes the problem unavoidable regardless of how you wrote "your"
programs carefully to avoid it. All software gets stale everyday. Your web
server software will have become old-fashioned just a few years later. Your web
framework may be not maintained anymore in that future. Same applies to the
libraries you are using in your application. It is difficult for you to make
your source code up to date with the times if your application is tightly
coupled to other software.

## What Clack solves

Clack was developed to solve this problem. Clack works like "glue" to compose a
web application. Actually, Clack is not a web application framework but a
collection of modular components, which are so loosely coupled that you can
easily replace any of them independently.

Clack is an abstraction layer for both HTTP and web servers. This allows you to
ignore the difference over backends of your system. As web applications built on
Clack are independent form your current choice of backend, you can run the same
code on other web servers just by modifying your application a little bit.

I should not explain all about Clack in this one chapter, but rather provide
additional information that helps you check how trustworthy Clack is: at least
if it's worth sparing your time to learn the outline.

## Clack has been stable

All features of the core of Clack were already implemented in the first official
release in June, 2011. Since then, no serious bug has been found and nothing
harmful to backward compatibility has been introduced into it.

## Well-documented

Most functions, variables and macros in Clack have docstrings. Even packages
have. We strongly believe all entities in sources should be documented except
that they are truly self-explanatory.

We provide the documentation also in HTML format at http://quickdocs.org/clack/api.

## Well-tested

The reason why Clack had only a few bugs so far is plenty of quality unit
tests. There are 173 tests currently. The test coverage has been kept over 70%
since its first official release.

All releases have passed the test suite on three CL implementations: Clozure CL,
SBCL, and CLISP. You can check the current status at http://ci.clacklisp.org/.
