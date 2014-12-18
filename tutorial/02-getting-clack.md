---
title: Getting Clack
layout: tutorial
---

The easiest way to install Clack is to use
[Quicklisp](http://beta.quicklisp.org/). After installing Quicklisp, just use:

~~~lisp
(ql:quickload :clack)
~~~

on your Common Lisp implementation. This command downloads and installs Clack
and all dependencies automatically.

To check if everything is installed correctly, run a web server with Clack on
your REPL:

~~~lisp
(clack:clackup
  (lambda (env)
    (declare (ignore env))
    '(200 (:content-type "text/plain") ("Hello, Clack!"))))

;-> Hunchentoot server is started.
    Listening on localhost:5000.
    #<CLACK.HANDLER:<HANDLER> #x30200A102B3D>
~~~

Clack starts a web server on localhost port 5000 by default. Open your web
browser and go to http://127.0.0.1:5000/. You should get "Hello, Clack!"
message. You may not understand the details of the above code. Don't worry. I'll
explain it in the next chapter.

To stop the server, use:

~~~lisp
(clack:stop *)
~~~
