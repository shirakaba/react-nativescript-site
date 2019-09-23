---
id: grid
title: GridLayout
sidebar_label: GridLayout
---
<!-- contributors: [shirakaba, rigor789, ikoevska] -->

`<$GridLayout>` is a React wrapper around `GridLayout`, a layout container that lets you arrange its child elements in a table-like manner (see the official [top-level documentation](https://docs.nativescript.org/ui/layouts/layout-containers#gridlayout) and [detailed API specification](https://docs.nativescript.org/api-reference/modules/_ui_layouts_grid_layout_)).

The grid consists of rows, columns, and cells. A cell can span one or more rows and one or more columns. It can contain multiple child elements which can span over multiple rows and columns, and even overlap each other. 

By default, `<$GridLayout>` has one column and one row. You can add columns and rows by configuring the `columns` and the `rows` properties (which take an array of `ItemSpec` instances to describe their dimensionality).

You can set a fixed size for column width and row height or you can create them in a responsive manner:

* **`"px"`:** Indicates a fixed size.
* **`"auto"`:** Makes the column as wide as its widest child or makes the row as tall as its tallest child.
* **`"star"`:** Takes as much space as available after filling all auto and fixed size columns or rows.

## Examples

### Grid layout with fixed sizing

The following example creates a simple 2-by-2 grid with fixed column widths and row heights.

```tsx
<$GridLayout
  columns={[new ItemSpec(115, "px"), new ItemSpec(115, "px")]}
  rows={[new ItemSpec(115, "px"), new ItemSpec(115, "px")]}
>
  <$Label text="0,0" row={0} col={0} backgroundColor="#43b883"/>
  <$Label text="0,1" row={0} col={1} backgroundColor="#1c6b48"/>
  <$Label text="1,0" row={1} col={0} backgroundColor="#289062"/>
  <$Label text="1,1" row={1} col={1} backgroundColor="#43b883"/>
</$GridLayout>
```
<img class="md:w-1/2 lg:w-1/3" src="https://art.nativescript-vue.org/layouts/grid_layout.svg" />

### Grid layout with star sizing

The following example creates a grid with responsive design, where space is alotted proportionally to child elements.

```tsx
<$GridLayout
  columns={[new ItemSpec(1, "star"), new ItemSpec(2, "star")]}
  rows={[new ItemSpec(2, "star"), new ItemSpec(3, "star")]}
>
  <$Label text="0,0" row={0} col={0} backgroundColor="#43b883"/>
  <$Label text="0,1" row={0} col={1} backgroundColor="#1c6b48"/>
  <$Label text="1,0" row={1} col={0} backgroundColor="#289062"/>
  <$Label text="1,1" row={1} col={1} backgroundColor="#43b883"/>
</$GridLayout>
```
<img class="md:w-1/2 lg:w-1/3" src="https://art.nativescript-vue.org/layouts/grid_layout_star_sizing.svg" />

### Grid layout with fixed and auto sizing

The following example create a grid with one auto-sized column and one column with fixed size. Rows have a fixed height.

```tsx
<$GridLayout
  columns={[new ItemSpec(80, "pixel"), new ItemSpec(1, "auto")]}
  rows={[new ItemSpec(80, "pixel"), new ItemSpec(80, "pixel")]}
>
  <$Label text="0,0" row={0} col={0} backgroundColor="#43b883"/>
  <$Label text="0,1" row={0} col={1} backgroundColor="#1c6b48"/>
  <$Label text="1,0" row={1} col={0} backgroundColor="#289062"/>
  <$Label text="1,1" row={1} col={1} backgroundColor="#43b883"/>
</$GridLayout>
```
<img class="md:w-1/2 lg:w-1/3" src="https://art.nativescript-vue.org/layouts/grid_layout_fixed_auto.svg" />

### Grid layout with mixed sizing and merged cells

The following example creates a complex grid with responsive design, mixed width and height settings, and some merged cells.

```tsx
<$GridLayout
  columns={[new ItemSpec(40, "pixel"), new ItemSpec(1, "auto"), new ItemSpec(1, "star")]}
  rows={[new ItemSpec(40, "pixel"), new ItemSpec(1, "auto"), new ItemSpec(1, "star")]}
  backgroundColor="#3c495e"
>
  <$Label text="0,0" row={0} col={0} backgroundColor="#43b883"/>
  <$Label text="0,1" row={0} col={1} colSpan="2" backgroundColor="#1c6b48"/>
  <$Label text="1,0" row={1} col={0} rowSpan="2" backgroundColor="#289062"/>
  <$Label text="1,1" row={1} col={1} backgroundColor="#43b883"/>
  <$Label text="1,2" row={1} col={2} backgroundColor="#289062"/>
  <$Label text="2,1" row={2} col={1} backgroundColor="#1c6b48"/>
  <$Label text="2,2" row={2} col={2} backgroundColor="#43b883"/>
</$GridLayout>
```
<img class="md:w-1/2 lg:w-1/3" src="https://art.nativescript-vue.org/layouts/grid_layout_complex.svg" />

## Props

| Name | Type | Description |
|------|------|-------------|
`columns` | `String` | A string value representing column widths delimited with commas.<br/>Valid values: an absolute number, `auto`, or `*`.<br/>A number indicates an absolute column width. `auto` makes the column as wide as its widest child. `*` makes the column occupy all available horizontal space. The space is proportionally divided over all star-sized columns. You can set values such as `3*` and `5*` to indicate a ratio of 3:5 in sizes.
`rows` | `String` | A string value representing row heights delimited with commas.<br/>Valid values: an absolute number, `auto`, or `*`.<br/>A number indicates an absolute row height. `auto` makes the row as tall as its tallest child. `*` makes the row occupy all available vertical space. The space is proportionally divided over all star-sized rows. You can set values such as `3*` and `5*` to indicate a ratio of 3:5 in sizes.

## Extra props for child elements

Applies to direct children (not, e.g. grandchildren).

| Name | Type | Description |
|------|------|-------------|
`row` | `number` | Specifies the row for this element. Combined with a `col` property, specifies the cell coordinates of the element.<br/>The first row is indicated by `0`.
`col` | `number` | Specifies the column for the element. Combined with a `row` property, specifies the cell coordinates of the element.<br/>The first column is indicated by `0`.
`rowSpan` | `number` | Specifies the number of rows which this element spans across.
`colSpan` | `number` | Specifies the number of columns which this element spans across.

## React NativeScript-specific props

None for `<$GridLayout>`, nor for any of its children.