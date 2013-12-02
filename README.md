# jquery-cropbox plugin.

jQuery plugin for in-place image cropping (zoom & pan, as opposed to select and drag).

This plugin depends only on jQuery. If either `Hammer.js` or `jquery.hammer.js` is
loaded, the cropbox plugin will support gestures for panning and zooming
the cropbox. Similary, if the `jquery.mousewheel.js` plugin is loaded, then the
cropbox plugin will support zoom in & out using the mousewheel. All
dependencies on third party libraries (other than jQuery) are strictly
optional. Support for CommonJS and AMD loading is built in.

In browsers that support the HTML5 FIle API and Canvas API, the cropbox
plugin provides mehtods to crop the image on the client and obtain the
resulting cropped image as a Data URL or a binary blob to upload it to
the server.

Check out the plugin in action here http://acornejo.github.io/jquery-cropbox/

**Credits:**
This plugin started as a fork of https://github.com/terebentina/jQcrop.

## Usage

```javascript
	$('yourimage').cropbox({
		 width: 200
		,height: 200
	}).on('cropbox', function(e, data) {
        console.log('coordinates: ' + data);
	});
```
## Options

<table>
	<tr>
		<th>Option</th>
		<th>Type</th>
		<th>Default</th>
		<th>Required</th>
		<th>Description</th>
	</tr>
	<tr>
		<td>width</td>
		<td>integer</td>
		<td>200</td>
		<td>no</td>
		<td>Width in pixels of the cropping window</td>
	</tr>
	<tr>
		<td>height</td>
		<td>integer</td>
		<td>200</td>
		<td>no</td>
		<td>Height in pixels of the cropping window</td>
	</tr>
	<tr>
		<td>zoom</td>
		<td>integer</td>
		<td>10</td>
		<td>no</td>
		<td>Number of incremental zoom steps. With the default of 10, you have to click the zoom-in button 9 times to reach 100%.</td>
	</tr>
	<tr>
		<td>controls</td>
		<td>string/jquery</td>
		<td>null</td>
		<td>no</td>
		<td>If not null, this is the entire html block that should appear on hover over the image for instructions and/or buttons (could include the zoom in/out buttons for example). If null, the default html block is used which has the text "Click to drag" and the zoom in/out buttons. Use '' (or false) if you don't want anything to appear.</td>
	</tr>
</table>

## Event

To get the crop results, bind a function on the `cropbox` event or read the object's result property .

```javascript
    $('yourimage').cropbox({width: 250, height: 250})
    .on('cropbox', function (e, result) {
        console.log(result);
    });
```

A reference to the cropbox object can be accessed like so:
```javascript
	var crop = $('yourimage').data('cropbox');
	console.log(crop.result);
```

You then have access to all the properties and methods used for that specific element.
