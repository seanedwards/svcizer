svcizer
=======

Turns a shell command into an HTTP endpoint.

Usage
=====

    svcize <cmd> <args>

Now you have an HTTP server running on port 8080, which you can hit with GET requests.

* Request headers and query parameters will be mapped to environment variables.
* The request body will be passed to stdin.
* `STDOUT` and `STDERR` from `cmd` will be dumped to the response body as `Content-Type: text/plain`.
* If the command returns 0, the server will return `200 OK`. If the command returns non-zero, the server will return `503 Internal Server Error`.

That's it. The end.

FAQ
===

"Security?"
-----------
There isn't any.

"How do I...?"
--------------
If it's not obvious, this probably isn't the tool you're looking for.

