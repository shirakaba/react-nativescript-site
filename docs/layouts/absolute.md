---
id: absolute
title: AbsoluteLayout
sidebar_label: AbsoluteLayout
---
<!-- contributors: [shirakaba, rigor789, ikoevska] -->

`<absoluteLayout>` is a React wrapper around `AbsoluteLayout`, the simplest layout container in NativeScript.

`<absoluteLayout>` has the following behaviour:

* Uses a pair of absolute left/top coordinates to position its children.
* Doesn't enforce any layout constraints on its children.
* Doesn't resize its children at runtime when its size changes.

See also:

* [Official top-level documentation](https://docs.nativescript.org/ui/layouts/layout-containers#absolutelayout)
* [Detailed API specification](https://docs.nativescript.org/api-reference/modules/_ui_layouts_absolute_layout_)

## Examples

### A grid-like layout

The following example creates a simple grid. For more information about creating grid layouts, see [GridLayout](/en/docs/elements/layouts/grid-layout).

```tsx
import * as React from "react";

<absoluteLayout backgroundColor="#3c495e">
  <label text="10,10" left={10} top={10} width={100} height={100} backgroundColor="#43b883"/>
  <label text="120,10" left={120} top={10} width={100} height={100} backgroundColor="#43b883"/>
  <label text="10,120" left={10} top={120} width={100} height={100} backgroundColor="#43b883"/>
  <label text="120,120" left={120} top={120} width={100} height={100} backgroundColor="#43b883"/>
</absoluteLayout>
```
<img class="md:w-1/2 lg:w-1/3" src="https://art.nativescript-vue.org/layouts/absolute_layout_grid.svg" />

*Licence: [NativeScript Vue Artwork](/docs/licences/licences#Nativescript_Vue_Artwork).*

### Overlapping elements

The following example creates a group of overlapping items.

```tsx
import * as React from "react";

<absoluteLayout backgroundColor="#3c495e">
  <label text="10,10" left={10} top={10} width={100} height={100} backgroundColor="#289062"/>
  <label text="30,40" left={30} top={40} width={100} height={100} backgroundColor="#43b883"/>
</absoluteLayout>
```
<img class="md:w-1/2 lg:w-1/3" src="https://art.nativescript-vue.org/layouts/absolute_layout_overlap.svg" />

*Licence: [NativeScript Vue Artwork](/docs/licences/licences#Nativescript_Vue_Artwork).*

## Extra props for child elements

None.

## React NativeScript-specific props

None for `<absoluteLayout>`, nor for any of its children.
