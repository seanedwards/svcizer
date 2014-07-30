svcizer
=======

Turns a shell command into an HTTP endpoint.

Usage
=====

    svcize <cmd> <args>

Now you have an HTTP server running on port 8080, which you can hit with GET requests.

* Request headers and query parameters will be mapped to environment variables.
* The request body will be passed to stdin.
* HTTP headers and query parameters will be passed as environment variables.
* `STDOUT` and `STDERR` from `cmd` will be dumped to the response body as `Content-Type: text/plain`.
* If the command returns 0, the server will return `200 OK`. If the command returns non-zero, the server will return `503 Internal Server Error`.
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

FAQ
===

"Security?"
-----------
There isn't any.

"How do I...?"
--------------
If it's not obvious, this probably isn't the tool you're looking for.

