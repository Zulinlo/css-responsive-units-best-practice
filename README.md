# CSS measurement units
## Relative units
Relative units scale relatively to other length properties.

| Unit | Description |
| ---- | ----------- |
| % | **Percentage:** relative to parent element |
| rem | **Root element's font-size:** relative to font-size of root element |
| em | **Font-size:** relative to font-size of parent element |
| ch | **Cap height:** sets font-size relative to the width of '0' |
| vw | **Viewport width:** relative to 1% of the width of the viewport |
| vh | **Viewport height:** relative to 1% of the height of the viewport |

## Absolute units
Absolute units are fixed lengths and must be used with caution for screens as their sizes vary greatly.

| Unit | Description |
| ---- | ----------- |
| cm | **Centimeter:** only a perfect centimeter if screen's resolution is high enough |
| mm | **Millimeter:** only a perfect millimeter if screen's resolution is high enough |
| in | **Inch:** 2.56cm and only a perfect inch if screen's resolution is high enough |
| px | **Pixel:** 1/96 of 1in |
| pt | **Point:** 1/72 of 1in |
| pc | **Pica:** 12pt|

# When to use what units
## HTML / Media queries
It is gnerally best practice to develop for a mobile screen size first and then adjust for larger screens whether it be through media queries breakpoints or other adjustments, although setting the root element's font-size can help with this transformation.

The root element(html)'s default font-size is generally set to ```16px``` however this differs per device as it can be customally altered (short-sighted people may increase this default property). Thus, it is important when adjusting the root's font-size to use ```%```.

As screen sizes differ, most commonly between phones, tablets and laptop screens it is prefferable to adjust the root element's font-size accordingly using media queries as shown below for responsive font sizes using ```rem```.

``` css
/* Small devices: Phones */
@media only screen and (min-width: 100px) {
  html {
    font-size: 75%;
  }
}

/* Medium devices: Laptops, tablets */
@media only screen and (min-width: 768px) {
  html {
    font-size: 100%;
  }
}

/* Large devices: TVs, large monitors */
@media only screen and (min-width: 1200px) {
  html {
    font-size: 125%;
  }
}
```

## Font-size
Font-size should only be applied to lowest-level children to avoid a cascading effect on relative units. It is recommended to use a combination of ```rem``` and ```em```.

``` css
.parent {
  font-size: 1rem;
}

.child {
  font-size: 0.5em;
}
```

## Border
Recommended to use ```px``` as borders do not generally need to scale.

``` css
.component {
  border: 1px solid black;
}
```

## Padding and margin
Recommended to use ```rem``` for both padding and margin.

``` css
.component {
  margin: 0 1rem;
  padding: 1rem;
}
```

## Images
Recommended to use relative units such as ```vw```, ```vh``` and ```%``` as a large image will overflow the screen of a mobile device and thus it is crucial to scale images.

``` css
.image {
  width: 100%
}
```
