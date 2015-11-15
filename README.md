# node-fastcgi-client

A FastCGI client implementation in Node.js, mainly designed for cummunication with PHP.

# API

`npm install node-fastcgi-client`. Use `require('node-fastcgi-client')` to get a `fastcgiConnector`.

`var client = fastcgiConnector(options)` Create a FastCGI client. Available options:

* `host` The server name or IP, default to '127.0.0.1'.
* `port` The server port, default to 9000.
* `connectionTimeout` The timeout for network connection in milliseconds, default to 20000.
* `skipCheckServer` Skip checking and getting options from the server.
* `maxConns` The default value of maximum concurrent connections to the server.
* `maxReqs` The default value of maximum concurrent requests to the server.
* `mpxsConns` The default value of using concurrency over connections or not.
* Event `ready` Client is ready for accepting request.
* Event `error` An error occurred and returned as 1st argument of event handler.

`client.request(params, cb)` Create a new request.
An error object would be passed to `cb` as 1st argument on failed, otherwise a `request` argument is passed as 2nd argument.

The `request` object:

* `request.abort()` Send an abort request. The request is not ended after the server responds.
* `request.stdin` The writable stdin stream.
* `request.stdout` The readable stdout stream.
* `request.stderr` The readable stderr stream.
* `request.getExitStatus()` Return exit code, or an error if not normally ended. It would be ready before the `end` events of stdout and stderr streams.

# test

You should have PHP-CGI installed and PHP5 FPM service running in 127.0.0.1:9000.

Then use `mocha` to test.

# LICENSE

MIT