# Octus-editor
Octus Editor is a simple, light weight bbcode editor built with HTML, CSS and JS with support for keyboard shortcuts. Octus editor allows for custom bbcodes by simply adding data tags to the buttons, there are many options so make sure to look below for a full demonstration.

# Demo
Check out Octus Editor in action over at the [GitHub page @ julianrichen.github.io/octus-editor](http://julianrichen.github.io/octus-editor/).

![Octus-editor](http://i.imgur.com/xdGdPnl.jpg)
![Octus-editor dark](http://i.imgur.com/BwUL3Qf.jpg)

## Browser Support
Octus Editor works in most modern browsers and has legacy code for older IE versions. If you find a compatibility issue please open up a bug report under the issue tab.

## Adding custom bbcodes
Octus editor allows for custom tags and customizable style bars by simply changing the tags inside of the `.styles` class. You can create a group of styles by placing the styles in separate `<ul>` elements. Example:
```html
<div class="styles group">
	<ul>
		Style group one...
	</ul>
	<ul>
		Style group two...
	</ul>
	<ul>
		Style group three...
	</ul>
</div>
```

Individual styles are shown as buttons in the style bar. They can be added by creating a `<li>` element.
```html
<ul>
	<li data-tag="bbcode_tag_1">bbcode_tag_1</li>
	<li data-tag="bbcode_tag_2">bbcode_tag_2</li>
	<li data-tag="bbcode_tag_3">bbcode_tag_3</li>
</ul>
```

If I wanted to create a group of styles for Bold, Italic and Underline I would do like so.
```html
<ul>
	<li data-tag="b">B</li>
	<li data-tag="i">I</li>
	<li data-tag="u">U</li>
</ul>
```

### Sub-tag
Subtags allow for extra code inside of a bbcode tag, for example selecting a specific font with `[font=Open Sans] [/font]`. Adding a sub-tag is done by using `data-subtag="subtag"`, example:
```html
<ul>
	<li data-tag="font" data-subtag="Open Sans">Open Sans</li>
	<li data-tag="font" data-subtag="Times New Roman">Times New Roman</li>
	<li data-tag="font" data-subtag="Helvetica">Helvetica</li>
</ul>
```

`data-subtag` only works when `data-tag` is present.

### Snippets
Snippets are created with `data-snippet="snippet"` and are a way to add a pieces of text to the body without wrapping the content like you would with bbcodes. A perfect example is for smilies:
```html
<ul>
	<li data-snippet=":)">Smile</li>
	<li data-snippet=":D">Grin</li>
	<li data-snippet=":(">Sad</li>
</ul>
```

### Drop-downs
Sometimes a style has to many options to be shown in the default bar and needs to be hidden with a drop down. You can turn a button into a drop down using the `.dropdown` class on a `<li>` element with a `<ul>` element nested, an example would be for fonts:
```html
<li class="dropdown">
	Font Family
	<ul>
		<li data-tag="font" data-subtag="Open Sans">Open Sans</li>
		<li data-tag="font" data-subtag="Times New Roman">Times New Roman</li>
		<li data-tag="font" data-subtag="Helvetica">Helvetica</li>
	</ul>
</li>
```

### Special tags (url & youtube)
The url and youtube buttons have unique JavaScript functions, these buttons detect if the tag is labelled `url` or `youtube` and create a pop-up asking for a url and link text. This is done automatically and must be edited in the JavaScript file to disable.

### All together
Here is an example of a complete form with support for Bold, Italtic, Underline, Strike and Font support.
```html
<div class="octus-editor group">
	<div class="styles group">
		<ul>
			<li data-tag="b" class="bold" accesskey="B">B</li>
			<li data-tag="i" class="italic" accesskey="I">I</li>
			<li data-tag="u" class="underline" accesskey="U">U</li>
			<li data-tag="s" class="strike">S</li>
		</ul>
		<li class="dropdown">
			Font Family
			<ul>
				<li data-tag="font" data-subtag="Open Sans">Open Sans</li>
				<li data-tag="font" data-subtag="Times New Roman">Times New Roman</li>
				<li data-tag="font" data-subtag="Helvetica">Helvetica</li>
			</ul>
		</li>
	</div>
	<noscript><div class="no-script">This content editor needs javascript, please enable javascript to use this editor!</div></noscript>
	<div class="textarea group">
		<textarea rows="3" cols="17" id="editor_content"></textarea>
	</div>
	<div class="options group">
		<a class="button" href="#">Preview</a>
		<a class="button" href="#">Post</a>
	</div>
</div>
```
