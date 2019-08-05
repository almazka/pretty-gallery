# prettyPhoto

In this package contains Facebook theme only

![Facebook pretty photo theme](http://www.no-margin-for-errors.com/wp-content/uploads/2009/11/facebook.jpg)

**Attention!** There are some changes in library js code: I increase container size for images for correct view on mobile devices.

The following minor changes have been made to the code:
The value 200 was replaced with 40. To stretch the image across the entire width of the screen.

`jquery.prettyPhoto.js`:

```javascript
while (!fitting){
    if((pp_containerWidth > windowWidth)){
        imageWidth = (windowWidth - 40); // here was 200
        imageHeight = (height/width) * imageWidth;
    }else if((pp_containerHeight > windowHeight)){
        imageHeight = (windowHeight - 40); // here was 200
        imageWidth = (width/height) * imageHeight;
    }else{
        fitting = true;
    };

    pp_containerHeight = imageHeight, pp_containerWidth = imageWidth;
};
```

Otherwise the plug-in code is original.

## Usage

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
		slideshow: 3000,
		opacity: 0.60,
		show_title: true,
		default_width: 500,
		autoplay_slideshow: false,
		default_height: 500,
		counter_separator_label: ' из ',
		theme: 'facebook',
		modal: false,
		social_tools: false,
		allow_resize: true,
		changepicturecallback: function () {
			// hide expand icon on small screens
            var windowWidth = $(window).width(),
                $pp_pic_holder = $('.pp_pic_holder');
            if (imgPreloader.width > windowWidth) {
                $pp_pic_holder.find('.pp_expand').hide();
            }
        },
	} );
}
```

### All the possibilities
```javascript
if( $( "a[rel^='prettyPhoto']" ).length > 0 ) {
	$( "a[rel^='prettyPhoto']" ).prettyPhoto( {
		hook: 'rel', // the attribute tag to use for prettyPhoto hooks. default: 'rel'. For HTML5, use "data-rel" or similar.
		animation_speed: 'fast', // fast/slow/normal
		ajaxcallback: function() {},
		slideshow: 5000, // false OR interval time in ms
		autoplay_slideshow: false, // true/false
		opacity: 0.80, // Value between 0 and 1
		show_title: true, // true/false
		allow_resize: true, // Resize the photos bigger than viewport. true/false
		allow_expand: true, // Allow the user to expand a resized image. true/false
		default_width: 500,
		default_height: 344,
		counter_separator_label: '/', // The separator for the gallery counter 1 "of" 2
		theme: 'pp_default', // light_rounded / dark_rounded / light_square / dark_square / facebook
		horizontal_padding: 20, // The padding on each side of the picture
		hideflash: false, // Hides all the flash object on a page, set to TRUE if flash appears over prettyPhoto
		wmode: 'opaque', // Set the flash wmode attribute
		autoplay: true, // Automatically start videos: True/False
		modal: false, // If set to true, only the close button will close the window
		deeplinking: true, // Allow prettyPhoto to update the url to enable deeplinking.
		overlay_gallery: true, // If set to true, a gallery will overlay the fullscreen image on mouse over
		overlay_gallery_max: 30, // Maximum number of pictures in the overlay gallery
		keyboard_shortcuts: true, // Set to false if you open forms inside prettyPhoto
		changepicturecallback: function(){}, // Called everytime an item is shown/changed
		callback: function(){}, // Called when prettyPhoto is closed
		ie6_fallback: true,
		markup: '<div class="pp_pic_holder"> \
			<div class="ppt">&nbsp;</div> \
			<div class="pp_top"> \
				<div class="pp_left"></div> \
				<div class="pp_middle"></div> \
				<div class="pp_right"></div> \
			</div> \
			<div class="pp_content_container"> \
				<div class="pp_left"> \
				<div class="pp_right"> \
					<div class="pp_content"> \
						<div class="pp_loaderIcon"></div> \
						<div class="pp_fade"> \
							<a href="#" class="pp_expand" title="Expand the image">Expand</a> \
							<div class="pp_hoverContainer"> \
								<a class="pp_next" href="#">next</a> \
								<a class="pp_previous" href="#">previous</a> \
							</div> \
							<div id="pp_full_res"></div> \
							<div class="pp_details"> \
								<div class="pp_nav"> \
									<a href="#" class="pp_arrow_previous">Previous</a> \
									<p class="currentTextHolder">0/0</p> \
									<a href="#" class="pp_arrow_next">Next</a> \
								</div> \
								<p class="pp_description"></p> \
								<div class="pp_social">{pp_social}</div> \
								<a class="pp_close" href="#">Close</a> \
							</div> \
						</div> \
					</div> \
				</div> \
				</div> \
			</div> \
			<div class="pp_bottom"> \
				<div class="pp_left"></div> \
				<div class="pp_middle"></div> \
				<div class="pp_right"></div> \
			</div> \
		</div> \
		<div class="pp_overlay"></div>',
		gallery_markup: '<div class="pp_gallery"> \
			<a href="#" class="pp_arrow_previous">Previous</a> \
			<div> \
				<ul> \
					{gallery} \
				</ul> \
			</div> \
			<a href="#" class="pp_arrow_next">Next</a> \
		</div>',
		image_markup: '<img id="fullResImage" src="{path}" />',
		flash_markup: '<object classid="clsid:D27CDB6E-AE6D-11cf-96B8-444553540000" width="{width}" height="{height}"><param name="wmode" value="{wmode}" /><param name="allowfullscreen" value="true" /><param name="allowscriptaccess" value="always" /><param name="movie" value="{path}" /><embed src="{path}" type="application/x-shockwave-flash" allowfullscreen="true" allowscriptaccess="always" width="{width}" height="{height}" wmode="{wmode}"></embed></object>',
		quicktime_markup: '<object classid="clsid:02BF25D5-8C17-4B23-BC80-D3488ABDDC6B" codebase="http://www.apple.com/qtactivex/qtplugin.cab" height="{height}" width="{width}"><param name="src" value="{path}"><param name="autoplay" value="{autoplay}"><param name="type" value="video/quicktime"><embed src="{path}" height="{height}" width="{width}" autoplay="{autoplay}" type="video/quicktime" pluginspage="http://www.apple.com/quicktime/download/"></embed></object>',
		iframe_markup: '<iframe src ="{path}" width="{width}" height="{height}" frameborder="no"></iframe>',
		inline_markup: '<div class="pp_inline">{content}</div>',
		custom_markup: '',
		social_tools: '<div class="twitter"><a href="http://twitter.com/share" class="twitter-share-button" data-count="none">Tweet</a><script type="text/javascript" src="http://platform.twitter.com/widgets.js"></script></div><div class="facebook"><iframe src="//www.facebook.com/plugins/like.php?locale=en_US&href={location_href}&amp;layout=button_count&amp;show_faces=true&amp;width=500&amp;action=like&amp;font&amp;colorscheme=light&amp;height=23" scrolling="no" frameborder="0" style="border:none; overflow:hidden; width:500px; height:23px;" allowTransparency="true"></iframe></div>' // html or false to disable
	} );
}
```

[Pretty Photo Site](http://www.no-margin-for-errors.com/projects/prettyPhoto-jquery-lightbox-clone/)
