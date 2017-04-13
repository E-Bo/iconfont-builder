# iconfont-builder

[![Build Status](https://travis-ci.org/q-iconfont/iconfont-builder.svg?branch=master)](https://travis-ci.org/q-iconfont/iconfont-builder)
[![npm](https://img.shields.io/npm/dm/iconfont-builder.svg)](https://www.npmjs.com/package/iconfont-builder)

[中文版](https://github.com/malcolmyu/iconfont-builder/blob/master/README_CN.md)

## Introduction

Iconfont-builder is a node.js package for providing a middleware that create some font files.

## Installation (via [npm](https://npmjs.org/package/iconfont-builder))

```bash
$ npm i --save iconfont-builder
```

## Usage

### Simple Usage

```js
var builder = require('iconfont-builder');
var path = require('path');

var options = {
    icons: [
        {
            name: 'www-font-o',
            file: 'abc.svg',
            codepoint: 61441
        }
    ],
    src: path.join(__dirname, 'src'),
    fontName: 'iconfont',
    descent: 0,
    dest: path.join(__dirname, 'dest')
};

builder(options)
    .then().catch();
```

### List of options

#### icons

Type: `Array<Object>`

Example:

```js
{
    name: 'www-font-o', // className of icon
    file: 'abc.svg',    // fileName of icon
    codepoint: 61441    // unicode of icon
}
```

#### writeFiles

Type: `Boolean`

Default: `true`

It is possible to not create font files but get the attribute **d** of each icon svg. The attribute d contains all paths' information of an icon, which can be use to draw a svg icon.

#### readFiles

Type: `Boolean`

Default: `true`

You can only use attribute **d** to create font files! If this param is `false`, the Object in param `icons` should have attribute `d`.

#### fontName

Type: `String`

Default: `'iconfont'`

Name of font and font files.

#### startCodePoint

Type: `Number`

Default: `0xF000`

Start of font's unicode in DEC(e.g. `61441`) or HEX(e.g. `0xF001`). When passing `options` without `icons`, builder will use `startCodePoint` as the first unicode of font icon, and the unicode of each remaining icons will increased by one in order.

#### src

Type: `String`

Default: `'.'`

Directory of source svg font files.

#### dest

Type: `String`

Directory for generated font files.

#### descent

Type: `Number`

Default: `0`

The font descent. It's useful to fix the font baseline yourself.

Warning: The descent is a positive value!

## Author

[missmiss](http://www.weibo.com/ssherrylliu)

[malcolmyu](https://twitter.com/minghaoyu)
