---
id: wrap
title: WrapLayout
sidebar_label: WrapLayout
---
<!-- contributors: [shirakaba, rigor789, ikoevska] -->

`<$WrapLayout>` is a React wrapper around `WrapLayout`, a layout container that lets you position items in rows or columns, based on the orientation property. When the space is filled, the container automatically wraps items onto a new row or column.

See also:

* [Official top-level documentation](https://docs.nativescript.org/ui/layouts/layout-containers#wraplayout)
* [Detailed API specification](https://docs.nativescript.org/api-reference/modules/_ui_layouts_wrap_layout_)

## Examples

### Default wrap layout

The following example creates a row of equally-sized items. When the row runs out of space, the container wraps the last item on a new row.

```tsx
import * as React from "react";
import { $WrapLayout, $Label } from "react-nativescript";

<$WrapLayout backgroundColor="#3c495e">
  <$Label
    text="first"
    width={{ value: 30, unit: "%" }}
    height={{ value: 30, unit: "%" }}
    backgroundColor="#43b883"}
  />
  <$Label
    text="second"
    width={{ value: 30, unit: "%" }}
    height={{ value: 30, unit: "%" }}
    backgroundColor="#1c6b48"}
  />
  <$Label
    text="third"
    width={{ value: 30, unit: "%" }}
    height={{ value: 30, unit: "%" }}
    backgroundColor="#289062"}
  />
  <$Label
    text="fourth"
    width={{ value: 30, unit: "%" }}
    height={{ value: 30, unit: "%" }}
    backgroundColor="#289062"}
  />
</$WrapLayout>
```

<img class="md:w-1/2 lg:w-1/3" src="https://art.nativescript-vue.org/layouts/wrap_layout_horizontal.svg" />

### Vertical wrap layout

The following example creates a column of equally-sized items. When the row runs out of space, the container wraps the last item on a new column.

```tsx
import * as React from "react";
import { $WrapLayout, $Label } from "react-nativescript";

<$WrapLayout orientation="vertical" backgroundColor="#3c495e">
  <$Label
    text="first"
    width={{ value: 30, unit: "%" }}
    height={{ value: 30, unit: "%" }}
    backgroundColor="#43b883"}
  />
  <$Label
    text="second"
    width={{ value: 30, unit: "%" }}
    height={{ value: 30, unit: "%" }}
    backgroundColor="#1c6b48"}
  />
  <$Label
    text="third"
    width={{ value: 30, unit: "%" }}
    height={{ value: 30, unit: "%" }}
    backgroundColor="#289062"}
  />
  <$Label
    text="fourth"
    width={{ value: 30, unit: "%" }}
    height={{ value: 30, unit: "%" }}
    backgroundColor="#289062"}
  />
</$WrapLayout>
```

<img class="md:w-1/2 lg:w-1/3" src="https://art.nativescript-vue.org/layouts/wrap_layout_vertical.svg" />

## Props

| Name | Type | Description |
|------|------|-------------|
`orientation` | `string` | Specifies the stacking direction.<br/>Valid values: `horizontal` (arranges items in rows) and `vertical` (arranges items in columns).<br/>Default value: `horizontal`.
`itemWidth` | `number` | Sets the width used to measure and layout each child.<br/>Default value: `Number.NaN`, which does not restrict children.
`itemHeight` | `number` | Sets the height used to measure and layout each child.<br/>Default value is `Number.NaN`, which does not restrict children.

## Extra props for child elements

None.

## React NativeScript-specific props

None for `<$WrapLayout>`, nor for any of its children.