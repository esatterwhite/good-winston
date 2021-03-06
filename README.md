# good-winston

A [hapi][0] [good-reporter][1] to [winston][2] logging adapter.

## Installation

``` bash
  $ npm install winston
  $ npm install good-winston
```

## Usage

To use the `GoodWinston` transport in winston, you simply need to require it and
then either add it to an existing winston logger or pass an instance to a new
winston logger:

``` js
var GoodWinston = require('good-winston');
var winston = require('winston');

server.register({
  register: require('good'),
  options: {
    reporters: [
      new GoodWinston({
        ops: '*',
        request: '*',
        response: '*',
        log: '*',
        error: '*'
      }, winston)
    ]
  }
}, function(err) {
  if (err) {
    return server.log(['error'], 'good load error: ' + err);
  }
});
```

The following `options` are availble to configure `GoodWinston`:

* __error_level:__ Map all good `error` events to this winston level (Default `error`).
* __ops_level:__ Map all good `ops` events to this winston level (Default `info`).
* __request_level:__ Map all good `request` events to this winston level (Default `info`).
* __response_level:__ Map all good `response` events to this winston level (Default `info`).
* __other_level:__ Map all other good events to this winston level (Default `info`).

[0]: http://hapijs.com
[1]: https://github.com/hapijs/good-reporter
[2]: https://github.com/winstonjs/winston
