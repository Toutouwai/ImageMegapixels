# Image Megapixels

A module for ProcessWire CMS/CMF. Adds a method for Pageimages that resizes to a target megapixel value.

## Example use

You are creating a lightbox gallery of images with different aspect ratios. For the enlargements, rather than setting a fixed maximum width or height you want all the enlargements have the same size in terms of area, allowing a panoramic image to be wider than a square image, for instance.

The effect of resizing three different aspect ratios by the same megapixel target value can be seen in the screenshot below:

![megapixels](https://user-images.githubusercontent.com/1538852/35495012-749cb392-0523-11e8-81d1-4a8beb68eaf3.jpg)

## Installation

[Install](http://modules.processwire.com/install-uninstall/) the Image Megapixels module.

## API

```php
// basic usage
$pageimage = $pageimage->megapixels(float $megapixels);

// usage with all arguments
$pageimage = $pageimage->megapixels(float $megapixels, array $options = []);
```

Example:

```php
foreach($page->images as $image) {
    echo "<img src='$image->megapixels(0.8)->url' alt='$image->description'>"
}
```

If needed you can supply an array of [options for Pageimage::size()](https://processwire.com/api/ref/page-image/size/) as a second argument.

### Getting dimensions

If you just want to get the height and width dimensions needed to size an image to the given number of megapixels you can use the `Pageimage::megapixelsDimensions()` method that this module also adds. It returns an array with `width` and `height` as keys.

Example of how this could be used to output a gallery of logos:

```php
foreach($page->logos as $logo) {
    $dimensions = $logo->megapixelsDimensions(0.01);
    $width = $dimensions['width'];
    $height = $dimensions['height'];
    $width2x = $width * 2;
    $height2x = $height * 2;
    echo "<img src='{$logo->size($width, $height)->url}' srcset='{$logo->size($width, $height)->url} 1x, {$logo->size($width2x, $height2x)->url} 2x' alt='Logo' width='$width' height='$height'>";
}
```
