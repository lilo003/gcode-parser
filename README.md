# gcode-parser [![build status](https://travis-ci.org/cheton/gcode-parser.svg?branch=master)](https://travis-ci.org/cheton/gcode-parser) [![Coverage Status](https://coveralls.io/repos/cheton/gcode-parser/badge.svg?branch=master&service=github)](https://coveralls.io/github/cheton/gcode-parser?branch=master)
[![NPM](https://nodei.co/npm/gcode-parser.png?downloads=true&stars=true)](https://nodei.co/npm/gcode-parser/)

## Install

`npm install --save gcode-parser`

## Usage
```js
var fs = require('fs');
var parser = require('gcode-parser');

// Parse from file
var file = 'example.nc';
parser.parseFile(file, function(err, results) {
    console.log(results);
});

// Parse from stream
var stream = fs.createReadStream(file, { encoding: 'utf8' });
parser.parseStream(stream, function(err, results) {
    console.log(results);
});

// Parse from string
var str = fs.readFileSync(file, 'utf8');
parser.parseString(str, function(err, results) {
    console.log(results);
});
```

## Advanced Usage
```js
var parser = require('gcode-parser');

parser.parseFile('example.nc', function(err, results) {
    if (err) {
        console.error(err);
        return;
    }
    console.log(results);
})
.on('data', function(data) {
    console.log(data);
})
.on('progress', function(o) {
    console.log(o.current, o.total);
})
.on('end', function(results) {
    console.log(results);
})
```

## Toolpath Generator
Check out [gcode-toolpath](https://github.com/cheton/gcode-toolpath) for an example.
