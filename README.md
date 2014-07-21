# ThickBox

ThickBox is a webpage UI dialog widget written in JavaScript on top of the jQuery library. Its function is to show a single image, multiple images, inline content, iframed content, or content served through AJAX in a hybrid modal.

It was developed by Cody Lindley and last updated to version 3.1 on 08/08/2007

This repository contains the ThickBox library as bower module for projects relying on the library

## Deprectation Warning

It seems that the author of ThickBox doesn't have maintained the code for more than 7 years. It may and probably will have problems with recent versions of jQuery which drop legacy browser support.
Anyway ThickBox is still used. So if you really need it within your project and you do not want to download and maintain the library by yourself, you might want to use this bower component.

## Notice about README

The README file contains the texts from the author's project website. It's taken and converted to markdown to have a reference beside the files you will find in the repository

## Features

* ThickBox was built using the super lightweight jQuery library. Compressed, the jQuery library is 20k, uncompressed it's 58k.
* The ThickBox JavaScript code and CSS file only add an additional 15k (only 10k by using the thickbox-compressed.js) on top of the jQuery code. The CSS file could additionally be compressed if need be.
* ThickBox will resize images that are bigger than the browser window.
* ThickBox offers versatility (images, iframed content, inline content, and AJAX content).
* ThickBox will hide form elements in Windows IE 6.
* ThickBox will remain centered in the window even when the user scrolls the page or changes the size of the browser window. Clicking an image, the overlay, or close link will remove ThickBox.
* Due to the ThickBox creator's view that transitions should be tailored by individual authors, ThickBox windows do not implement fancy transitions. Feel free to add them as you see fit. Is this a feature? Well, some might say it is.
* ThickBox can be invoked from a link element, input element (typically a button), and the area element (image maps).

## Installation

If you prefer to use the original library please visit http://codylindley.com/thickbox/

Otherwise you may want to use bower to install the library to your project:

    bower install jquery-thickbox --save

## Integration

ThickBox depends on jQuery. So you need to include jQuery *before* ThickBox into your website. The following example shows how it may be done.

    <script type="text/javascript" src="path-to-file/jquery.js"></script>
    <script type="text/javascript" src="path-to-file/thickbox.js"></script>

Paths may be different depending on your file structure. Because ThickBox is a bit aged yet, you should not expect that it will work with latest-greatest jQuery versions - but for now it works fine with jQuery 2.1.1.

You also must include the ThickBox CSS file into your website:

    <link rel="stylesheet" href="path-to-file/thickbox.css" type="text/css" media="screen" />

Please be aware that ThickBox uses a special PNG image (mayFFBgHack.png) which is referenced by the CSS file. ThickBox also uses a loading animation which basically is a animated GIF image with the name loadingAnimation.gif.

Depending on your file structure it might be necessary to update the path to this files.

## Supported and tested browsers

Windows IE 6.0, Windows IE 7+, Windows FF 2.0.0.6+, Windows Opera 9.0+, Macintosh Safari 2.0.4+, Macintosh FF 2.0.0.6+, Macintosh Opera 9.10+

## Examples

### Single Image

This is the simplest example of ThickBox functionality. This example places a single image in a ThickBox.

* Create a link element (<a href>)
* Give the link a class attribute with a value of thickbox (class="thickbox")
* Provide a path in the href attribute to an image file (.jpg .jpeg .png .gif .bmp)

    <a href="image1.jpg" title="add a caption to title attribute / or leave blank" class="thickbox"><img src="ithumbnail1.jpg" alt="Single Image"/></a>
    

### Gallery Images

This example is exactly like the single image functionality except that it allows use of the rel attribute to group images together so they can be navigated in a ThickBox. The ideal usage would be for images galleries.

* Create some link elements (<a href>)
* Give the link a class attribute with a value of "thickbox" (class="thickbox")
* Provide a path in the href attribute to an image file (.jpg .jpeg .png .gif .bmp)
* Give each link element the same rel element and value. (Example: rel="gallery-plants")

