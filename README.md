Purpose
-------

This widget toggles the display of two div blocks, hiding one and displaying the other, but also triggers a callback to the surrounding wrapper area to animate a resize of the surrounding space (i.e. wrapper div) to fit the space needed by the new content. This sounds far more simplistic than it actually is, at times, as there are some "gotchas" with this task including:

- if the space is a modal window or something in a fixed position, make sure that the dimensions do not exceed the dimensions of the browser viewport
- waiting for all of the images to be loaded before taking measurements
- properly measuring the space needed by the new content prior to actually displaying it on the page

In addition to accounting for these considerations, this widget provides the following features:

- optional callbacks before and after the start/end of the animation
- offset values built into width and height calculations
- options to constrain the width or height

Usage
-----

	var nmresizer = new Y.Nmresizer();
	nmresizer.loadAndResize({
		olddiv:[old div tag],  // e.g. '#olddiv'
		newdiv:[new div tag],  // e.g. '#newdiv'
		animDuration:0.5,
		resizediv:[surrounding div wrapper to be animated],  // e.g. '#mystuff_wrapper'
		maxWidth:Y.one('body').get('winWidth') - 40,  // i.e. viewport width minus 40 pixels
		maxHeight:Y.one('body').get('winHeight') - 40,  // i.e. viewport height minus 40 pixels
		offsetHeight:0,  // number of pixels to add to height calculations
		offsetWidth:0,  // number of pixels to add to width calculations
		onStart:Y.bind(beforeResize),  // callback function to be fired before animation start, where "beforeResize" is your function name
		onEnd:Y.bind(afterResize)  // callback function to be fired before animation start, where "afterResize" is your function name
	});
	
Full Example
------------

[Click here](http://mixolydian.netmusician.org/~joe/yuidemos/NetMusician-Resizer-YUI-Widget/demo.html)
	