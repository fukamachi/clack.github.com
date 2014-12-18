---
title: Using Clack.Middleware.Static
layout: tutorial
---

Clack contains these useful middlewares:

* [Clack.Middleware.Static](http://clacklisp.org/doc/clack.middleware.static.html) - returns static files
* [Clack.Middleware.Logger](http://clacklisp.org/doc/clack.middleware.logger.html) - logs messages
* [Clack.Middleware.Session](http://clacklisp.org/doc/clack.middleware.session.html) - manages sessions
* [Clack.Middleware.Conditional](http://clacklisp.org/doc/clack.middleware.conditional.html) - enables a middleware to conditionally wraps components
* [Clack.Middleware.Auth.Basic](http://clacklisp.org/doc/clack.middleware.auth.basic.html) - provides basic authentication

Clack.Middleware.Csrf which protects Clack applications from CSRF attacks is
also available as a contrib package.

Let's take a look at
[Clack.Middleware.Static](http://clacklisp.org/doc/clack.middleware.static.html)
as a real example of a Clack middleware. It returns a static file if a request
matches a specified pattern.

Here's an example source code to show how to use Clack.Middleware.Static. This
wrapped application returns "Hello, Clack!" for most requests, but a file in
`/path/to/static-files/` when request pathes match `/public/*`.

~~~lisp
(import '(clack:wrap
          clack.middleware.static:&lt;clack-middleware-static&gt;))

(defun app (env)
  (declare (ignore env))
  '(200
    (:content-type "text/plain")
    ("Hello, Clack!")))

(defvar mw
    (make-instance '&lt;clack-middleware-static&gt;
       :path "/public/"
       :root #p"/path/to/static-files/"))

(clack:clackup
  (wrap mw #'app))
~~~

Every middleware implements a `wrap` method, which provides a mechanism to
generate wrapped applications. An application can be wrapped by multiple
middlewares through calling `wrap`s consecutively:

~~~lisp
(clack:clackup
  (wrap mw3
    (wrap mw2
      (wrap mw1 #'app))))
~~~

However, this nesting `wrap`s looks tedious. Clack has a solution to write this
with a DSL style syntax. That's the topic of the next chapter.