While you have a ThickBox gallery image open, you can navigate forward and backward through the images by using the left < key (previous) and right > key (next) on the keyboard (Next and Previous links are also provided in the ThickBox). The images will appear in the gallery from first to last as they appear in the HTML document flow.

    <a href="image1.jpg" title="add a caption to title attribute / or leave blank" class="thickbox" rel="gallery-plants"><img src="thumbnail1.jpg" alt="Plant 1" /></a>
    <a href="image2.jpg" title="add a caption to title attribute / or leave blank" class="thickbox" rel="gallery-plants"><img src="thumbnail2.jpg" alt="Plant 1" /></a>
    <a href="image3.jpg" title="add a caption to title attribute / or leave blank" class="thickbox" rel="gallery-plants"><img src="thumbnail3.jpg" alt="Plant 1" /></a>
    <a href="image4.jpg" title="add a caption to title attribute / or leave blank" class="thickbox" rel="gallery-plants"><img src="thumbnail4.jpg" alt="Plant 1" /></a>

### Inline Content

Inline content on the page, either hidden or showing, can be placed in a ThickBox.

* Create a link element (<a href>)
* Give the link a class attribute with a value of thickbox (class="thickbox")
* In the href attribute of the link add the following anchor: #TB_inline
* In the href attribute after the #TB_inline add the following query string on to the anchor: '?height=300&width=300&inlineId=myOnPageContent'
* Change the values of height, width, and inlineId in the query accordingly (inlineID is the ID value of the element that contains the content you would like to show in a ThickBox.
* Optionally you may add modal=true to the query string (e.g. #TB_inline?height=155&width=300&inlineId=hiddenModalContent&modal=true) so that closing a ThickBox will require calling the tb_remove() function from within the ThickBox. See the hidden modal content example, where you must click yes or no to close the ThickBox.

If the inline content in the ThickBox contains more content than the ThickBox dimensions will show, a vertical scroll bar will appear so that the content can be scrolled. You can avoid having the scroll by making sure the ThickBox has the appropriate dimensions in order to show all of the inline content without having to scroll. In other words, if you don't want scroll bars, increase the height and width of the ThickBox until the content does not require scrolling.

    <input alt="#TB_inline?height=300&width=400&inlineId=myOnPageContent" title="add a caption to title attribute / or leave blank" class="thickbox" type="button" value="Show" />
    <a href="#TB_inline?height=155&width=300&inlineId=hiddenModalContent&modal=true" class="thickbox">Show hidden modal content.</a>

### iFramed Content

Opens URL's in an iframe inside of ThickBox. Yes, this is Greybox functionality.

* Create a link element (<a href>)
* Give the link a class attribute with a value of thickbox (class="thickbox")
* In the href attribute of the link provide the URL you would like to display in a ThickBox
* In the href attribute, after the URL, add the following query on to the end of the URL & any parameters you might add: '?KeepThis=true&TB_iframe=true&height=400&width=600'
* Change the values of height and width in the query accordingly
* Optionally you may add modal=true to the query string (e.g. ?KeepThis=true&TB_iframe=true&height=400&width=600&modal=true) so that closing a ThickBox will require calling the tb_remove() function from within the ThickBox iframe (self.parent.tb_remove()). See the iframe demo for an example, where you must click "ok" to close the ThickBox.

Add all other query parameters before the TB_iframe parameters. Everything after the "TB" is removed from the URL.

    <a href="ajax.PHP?keepThis=true&TB_iframe=true&height=250&width=400" title="add a caption to title attribute / or leave blank" class="thickbox">Example 1</a>
    <a href="ajaxOverFlow.htm?keepThis=true&TB_iframe=true&height=300&width=500" title="add a caption to title attribute / or leave blank" class="thickbox">Example 2</a>
    <a href="iframeModal.html?placeValuesBeforeTB_=savedValues&TB_iframe=true&height=200&width=300&modal=true" title="add a caption to title attribute / or leave blank" class="thickbox">Open iFrame Modal</a>

### AJAX Content

Use a hidden HTTP request (AJAX) to fetch files from the same server and have ThickBox display the contents of the files.

* Create a link element (<a href>)
* Give the link a class attribute with a value of thickbox (class="thickbox")
* Provide a path in the href to the file/directory on the server. (href="ajaxLogin.htm")
* In the href attribute, after the URL path to the file, add the following query on to the end of the URL: '?height=300&width=300'
* Change the values of height and width in the query accordingly
* Optionally you may add modal=true to the query string (e.g. ?height=300&width=300&modal=true) so that closing a ThickBox will require calling the tb_remove() function from within the ThickBox. See the login example, where you must click cancel to close the ThickBox.

In order to open new Ajax content in an open Ajax ThickBox, its code must also contain the appropriate HTML (class=""thickbox) to launch an Ajax ThickBox (see demo for example). The only catch is, the ThickBox calls must include both the width and height of the original ThickBox. If you leave it blank the window will resize to the default size(630x440).

    <a href="ajaxOverFlow.html?height=300&width=300" title="add a caption to title attribute / or leave blank" class="thickbox">Scrolling content</a>
    <a href="ajax.PHP?height=220&width=400" class="thickbox" title="add a caption to title attribute / or leave blank">No-scroll content</a>
    <a href="ajaxLogin.html?height=85&width=250&modal=true" class="thickbox" title="Please Sign In">login (modal)</a>
    <a href="ajaxTBcontent.html?height=200&width=300" class="thickbox" title="">Update ThickBox content</a>

## Q & A

### I am using an older version of ThickBox. How do I upgrade?
I suggest stripping out the old CSS and JS and adding back in the new code created for the current version of ThickBox. If that is bad news, then hold tight - I have some good news, too. The way by which ThickBox is invoked has not changed. So, there is no need to change the HTML that invokes a ThickBox.

### Can I display Flash in a ThickBox?
In short, yes! However, I have not personally tested this yet. I have no idea of the browser quirks and support surrounding the usage of Flash in a ThickBox.

### Can a ThickBox appear over the top of my Flash content?
Yes! Have a look here for a full explanation.

### If we use this code for a client, can we donate money to thank you for your efforts?
Yes, simply click on the "Donate" button in the next section to make a PayPal donation.

### Can a ThickBox be opened from another ThickBox?
Sort of, using an Ajax ThickBox you can update the content of the ThickBox. See the Ajax Demo Example.

### Can you view a PDF in a ThickBox?
The short of it is, yes! In fact, anything that can be viewed in a browser can also be viewed in a ThickBox using an iframe. Check out the iframe content example.

## License

http://www.opensource.org/licenses/mit-license.php
http://www.gnu.org/licenses/gpl.html

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so.

## Changelog

The changelog was included for historical purposes. It seems that the project is not longer maintained by the original author.

### As of 08/01/2007
* Added modal functionality to ThickBox iframes
* Fixed Flash transparency issue with Firefox on OSX
* Updated to jQuery 1.1.3.1
* Changed how inline content is handled in Thickbox. Instead of duplicating the inline content thickbox will now move it accordingly inside of the DOM
* Safari iframe source issue solved

### As of 05/02/2007
* If sizes are not set for width and/or height (inline, iframe, and ajax content), ThickBox will default to a width of 630px and a height of 440px
* iframe hack to hide &select" elements now only runs in IE 6
* Scrollbars are removed in IE 6 when a ThickBox is opened (to counter IE 6's errant width and height calculations)
* Cleaned code using JSLint
* A new compressed thickbox.js using Packer
* Updated ThickBox to use jQuery 1.1.2
* Major updates to JavaScript and CSS to address scrolling and overlay issues
* Replaced pre-loader image, and Pre-loader image is now being pre-loaded
* ThickBox now works with image maps ("area" elements) and form buttons ("input" elements), just like links ("a" elements)
* If you use Ajax content, ThickBox will now open new content in the current ThickBox. That is, after the content is loaded into a ThickBox (via Ajax), it will be parsed for any area, link, or input elements with a class of "thickbox". This will allow you to load new content into the current ThickBox
* Added the ability to create a real modal window when using inline or Ajax content

### As of 1/24/2007
* Updated ThickBox to work with jQuery release 1.1.1

### As of 10/11/2006
* Updated jQuery code to release 1.0.2

### As of 10/09/2006
* Fixed scrolling issues with FireFox

### As of 09/23/2006
* Updated jQuery code to release 1.0.1
* The escape key will now close ThickBox
* Removed the necessity to have an extension to use the iframe content and ajax content (image content still requires an extension)
* When opening iframe content with ThickBox the window will only appear after the window has loaded its content (This will not work in Safari)
* Moved the next and previous keyboard functionality for the gallery images to the left < key (previous) and right > key (next). By doing this it fixes a known issue with safari and the arrow keys. This also allows sites design to be scrolled horizontally to use the arrow keys accordingly.
* ThickBox will now work with sites that scroll horizontally. So, a ThickBox, not matter if you scroll a website horizontally or vertically will always show up centered in the window.

### As of 08/07/2006
* Fixed height issue of transparent iframe to hide select elements in IE

### As of 08/03/2006
* Added greybox functionality (iframed content)
* Added titles to ThickBox for iframed, inline, and ajax content
* Added image gallery functions (with keyboard navigation by using the left and right arrow keys)
* New (separate) CSS file specifically for ThickBox
* Fixed Firefox caching issue when loading a ThickBox image for the first time
* Cleaned up and optimized the thickbox.js file
* Add the new file extension .bmp for ThickBox images
* Removed set height on ThickBox so two lines of caption will stretch the window vertically

### As of 07/06/2006
* Added the ability to use inline div elements to populate a ThickBox
* Added the ability to use uppercase and lowercase extensions
* Loading animation centers on the screen regardless of vertical scroll
* In IE, select boxes are now hidden when ThickBox is open
* Fixed a bug that occurs when no title is used on anchor elements
* Fixed overlay so that it covers the screen during the loading animation (occurred in FF and Opera)
* Uses the new jQuery 1.0 â€“ Alpha Release

## Support

ThickBox has received more attention than I had initially expected - so much so that I am a little overwhelmed with the notoriety and somewhat dumbfounded by all the individuals using it. Truthfully, I developed the solution as a proof of concept and personal endeavor to showcase the jQuery library. With that said, I think I might owe some people an apology. ThickBox is not retail software. It has no support or documentation (except for this site). Itâ€™s the start of a great script and should be used as a launching point. If you see its potential, then the script was likely created for you. If, however, you only see the limitations of the solution, then honestly, the script is likely not for you. With that said, I am sorry that I do not have the time to respond to every email/comment requesting support. However, if you send a detailed email of the issue, along with the browser(s) and operating system(s) the issue is occurring in, the chances of getting direct support will increase significantly. In addition to emailing me directory, and the choice for support I would recommend, you can visit and pillaged the ThickBox Forum for peer support.

If past development is any indication, ThickBox will likely morph into another version in the future. If at that point it can stand alone as useful to you, then use it. However, as of today please do not expect a great deal of support for a script that was really never meant to be a complete software solution. Remember, this stuff is free. If it so happens to come wrapped with great documentation and support, then even better, but please don't assume that it should.

## Donate

Knowledge is its own reward. While its true that my own personal enjoyment and education continues to thrive as I develop ThickBox, a little bit of cash for a rainy day never hurt anyone. So, if you're feeling gracious and would like to improve my monetary situation out of gratitude, or maybe because my work on ThickBox has helped you monetarily, you can give me a little cash for all my hard work by clicking on the "PayPal Donate" button below and send me some cha-ching. Of course, this is not necessary, even if you plan on using ThickBox commercially. As I said, knowledge is its own reward.

Please refer to http://codylindley.com/thickbox/ for the proper PayPal donation link.