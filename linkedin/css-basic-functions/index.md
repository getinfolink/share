# __css basic functions__
## 1. __Color Functions__
<mark>rgb()</mark> and rgba(): Specify colors using red, green, and blue values, with optional alpha for transparency.

```css
    color: rgb(255, 0, 0);      /* Red color */
    color: rgba(255, 0, 0, 0.5); /* Red with 50% opacity */
    hsl() and hsla(): Define colors using hue, saturation, and lightness, with optional alpha.
```


```css
  color: hsl(120, 100%, 50%);      /* Bright green */
  color: hsla(120, 100%, 50%, 0.3); /* Bright green with 30% opacity */
```
<div style="page-break-after: always;"></div>

## 2. __Math Functions__
calc(): Perform basic calculations for dynamic sizes, margins, or positions.


```css
  width: calc(100% - 50px); /* Width that subtracts 50px from 100% */
  margin-top: calc(1rem + 10px);
```
min(), max(), and clamp():

min(): Chooses the smallest value.
max(): Chooses the largest value.
clamp(): Sets a value with a minimum and maximum range.

```css
  width: min(100%, 500px); /* Max width of 500px, but not more than 100% */
  font-size: clamp(1rem, 2vw, 2rem); /* Responsive font size between 1rem and 2rem */
```
<div style="page-break-after: always;"></div>

## 3. String Functions
attr(): Inserts attribute values directly into CSS, mainly for content.

```css
  content: attr(data-label); /* Useful for custom data attributes */
```
<div style="page-break-after: always;"></div>

## 4. Shape Functions
circle(), ellipse(), polygon(): Used with clip-path to create complex shapes.

```css
  clip-path: circle(50%); /* Circular clipping */
  clip-path: polygon(50% 0%, 100% 100%, 0% 100%); /* Triangle shape */
```
<div style="page-break-after: always;"></div>

## 5. Transform Functions
rotate(), scale(), translate(), skew(): Modify element position, size, and rotation.

```css
  transform: rotate(45deg);     /* Rotates element by 45 degrees */
  transform: scale(1.5);        /* Scales element to 150% size */
  transform: translate(10px, 20px); /* Moves element 10px right and 20px down */
```
<div style="page-break-after: always;"></div>

## 6. Gradient Functions
linear-gradient(), radial-gradient(), conic-gradient(): Create color gradients for backgrounds.

```css
  background: linear-gradient(to right, red, yellow);
  background: radial-gradient(circle, red, blue);
  background: conic-gradient(from 0deg, red, yellow, green);
```
<div style="page-break-after: always;"></div>

## 7. Filter Functions
blur(), brightness(), contrast(), grayscale(), hue-rotate(), invert(), opacity(), saturate(), sepia(): Apply visual effects.

```css
  filter: blur(5px);              /* Blurs the image by 5px */
  filter: brightness(1.2);        /* Increases brightness by 20% */
  filter: grayscale(100%);        /* Converts image to grayscale */
```
These functions are powerful tools in CSS that enable complex and dynamic styling, from adjusting colors and sizes to transforming and filtering elements.


<div style="page-break-after: always;"></div>

![](../../assets/ads/img-001.png)

