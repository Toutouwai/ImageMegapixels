# Image Megapixels

A module for ProcessWire CMS/CMF. Adds a method for Pageimages that resizes to a target megapixel value.

## Example use

You are creating a lightbox gallery. For the enlargements, rather than setting a fixed maximum width or height you want all the enlargements have the same size in terms of area, allowing a panoramic image to be wider than a square image, for instance.

The effect of resizing three different aspect ratios by the same megapixel value can be seen the screenshot below:

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