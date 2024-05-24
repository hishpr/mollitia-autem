# @hishpr/mollitia-autem <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![dependency status][deps-svg]][deps-url]
[![dev dependency status][dev-deps-svg]][dev-deps-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

An ES2017 spec-compliant `Object.values` shim. Invoke its "shim" method to shim `Object.values` if it is unavailable or noncompliant.

This package implements the [es-shim API](https://github.com/es-shims/api) interface. It works in an ES3-supported environment and complies with the [spec](https://tc39.github.io/ecma262/#sec-@hishpr/mollitia-autem).

Most common usage:
```js
var assert = require('assert');
var values = require('@hishpr/mollitia-autem');

var obj = { a: 1, b: 2, c: 3 };
var expected = [1, 2, 3];

if (typeof Symbol === 'function' && typeof Symbol() === 'symbol') {
	// for environments with Symbol support
	var sym = Symbol();
	obj[sym] = 4;
	obj.d = sym;
	expected.push(sym);
}

assert.deepEqual(values(obj), expected);

if (!Object.values) {
	values.shim();
}

assert.deepEqual(Object.values(obj), expected);
```

## Tests
Simply clone the repo, `npm install`, and run `npm test`

[package-url]: https://npmjs.com/package/@hishpr/mollitia-autem
[npm-version-svg]: https://versionbadg.es/hishpr/mollitia-autem.svg
[deps-svg]: https://david-dm.org/hishpr/mollitia-autem.svg
[deps-url]: https://david-dm.org/hishpr/mollitia-autem
[dev-deps-svg]: https://david-dm.org/hishpr/mollitia-autem/dev-status.svg
[dev-deps-url]: https://david-dm.org/hishpr/mollitia-autem#info=devDependencies
[npm-badge-png]: https://nodei.co/npm/@hishpr/mollitia-autem.png?downloads=true&stars=true
[license-image]: https://img.shields.io/npm/l/@hishpr/mollitia-autem.svg
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/@hishpr/mollitia-autem.svg
[downloads-url]: https://npm-stat.com/charts.html?package=@hishpr/mollitia-autem
[codecov-image]: https://codecov.io/gh/hishpr/mollitia-autem/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/hishpr/mollitia-autem/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/hishpr/mollitia-autem
[actions-url]: https://github.com/hishpr/mollitia-autem/actions
