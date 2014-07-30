svcizer
=======

Turns a shell command into a plain HTTP endpoint. _There is no security._

Usage
=====

    svcize <cmd> <args>

Now you have an HTTP server running on port 8080, which you can hit with GET requests.

* Request headers and query parameters will be mapped to environment variables.
* The request body will be passed to stdin.
* `STDOUT` and `STDERR` from `cmd` will be dumped to the response body.
* If the command returns 0, the server will return `200 OK`. If the command returns non-zero, the server will return `503 Internal Server Error`.
* If you really care, the actual exit code is stuffed into the `Exit-Status` header.
* HTTP headers and query parameters will be passed as environment variables. Yes, this means you can overwrite `$PATH`. Do it if you want. _There is no security._
* Any environment variable can be substituted into an argument by using `%var%`:
  
      `svcize ls %p%`
  
  Now we can pass in an argument with the `p` query parameter:
  
      $ curl "http://localhost:8080?p=."
      Gemfile
      Gemfile.lock
      LICENSE
      README.md
      svcize

That's it. The end.

Potential FAQ
=============

"Security?"
-----------
_There is no security._

"Cookies?"
----------
Delicious. But no.

"What about...?"
--------------
You probably can't. This is a super basic tool for building the most micro of web services.

"How do I perform maximum evil?"
--------------------------------
    svcize bash -c %cmd%

