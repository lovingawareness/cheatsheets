# macOS Cheatsheet

## OS Shortcuts

* **Shift-Command (⌘)-3** - Take a screenshot of the entire screen, find the .PNG on your desktop.
* **Shift-Command (⌘)-4** - Take a screenshot of a portion of the screen, find the .PNG on your desktop.
* **Shift-Command (⌘)-4, Spacebar** - Take a screenshot of a window, cursor changes to a camera after pressing Spacebar, click on the window you want to screenshot, find the .PNG on your desktop.
* **Control-Command (⌘)-Q** - Lock screen

## CLI Image Processing

* `sips -g pixelWidth -g pixelHeight image.jpg` - Get image dimensions.
* `sips -s format jpeg image.png --out image.jpg` - Convert an image from PNG to JPG.
* `sips -Z 500 image.jpg --out image2.jpg` - Resize an image so its largest dimension is 500 pixels.
* `sips -c 400 500 image.jpg --out image2.jpg` - Crop an image so it's 500 pixels wide and 400 pixels tall.
* `sips --padToHeightWidth 400 500 --padColor FFFFFF image.jpg --out image2.jpg` - Pad an image so it's 500 pixels wide and 400 pixels tall, padding with white.
* `mkdir output; for i in *.jpg; do sips -Z 750 $i --out output/$i.jpg; done` - Make changes to all files in a folder.
* `convert source.jpg -splice 0x100 out.jpg` - To pad an image just on the top with 100 pixels of white space, using imagemagick.

## Sources

* [How to take Screenshots in macOS](https://support.apple.com/en-us/HT201361)
* [macOS Keyboard Shortcuts](https://support.apple.com/en-us/HT201236)
