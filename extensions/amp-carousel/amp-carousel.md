<!---
Copyright 2015 The AMP HTML Authors. All Rights Reserved.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

      http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS-IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
-->

# <a name="amp-carousel"></a> `amp-carousel`

<table>
  <tr>
    <td width="40%"><strong>Description</strong></td>
    <td>A generic carousel for displaying multiple similar pieces of content along a horizontal axis; meant to be highly flexible and performant.</td>
  </tr>
  <tr>
    <td width="40%"><strong>Availability</strong></td>
    <td>Stable</td>
  </tr>
  <tr>
    <td width="40%"><strong>Required Script</strong></td>
    <td><code>&lt;script async custom-element="amp-carousel" src="https://cdn.ampproject.org/v0/amp-carousel-0.1.js">&lt;/script></code></td>
  </tr>
  <tr>
    <td width="40%"><strong>Examples</strong></td>
    <td><a href="https://ampbyexample.com/components/amp-carousel">amp-carousel.html</a><br /><a href="https://ampbyexample.com/advanced/image_galleries_with_amp-carousel">image_galleries_with_amp-carousel.html</a></br><a href="https://github.com/ampproject/amphtml/blob/master/examples/everything.amp.html">everything.amp.html</a></td>
  </tr>
</table>

## Behavior

Each of the `amp-carousel` component’s immediate children is considered an item in the carousel. Each of these nodes may also have arbitrary HTML children.

The carousel consists of an arbitrary number of items, as well as optional navigational arrows to go forward or backwards a single item.

The carousel advances between items if the user swipes, uses arrow keys, clicks an optional navigation arrow.
```html
<amp-carousel width=300 height=400>
  <amp-img src="my-img1.png" width=300 height=400></amp-img>
  <amp-img src="my-img2.png" width=300 height=400></amp-img>
  <amp-img src="my-img3.png" width=300 height=400></amp-img>
</amp-carousel>
```

Note, that while the example shows a carousel of images `amp-carousel` support arbitrary children.

## Attributes

**controls**

If present, displays left and right arrows for the user to use in navigation on mobile.
Visibility of arrows can also be controlled via styling, and a media query can be used to
only display arrows at certain screen widths. On desktop, arrows will always be displayed
unless only a single child is present.

**type**
- `carousel` (default) - All slides are shown and are scrollable horizontally.
  Be aware that `type=carousel` does not currently support `layout=responsive`.
- `slides` - Shows a single slide at a time. Supports `layout=responsive`.

**loop** (type=slides only)

If present, the user may advance past the first item or the final item.

**autoplay** (type=slides only)

If present, advances the slide to the next slide without user interaction.
By default it will advance a slide in 5000 millisecond intervals (5 seconds)
and can be overridden by the `delay` attribute.
If `autoplay` is present it will also attach the `loop` attribute to
`amp-carousel` if `loop` is not already present.

**delay** (type=slides only)
By default a slide will advance in 5000 millisecond intervals (5 seconds)
when `autoplay` is specified and will use the value of the `delay`
attribute if present (minimum of 1000 ms, an error will be thrown if its any lower).
The value of `delay` must be numeric representation in milliseconds, ex. `delay=5000`.

## Styling
- You may use the `amp-carousel` element selector to style it freely.
- `.amp-carousel-button` by default uses an inlined svg as the background-image of the buttons.
You may override this with your own svg or image like so:

  **default**

```css
.amp-carousel-button-prev {
  left: 16px;
  background-image: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 18 18"><path d="M15 8.25H5.87l4.19-4.19L9 3 3 9l6 6 1.06-1.06-4.19-4.19H15v-1.5z" fill="#fff" /></svg>');
}
```

  **override**
```css
.amp-carousel-button-prev {
  left: 5%;
  background-image: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 18 18"><path d="M11.56 5.56L10.5 4.5 6 9l4.5 4.5 1.06-1.06L8.12 9z" fill="#fff" /></svg>');
}
```
- By default the visual state of an `amp-carousel` button when it is disabled is that it is hidden.
  You may override this visual state of an `amp-carousel` button in the disabled state by:

```css
.amp-carousel-button.amp-disabled {
  /* make sure we make it visible */
  visibility: visible;
  /* choose our own background styling, red'ish */
  background-color: rgba(255, 0, 0, .5);
}
```
## Validation errors

The following lists validation errors specific to the `amp-carousel` tag
(see also `amp-carousel` in the [AMP validator specification](https://github.com/ampproject/amphtml/blob/master/extensions/amp-carousel/0.1/validator-amp-carousel.protoascii)):

<table>
  <tr>
    <th width="40%"><strong>Validation Error</strong></th>
    <th>Description</th>
  </tr>
  <tr>
    <td width="40%"><a href="https://www.ampproject.org/docs/reference/validation_errors.html#tag-required-by-another-tag-is-missing">The 'example1' tag is missing or incorrect, but required by 'example2'.</a></td>
    <td>Error thrown when required <code>amp-carousel</code> extension <code>.js</code> script tag is missing or incorrect.</td>
  </tr>
  <tr>
    <td width="40%"><a href="https://www.ampproject.org/docs/reference/validation_errors.html#implied-layout-isnt-supported-by-amp-tag">The implied layout 'example1' is not supported by tag 'example2'.</a></td>
    <td>Error thrown when implied layout is set to <code>CONTAINER</code>; this layout type isn't supported.</td>
  </tr>
  <tr>
    <td width="40%"><a href="https://www.ampproject.org/docs/reference/validation_errors.html#specified-layout-isnt-supported-by-amp-tag">The specified layout 'example1' is not supported by tag 'example2'.</a></td>
    <td>Error thrown when specified layout is set to <code>CONTAINER</code>; this layout type isn't supported.</td>
  </tr>
  <tr>
    <td width="40%"><code>Layout not supported for: responsive</code></td>
    <td>Error thrown when layout set to <code>RESPONSIVE</code> and the <code>type</code> attribute is set to (or defaults to) <code>carousel</code>.</td>
  </tr>
</table>
