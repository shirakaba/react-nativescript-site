---
id: Image
title: Image
---
<!-- contributors: [MisterBrownRSA, rigor789, ikoevska] -->

`<image>` is a UI component that shows an image from an [ImageSource](https://docs.nativescript.org/api-reference/modules/_image_source_) or from a URL.

See also:

* [Official top-level documentation](https://docs.nativescript.org/ui/components/image)
* [Detailed API specification](https://docs.nativescript.org/api-reference/classes/_ui_image_.image)

---

#### Displaying an image relative to the `app` directory

```tsx
import * as React from "react";

<image src="~/logo.png" stretch="none" />
```

#### Displaying an image from a URL

```tsx
import * as React from "react";

<image src="https://art.nativescript-vue.org/NativeScript-Vue-White-Green.png" stretch="none" />
```

#### Displaying an image from `App_Resources`

```tsx
import * as React from "react";

<image src="res://icon" stretch="none" />
```

#### Displaying a `base64`-encoded image

```tsx
import * as React from "react";

<image src="data:Image/png;base64,iVBORw..." stretch="none" />
```

<!-- [> screenshots for=Image <] -->

## Props

| Name | Type | Description |
|------|------|-------------|
| `src` | `string` or [`ImageSource`](https://docs.nativescript.org/api-reference/modules/_image_source_) | Gets or sets the source of the image as a URL or an image source.
|`imageSource` | [`ImageSource`](https://docs.nativescript.org/api-reference/modules/_image_source_) | Gets or sets the image source of the image.
| `tintColor` | [`Color`](https://docs.nativescript.org/api-reference/classes/__nativescript_core_.color) | (Style property) Sets a color to tint template images.
| `stretch` | [`Stretch`](https://docs.nativescript.org/api-reference/modules/__nativescript_core_#stretch) | (Style property) Gets or sets the way the image is resized to fill its allocated space.<br/>Valid values: `none`, `aspectFill`, `aspectFit`, or `fill`.<br/>For more information, see [Stretch](https://docs.nativescript.org/api-reference/modules/_ui_enums_.stretch). 
| `loadMode` | | Gets or sets the loading strategy for the images on the local file system.<br/>Valid values: `sync` or `async`.<br/>Default value: `async`.<br/>For more information, see [loadMode](https://docs.nativescript.org/api-reference/classes/_ui_image_.image#loadmode).

## Native component

| Android | iOS |
|---------|-----|
| [`android.widget.ImageView`](https://developer.android.com/reference/android/widget/ImageView.html) | [`UIImageView`](https://developer.apple.com/documentation/uikit/uiimageview)