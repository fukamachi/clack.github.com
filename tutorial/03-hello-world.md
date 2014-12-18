---
title: Hello, World!
layout: tutorial
---

Let's take a closer look at the first small Clack application we introduced in
the previous chapter. Here's a slightly "polite" version of the program.

~~~lisp
(defun app (env)
  (declare (ignore env))
  '(200
    (:content-type "text/plain")
    ("Hello, World!")))

(clack:clackup #'app)
~~~

You see a Clack application is just a function which takes one argument and
returns a list of three elements, which respectively expresses a status code,
header fields, and body data, I mean, an HTTP response collectively.

Let's modify this application a little bit to explain the argument `env`.

~~~lisp
(defun app (env)
  `(200
    (:content-type "text/plain")
    ("Hello stranger from:"
     ,(getf env :remote-addr))))

(clack:clackup #'app)
~~~

This application returns web clients' remote addresses. It should be 127.0.0.1
if you are accessing a server running on localhost. The `env` is a property list
containing various information about each HTTP connection associated with an
HTTP request.

You can designate a file as HTTP body data. Here's a little bit complicated
example using this feature.

~~~lisp
(defun app (env)
  (cond
    ((string= (getf env :path-info) "/favicon.ico")
     '(200
       (:content-type "image/x-icon")
       #p"/path/to/favicon.ico"))
    ((string= (getf env :path-info) "/")
     '(200
       (:content-type "text/html")
       ("<html><head></head><body>Hello again</body></html>")))
    (t '(404 (:content-type "text/plain") ("Not found")))))

(clack:clackup #'app)
~~~

This application returns the file favicon.ico in response to the request whose
request path is "/favicon.ico", "Hello again" in response to a request to the
root (/), or otherwise "Not found" with a 404 status code.
