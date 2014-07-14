# streaming-json-parser

This is a streaminig json parser that only parsers what you tell it.

The code is forked from https://github.com/alFReD-NSH/JSON-- and modified to work for me. It might not work for you.

## Install

```sh
npm install streaming-json-parser
```

## Example

```js
var JSONParser = require('streaming-json-parser');
var request = require('request');
var through = require('through2');

var parser = new JSONParser(['rows', true, 'name']);
parser.onValue = console.log.bind(console);

request('http://somejson')
.pipe(through(function (chunk, done) {
  parser.write(chunk);
  done();
}));
```

Note that the `parser.write` only accepts a Buffer instance.