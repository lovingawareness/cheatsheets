# macOS Cheatsheet

* `sips -g pixelWidth -g pixelHeight image.jpg` - Get image dimensions.
* `sips -s format jpeg image.png --out image.jpg` - Convert an image from PNG to JPG.
* `sips -Z 500 image.jpg --out image2.jpg` - Resize an image so its largest dimension is 500 pixels.
* `sips -c 400 500 image.jpg --out image2.jpg` - Crop an image so it's 500 pixels wide and 400 pixels tall.
* `sips --padToHeightWidth 400 500 --padColor FFFFFF image.jpg --out image2.jpg` - Pad an image so it's 500 pixels wide and 400 pixels tall, padding with white.
* `mkdir output; for i in *.jpg; do sips -Z 750 $i --out output/$i.jpg; done` - Make changes to all files in a folder.
* `convert source.jpg -splice 0x100 out.jpg` - To pad an image just on the top with 100 pixels of white space, using imagemagick.
