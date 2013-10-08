# [verge](../../)

<b>verge</b> is a compact (<1k gzipped) set of cross-browser viewport utilities written in native JavaScript. It includes the ability to detect if an element is in the current viewport. It works as a standalone module, an [ender](#ender) module, or as a [jQuery](#jquery) plugin.

<pre>
<code>$ <a href="https://npmjs.org/package/verge">npm install verge</a></code>
</pre>

## API ([1.8](../../releases))

In <b>standalone</b> usage, methods are available on the <b>verge</b> namespace. (`verge.aspect()`, &hellip;)

The docs below use <b>$</b> to denote <b>verge</b> or a [host lib](#integrate).

- <a href="#aspect"><b>$.aspect()</b></a>
- <a href="#inviewport"><b>$.inViewport()</b></a>
- <a href="#inx"><b>$.inX()</b></a>
- <a href="#iny"><b>$.inY()</b></a> 
- <a href="#mq"><b>$.mq()</b></a>
- <a href="#rectangle"><b>$.rectangle()</b></a>
- <a href="#viewportw"><b>$.viewportW()</b></a>
- <a href="#viewporth"><b>$.viewportH()</b></a>

***

### $.viewportW()

```js
$.viewportW()  // -> viewport width in pixels
```

### $.viewportH()

```js
$.viewportH()  // -> viewport height in pixels
```

### $.inViewport()

Test if any part of an element (or the first element in a matched set) is in the current viewport. Returns **boolean**.

```js
$.inViewport(elem)       // true if elem is in the current viewport
$.inViewport(elem, 100)  // true if elem is in the current viewport or within 100px of it
$.inViewport(elem, -100) // true if elem is in the current viewport and not within 99px of the edge
```

<b>Tip:</b> If you're dealing with a page that only ever scrolls in one direction, it is faster to substitute `inViewport` with `inY` or `inX`. On pages that **never** scroll horizontally, `inX` always returns `true`. On pages that **never** scroll vertically, `inY` always returns `true`. In other words, use `inY` on sites that scroll **only** vertically, and `inX` on sites that scroll **only** horizontally. If the viewport width is greater than or equal to the `document` width, then `inX` will always return `true`.

```js
$.inViewport(elem) === $.inX(elem) && $.inY(elem) // always true
```

### $.inX()

Test if any part of an element (or the first element in a matched set) is in the same x-axis section as the viewport. Returns **boolean**. 

```js
$.inX(elem)       // true if elem is in same x-axis as the viewport (exact)
$.inX(elem, 100)  // true if elem is in same x-axis as the viewport or within 100px of it
$.inX(elem, -100) // true if elem in is the viewport and not within 99px of the edge
```

### $.inY()

Test if any part of an element (or the first element in a matched set) is in the same y-axis section as the viewport. Returns **boolean**.

```js
$.inY(elem)       // true if elem is in same y-axis as the viewport (exact)
$.inY(elem, 100)  // true if elem is in same y-axis as the viewport or within 100px of it
$.inY(elem, -100) // true if elem in is the viewport and not within 99px of the edge
```

### $.mq()

Test if a [media query](http://airve.com/mq/) is active.

```js
$.mq(mediaQueryString)
$.mq('(min-color:2)')
$.mq('tv')
```

### $.rectangle()
#### $.rectangle(element, cushion?)

Get an a <b>object</b> containing the properties `top`, `bottom`, `left`, `right`, `width`, and `height` with respect to the top-left corner of the current viewport, and with an optional cushion amount. Its return is like that of the native [getBoundingClientRect](https://developer.mozilla.org/en/DOM/element.getBoundingClientRect).

The optional <b>cushion</b> parameter is an amount of pixels to act as a cushion around the element. If none is provided then it defaults to `0` and the rectangle will match the native rectangle. If a cushion is specified, the properties are adjusted according to the cushion amount. If the cushion is **positive** the rectangle will represent an area that is larger that the actual element. If the cushion is **negative** then the rectangle will represent an area that is **smaller** that the actual element. 

```js
$.rectangle(element)       // rectangle object
$.rectangle(element, 100)  // rectangle object adjusted by 100 pixels
```

### $.aspect()
#### $.aspect(object?)

Get the aspect ratio of the viewport <b>or</b> of an object with width/height properties.

```
$.aspect()         // -> viewport aspect ratio
$.aspect(element)  // -> element aspect ratio
$.aspect(screen)   // -> device aspect ratio
1 < $.aspect()     // => landscape orientation
```

## <a name="integrate"></a>Integrate

### <a href="http://jquery.com">jQuery</a>

```js
jQuery.extend(verge)
```

### <a href="https://github.com/ender-js">ender</a>

```sh
$ ender build verge
```

## Developers

<b>Contribute</b> by making edits in [`/src`](./src) or reporting [issues](../../issues).

```sh
$ npm install
$ grunt jshint:src
```

## Fund

Fund development with [tips to @ryanve](https://www.gittip.com/ryanve/) =)

## [MIT License](http://opensource.org/licenses/MIT)

Copyright (C) 2012 by [Ryan Van Etten](https://github.com/ryanve)