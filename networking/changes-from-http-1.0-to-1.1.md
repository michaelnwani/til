# Changes from HTTP 1.0 to HTTP 1.1

HTTP 1.0 was unofficially released to the world around December 1994, when Netscape (of Marc Andreessen-fame) released Netscape Navigator 1.0, which one could argue was the first popular web browser, and the harbinger of the highly consumer-friendly web we have today. I say 'unofficially' released because HTTP 1.0 was not a formal RFC specification or an Internet standard.. it's a term that just stuck. Anyway,

With HTTP 1.0, TCP connections couldn't be kept alive; for every TCP request, the server would send a response, and the connection would be terminated. For example, if you typed in a terminal:

`telnet google.com 80`

You would get back something like:

`Trying 173.194.123.73...`
`Connected to google.com.`
`Escape character is '^]'.`

To which if you specify a request using HTTP 1.0:

`GET /about/ HTTP/1.0`

You would receive back a response message from the server, including response headers and a payload, followed by an automatic connection termination:

`Connection closed by foreign host.`

Then you'd have to `telnet` back in again.

This led to some highly unfavorable and inefficient network performance issues (high RTT on a request, high latency delays, high power consumption, etc.). Nowadays one of the things we rely on for great performance is *connection keep-alives*, introduced in HTTP 1.1. HTTP 1.1 was first released in RFC 2068 in January 1997, and after two and a half years of development, was re-released in RFC 2616 in June of 1999. Following the last example, if you typed in a terminal:

`telnet google.com 80`

followed by `GET /about/ HTTP/1.1`

you would receive back a response from the server with more http headers than those that were in the HTTP 1.0 request (one that gets omitted because its implicit is the header *Connection: Keep-alive*), and more importantly, the connection wasn't terminated! Which means you can now request some other object:

`GET /finance HTTP/1.1 `

without having to `telnet` back in again!

1.1 also introduced some other substantial features such as chunked encoding transfers, byte-range requests, additional caching mechanisms, transfer encodings, request pipelining, and more.

That's it for now.