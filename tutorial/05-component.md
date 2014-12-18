---
title: Component
layout: tutorial
---

Sorry. I told a lie in [Chapter 3](03-hello-world.html): *Clack application is
just a function.* The truth is, **it's not always a function**. See this
example:

~~~lisp
;; importing symbols for readability.
(import '(clack:call clack:<component>))

(defclass <sample-app> (<component>) ())

(defmethod call ((this <sample-app>) env)
  (declare (ignore env))
  '(200
    (:content-type "text/plain")
    ("Hello, Clack!")))

(clack:clackup
  (make-instance '<sample-app>))
~~~

This is much similar to what we saw before, isn't it? The differeces are minor:
the content of the function was just moved into the `call` method, and the
argument of the `clackup` is an instance of `<sample-app>`.

In a nutshell, `clackup` takes a function or an instance of a subclass of
`<component>` as a Clack application implementation. All components must
implement `call`, which is called for each request.

You may not understand yet how these things work. Don't worry. I'll tell the
details with a real example in the next chapter. Please just remember `clackup`
can take a CLOS instance for now.
