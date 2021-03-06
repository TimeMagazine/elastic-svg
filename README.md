# Elastic SVG elements
=======

v0.1.2

Scalable Vector Graphics are one of the Web's most triumphant technologies, but they're not as responsive as they might be. This is a very lightweight, dependency-free library that generates `svg` elements that fit to their container and scale <em>or don't scale</em> as desired.

## Installation

	npm install elastic-svg --save

And in node:

	import elasticSVG from 'elastic-svg'

Or you can [clone the repo](https://github.com/TimeMagazine/elastic-svg/) and include directly on the page, which adds an `elasticSVG` function to the `window`:

	<script src='./dist/elasticSVG.min.js'></script>

## Example

	import elasticSVG from 'elastic-svg';

	var b = elasticSVG("#container", {
		height: 400
	});

	var b = elasticSVG("#container", {
		aspect: 0.5
	});

## Options
You must pass `base` a selector representing the parent element in width the SVG will be created. You can optionally pass an object as a second argument representing options. These are:

| property | description |
| -------- | ----------- |
| `selector`  | The CSS3 query selector or HTML element in which to create the `<svg>` |
| `width`  | The initial width of the SVG. Defaults to width of parent |
| `height` | The initial height of the SVG. Defaults to the aspect ratio. |
| `aspect` | The aspect ratio of the SVG. Defaults to 0.618, approximately the [golden ratio](http://en.wikipedia.org/wiki/Golden_ratio) |
| `resize` | Info about how the SVG should scale. Current options are: <ul><li>`auto`: Set the `viewBox` to the initial width and height, thus scaling automatically according to the SVG specification </li></ul> |
| `onResize` | callback function to fire whenever the SVG resizes. This function will receive three arguments: the (new) width, height, and scale, which is (current width) / (original width) |

## How resizing works
Sometimes you want an SVG to resize according to its original proportions, other times you want the height to remain fixed while the width resizes. If you specify the `height`, it will remain fixed. If you don't, but you specify `aspect`, it remains proportional. If you specify neither, it defaults to an aspect ration of 0.618, or approximately the aspect ratio.

## A callback example

	var elasticSVG = require("elastic-svg");

	var b = base("#container", {
		onResize: function(w, h, z) {
			console.log("Scale is", z);
		}
	});

## Change log
+ *v0.1.1*: Allowing for elements as well as selectors
+ *v0.1.0*: Removing an annoying console log
+ *v0.0.8*: Made an ES6 module and created `./dist` from external packager
+ *v0.0.6*: Flipped module and AMD check so as not to confuse webpack
+ *v0.0.5*: Now stays fixed height if only height specified

## To Do
Allow to make an existing SVG responsive