<!--

@license Apache-2.0

Copyright (c) 2025 The Stdlib Authors.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

-->


<details>
  <summary>
    About stdlib...
  </summary>
  <p>We believe in a future in which the web is a preferred environment for numerical computation. To help realize this future, we've built stdlib. stdlib is a standard library, with an emphasis on numerical and scientific computation, written in JavaScript (and C) for execution in browsers and in Node.js.</p>
  <p>The library is fully decomposable, being architected in such a way that you can swap out and mix and match APIs and functionality to cater to your exact preferences and use cases.</p>
  <p>When you use stdlib, you can be absolutely certain that you are using the most thorough, rigorous, well-written, studied, documented, tested, measured, and high-quality code out there.</p>
  <p>To join us in bringing numerical computing to the web, get started by checking us out on <a href="https://github.com/stdlib-js/stdlib">GitHub</a>, and please consider <a href="https://opencollective.com/stdlib">financially supporting stdlib</a>. We greatly appreciate your continued support!</p>
</details>

# lastIndexOf

[![NPM version][npm-image]][npm-url] [![Build Status][test-image]][test-url] [![Coverage Status][coverage-image]][coverage-url] <!-- [![dependencies][dependencies-image]][dependencies-url] -->

> Return the last index of a specified search element along an [ndarray][@stdlib/ndarray/ctor] dimension.



<section class="usage">

## Usage

