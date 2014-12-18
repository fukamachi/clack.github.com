---
title: The Environment
layout: tutorial
---

Let's have a good look at `env`. When you access a server on localhost,
ex. http://localhost:4242/sns/member?id=3, the `env` is something like this:

~~~lisp
(:request-method :GET
 :script-name ""
 :path-info "/sns/member"
 :query-string "id=3"
 :server-name "localhost"
 :server-port 4242
 :request-uri "/sns/member?id=3"
 :server-protocol :HTTP/1.1
 :remote-addr "127.0.0.1"
 :remote-port 26077
 :headers #<HASH-TABLE :TEST EQUAL :COUNT 4 {10061F0F23}>)
~~~

Below is the details of the keys and values of `env`. You don't need to memorize
all of them, except that you are creating a Clack handler or an adapter between
Clack and a web server.

`:request-method` (Required, Keyword)
: The HTTP request method: ` :GET` , ` :HEAD` , ` :OPTIONS` , ` :PUT` , `
  :POST`, or ` :DELETE` .

`:script-name` (Required, String)
: The initial portion of the request URI path that corresponds to the Clack
  application. The value of this key may be an empty string when the client is
  accessing the application represented by the server's root URI. Otherwise, it
  is a non-empty string starting with a forward slash (`/`).

`:path-info` (Required, String)
: The remainder of the request URI path. The value of this key may be an empty
  string when you access the application represented by the server's root URI
  with no trailing slash.

`:query-string` (Optional, String)
: The portion of the request URI that follows the `?`, if any. This key may
  have no value at all while the key itself always exists.

`:server-name` (Required, String)
: The resolved server name or the server IP address.

`:server-port` (Required, Integer)
: The port on which the request is being handled.

`:server-protocol` (Required, Keyword)
: The version of the protocol the client used to send the request: typically
  `:HTTP/1.0` or `:HTTP/1.1`.

`:request-uri` (Required, String)
: The request URI. Always starts with &quot;/&quot;.

`:raw-body` (Optional, Stream)
: The raw body of the request.

`:remote-addr` (Required, String)
: The remote address.

`:remote-port` (Required, Integer)
: The remote port.

`:headers` (Required, Hash-Table)
: A hash table of headers.
