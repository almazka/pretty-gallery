# prettyPhoto

##### Create the element in your HTML:
```html
	<a href="images/lepestok_max.jpg" rel="prettyPhoto[gallery]" title="Beauty Flower">
		<img src="images/lepestok_min.jpg" alt="">
	</a>
```

##### Include jQuery:

```html
	<script src="http://ajax.googleapis.com/ajax/libs/jquery/2.0.0/jquery.min.js"></script>
```

##### Include html:

```html
	<link rel="stylesheet" type="text/css" href="/css/prettyPhoto.css" />
	<script type="text/javascript" src="js/jquery.prettyPhoto.js"></script>
```

##### Or Sass:
```css
	@import url(../css/prettyPhoto.css);
```

#### In the main.js:

```javascript
if( $( "a[rel^='prettyPhoto']" ).length > 0 ) {
	$( "a[rel^='prettyPhoto']" ).prettyPhoto( {
		animation_speed: 'fast',
		autoplay_slideshow: true,
		slideshow: 3000,
		opacity: 0.60,
		show_title: true,
		default_width: 500,
		default_height: 500,
		counter_separator_label: ' из ',
		theme: 'facebook', // themes: light_rounded, dark_rounded, light_square, dark_square или facebook
		modal: false, // if true - closing only press Close button
		social_tools: false,
	} );
}

### 