```javascript
import lastIndexOf from 'https://cdn.jsdelivr.net/gh/stdlib-js/blas-ext-last-index-of@esm/index.mjs';
```
The previous example will load the latest bundled code from the esm branch. Alternatively, you may load a specific version by loading the file from one of the [tagged bundles](https://github.com/stdlib-js/blas-ext-last-index-of/tags). For example,

```javascript
import lastIndexOf from 'https://cdn.jsdelivr.net/gh/stdlib-js/blas-ext-last-index-of@v0.1.0-esm/index.mjs';
```

You can also import the following named exports from the package:

```javascript
import { assign } from 'https://cdn.jsdelivr.net/gh/stdlib-js/blas-ext-last-index-of@esm/index.mjs';
```

#### lastIndexOf( x, searchElement\[, fromIndex]\[, options] )

Returns the last index of a specified search element along an [ndarray][@stdlib/ndarray/ctor] dimension.

```javascript
import array from 'https://cdn.jsdelivr.net/gh/stdlib-js/ndarray-array@esm/index.mjs';

// Create an input ndarray:
var x = array( [ 1.0, 2.0, 3.0, 2.0, 5.0, 6.0 ] );
// returns <ndarray>

// Perform operation:
var out = lastIndexOf( x, 2.0 );
// returns <ndarray>

var idx = out.get();
// returns 3
```

The function has the following parameters:

-   **x**: input [ndarray][@stdlib/ndarray/ctor]. Must have at least one dimension.
-   **searchElement**: search element. May be either a scalar value or an [ndarray][@stdlib/ndarray/ctor]. If provided a scalar value, the value is cast to the data type of the input [ndarray][@stdlib/ndarray/ctor]. If provided an [ndarray][@stdlib/ndarray/ctor], the value must have a shape which is [broadcast-compatible][@stdlib/ndarray/base/broadcast-shapes] with the non-reduced dimensions of the input [ndarray][@stdlib/ndarray/ctor]. For example, given the input shape `[2, 3, 4]` and `options.dim=0`, the search element [ndarray][@stdlib/ndarray/ctor] must have a shape which is [broadcast-compatible][@stdlib/ndarray/base/broadcast-shapes] with the shape `[3, 4]`.
-   **fromIndex**: index from which to begin searching (_optional_). May be either a scalar value or an [ndarray][@stdlib/ndarray/ctor] having an integer index or "generic" [data type][@stdlib/ndarray/dtypes]. If provided an [ndarray][@stdlib/ndarray/ctor], the value must have a shape which is [broadcast-compatible][@stdlib/ndarray/base/broadcast-shapes] with the non-reduced dimensions of the input [ndarray][@stdlib/ndarray/ctor]. For example, given the input shape `[2, 3, 4]` and `options.dim=0`, a provided [ndarray][@stdlib/ndarray/ctor] must have a shape which is [broadcast-compatible][@stdlib/ndarray/base/broadcast-shapes] with the shape `[3, 4]`. If provided a negative integer, the index at which to begin searching along a dimension is determined by counting backward from the last element (where `-1` refers to the last element). Default: `-1`.
-   **options**: function options (_optional_).

The function accepts the following options:

-   **dtype**: output ndarray [data type][@stdlib/ndarray/dtypes]. Must be an integer index or generic [data type][@stdlib/ndarray/dtypes].
-   **dim**: dimension over which to perform operation. If provided a negative integer, the dimension along which to perform the operation is determined by counting backward from the last dimension (where `-1` refers to the last dimension). Default: `-1`.
-   **keepdims**: boolean indicating whether the reduced dimensions should be included in the returned [ndarray][@stdlib/ndarray/ctor] as singleton dimensions. Default: `false`.

If the function is unable to find a search element along an [ndarray][@stdlib/ndarray/ctor], the corresponding element in the returned [ndarray][@stdlib/ndarray/ctor] is `-1`.

```javascript
import array from 'https://cdn.jsdelivr.net/gh/stdlib-js/ndarray-array@esm/index.mjs';

// Create an input ndarray:
var x = array( [ 1.0, 2.0, 3.0, 4.0, 5.0, 6.0 ] );
// returns <ndarray>

// Perform operation:
var out = lastIndexOf( x, 10.0 );
// returns <ndarray>

var idx = out.get();
// returns -1
```

By default, the function begins searching from the last element along the reduction dimension. To begin searching from a different index, provide a `fromIndex` argument.

```javascript
import array from 'https://cdn.jsdelivr.net/gh/stdlib-js/ndarray-array@esm/index.mjs';

// Create an input ndarray:
var x = array( [ 1.0, 2.0, 3.0, 4.0, 2.0, 6.0 ] );
// returns <ndarray>

// Perform operation:
var out = lastIndexOf( x, 2.0, 3 );
// returns <ndarray>

var idx = out.get();
// returns 1
```

By default, the function performs the operation over elements in the last dimension. To perform the operation over a different dimension, provide a `dim` option.

```javascript
import ndarray2array from 'https://cdn.jsdelivr.net/gh/stdlib-js/ndarray-to-array@esm/index.mjs';
import array from 'https://cdn.jsdelivr.net/gh/stdlib-js/ndarray-array@esm/index.mjs';

var x = array( [ [ -3.0, 2.0 ], [ -3.0, 4.0 ] ] );

var out = lastIndexOf( x, -3.0, {
    'dim': 0
});
// returns <ndarray>

var idx = ndarray2array( out );
// returns [ 1, -1 ]
```

By default, the function excludes reduced dimensions from the output [ndarray][@stdlib/ndarray/ctor]. To include the reduced dimensions as singleton dimensions, set the `keepdims` option to `true`.

```javascript
import array from 'https://cdn.jsdelivr.net/gh/stdlib-js/ndarray-array@esm/index.mjs';
import ndarray2array from 'https://cdn.jsdelivr.net/gh/stdlib-js/ndarray-to-array@esm/index.mjs';

var x = array( [ [ -3.0, 2.0 ], [ -3.0, 4.0 ] ] );

var opts = {
    'dim': 0,
    'keepdims': true
};

var out = lastIndexOf( x, -3.0, opts );
// returns <ndarray>

var idx = ndarray2array( out );
// returns [ [ 1, -1 ] ]
```

By default, the function returns an [ndarray][@stdlib/ndarray/ctor] having a [data type][@stdlib/ndarray/dtypes] determined by the function's output data type [policy][@stdlib/ndarray/output-dtype-policies]. To override the default behavior, set the `dtype` option.

```javascript
import ndarray2array from 'https://cdn.jsdelivr.net/gh/stdlib-js/ndarray-to-array@esm/index.mjs';
import dtype from 'https://cdn.jsdelivr.net/gh/stdlib-js/ndarray-dtype@esm/index.mjs';
import array from 'https://cdn.jsdelivr.net/gh/stdlib-js/ndarray-array@esm/index.mjs';

var x = array( [ 1.0, 2.0, 3.0, 4.0 ] );

var idx = lastIndexOf( x, 2.0, {
    'dtype': 'generic'
});
// returns <ndarray>

var dt = dtype( idx );
// returns 'generic'
```

#### lastIndexOf.assign( x, searchElement\[, fromIndex], out\[, options] )

Returns the last index of a specified search element along an [ndarray][@stdlib/ndarray/ctor] dimension and assigns results to a provided output [ndarray][@stdlib/ndarray/ctor].

```javascript
import array from 'https://cdn.jsdelivr.net/gh/stdlib-js/ndarray-array@esm/index.mjs';
import zeros from 'https://cdn.jsdelivr.net/gh/stdlib-js/ndarray-zeros@esm/index.mjs';

var x = array( [ 1.0, 2.0, 3.0, 2.0, 5.0, 6.0 ] );
var y = zeros( [], {
    'dtype': 'int32'
});

var out = lastIndexOf.assign( x, 2.0, y );
// returns <ndarray>

var idx = out.get();
// returns 3

var bool = ( out === y );
// returns true
```

The method has the following parameters:

-   **x**: input [ndarray][@stdlib/ndarray/ctor]. Must have at least one dimension.
-   **searchElement**: search element. May be either a scalar value or an [ndarray][@stdlib/ndarray/ctor]. If provided a scalar value, the value is cast to the data type of the input [ndarray][@stdlib/ndarray/ctor]. If provided an [ndarray][@stdlib/ndarray/ctor], the value must have a shape which is [broadcast-compatible][@stdlib/ndarray/base/broadcast-shapes] with the non-reduced dimensions of the input [ndarray][@stdlib/ndarray/ctor]. For example, given the input shape `[2, 3, 4]` and `options.dim=0`, the search element [ndarray][@stdlib/ndarray/ctor] must have a shape which is [broadcast-compatible][@stdlib/ndarray/base/broadcast-shapes] with the shape `[3, 4]`.
-   **fromIndex**: index from which to begin searching (_optional_). May be either a scalar value or an [ndarray][@stdlib/ndarray/ctor] having an integer index or "generic" [data type][@stdlib/ndarray/dtypes]. If provided an [ndarray][@stdlib/ndarray/ctor], the value must have a shape which is [broadcast-compatible][@stdlib/ndarray/base/broadcast-shapes] with the non-reduced dimensions of the input [ndarray][@stdlib/ndarray/ctor]. For example, given the input shape `[2, 3, 4]` and `options.dim=0`, a provided [ndarray][@stdlib/ndarray/ctor] must have a shape which is [broadcast-compatible][@stdlib/ndarray/base/broadcast-shapes] with the shape `[3, 4]`. If provided a negative integer, the index at which to begin searching along a dimension is determined by counting backward from the last element (where `-1` refers to the last element). Default: `-1`.
-   **out**: output [ndarray][@stdlib/ndarray/ctor].
-   **options**: function options (_optional_).

The method accepts the following options:

-   **dim**: dimension over which to perform operation. If provided a negative integer, the dimension along which to perform the operation is determined by counting backward from the last dimension (where `-1` refers to the last dimension). Default: `-1`.

</section>

<!-- /.usage -->

<section class="notes">

## Notes

-   Setting the `keepdims` option to `true` can be useful when wanting to ensure that the output [ndarray][@stdlib/ndarray/ctor] is [broadcast-compatible][@stdlib/ndarray/base/broadcast-shapes] with ndarrays having the same shape as the input [ndarray][@stdlib/ndarray/ctor].
-   The output data type [policy][@stdlib/ndarray/output-dtype-policies] only applies to the main function and specifies that, by default, the function must return an [ndarray][@stdlib/ndarray/ctor] having an integer index or "generic" [data type][@stdlib/ndarray/dtypes]. For the `assign` method, the output [ndarray][@stdlib/ndarray/ctor] is allowed to have any supported output [data type][@stdlib/ndarray/dtypes].

</section>

<!-- /.notes -->

<section class="examples">

## Examples

<!-- eslint no-undef: "error" -->

```html
<!DOCTYPE html>
<html lang="en">
<body>
<script type="module">

import discreteUniform from 'https://cdn.jsdelivr.net/gh/stdlib-js/random-array-discrete-uniform@esm/index.mjs';
import ndarray2array from 'https://cdn.jsdelivr.net/gh/stdlib-js/ndarray-to-array@esm/index.mjs';
import ndarray from 'https://cdn.jsdelivr.net/gh/stdlib-js/ndarray-ctor@esm/index.mjs';
import lastIndexOf from 'https://cdn.jsdelivr.net/gh/stdlib-js/blas-ext-last-index-of@esm/index.mjs';

// Generate an array of random numbers:
var xbuf = discreteUniform( 10, 0, 20, {
    'dtype': 'float64'
});

// Wrap in an ndarray:
var x = new ndarray( 'float64', xbuf, [ 5, 2 ], [ 2, 1 ], 0, 'row-major' );
console.log( ndarray2array( x ) );

// Perform operation:
var idx = lastIndexOf( x, 10.0, {
    'dim': 0
});

// Print the results:
console.log( ndarray2array( idx ) );

</script>
</body>
</html>
```

</section>

<!-- /.examples -->

<!-- Section for related `stdlib` packages. Do not manually edit this section, as it is automatically populated. -->

<section class="related">

</section>

<!-- /.related -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->


<section class="main-repo" >

* * *

## Notice

This package is part of [stdlib][stdlib], a standard library with an emphasis on numerical and scientific computing. The library provides a collection of robust, high performance libraries for mathematics, statistics, streams, utilities, and more.

For more information on the project, filing bug reports and feature requests, and guidance on how to develop [stdlib][stdlib], see the main project [repository][stdlib].

#### Community

[![Chat][chat-image]][chat-url]

---

## License

See [LICENSE][stdlib-license].


## Copyright

Copyright &copy; 2016-2026. The Stdlib [Authors][stdlib-authors].

</section>

<!-- /.stdlib -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="links">

[npm-image]: http://img.shields.io/npm/v/@stdlib/blas-ext-last-index-of.svg
[npm-url]: https://npmjs.org/package/@stdlib/blas-ext-last-index-of

[test-image]: https://github.com/stdlib-js/blas-ext-last-index-of/actions/workflows/test.yml/badge.svg?branch=v0.1.0
[test-url]: https://github.com/stdlib-js/blas-ext-last-index-of/actions/workflows/test.yml?query=branch:v0.1.0

[coverage-image]: https://img.shields.io/codecov/c/github/stdlib-js/blas-ext-last-index-of/main.svg
[coverage-url]: https://codecov.io/github/stdlib-js/blas-ext-last-index-of?branch=main

<!--

[dependencies-image]: https://img.shields.io/david/stdlib-js/blas-ext-last-index-of.svg
[dependencies-url]: https://david-dm.org/stdlib-js/blas-ext-last-index-of/main

-->

[chat-image]: https://img.shields.io/badge/zulip-join_chat-brightgreen.svg
[chat-url]: https://stdlib.zulipchat.com

[stdlib]: https://github.com/stdlib-js/stdlib

[stdlib-authors]: https://github.com/stdlib-js/stdlib/graphs/contributors

[umd]: https://github.com/umdjs/umd
[es-module]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules

[deno-url]: https://github.com/stdlib-js/blas-ext-last-index-of/tree/deno
[deno-readme]: https://github.com/stdlib-js/blas-ext-last-index-of/blob/deno/README.md
[umd-url]: https://github.com/stdlib-js/blas-ext-last-index-of/tree/umd
[umd-readme]: https://github.com/stdlib-js/blas-ext-last-index-of/blob/umd/README.md
[esm-url]: https://github.com/stdlib-js/blas-ext-last-index-of/tree/esm
[esm-readme]: https://github.com/stdlib-js/blas-ext-last-index-of/blob/esm/README.md
[branches-url]: https://github.com/stdlib-js/blas-ext-last-index-of/blob/main/branches.md

[stdlib-license]: https://raw.githubusercontent.com/stdlib-js/blas-ext-last-index-of/main/LICENSE

[@stdlib/ndarray/ctor]: https://github.com/stdlib-js/ndarray-ctor/tree/esm

[@stdlib/ndarray/dtypes]: https://github.com/stdlib-js/ndarray-dtypes/tree/esm

[@stdlib/ndarray/output-dtype-policies]: https://github.com/stdlib-js/ndarray-output-dtype-policies/tree/esm

[@stdlib/ndarray/base/broadcast-shapes]: https://github.com/stdlib-js/ndarray-base-broadcast-shapes/tree/esm

</section>

<!-- /.links -->
