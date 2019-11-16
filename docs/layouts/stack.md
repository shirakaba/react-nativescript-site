---
id: stack
title: StackLayout
sidebar_label: StackLayout
---
<!-- contributors: [shirakaba, rigor789, ikoevska] -->

`<$StackLayout>` is a React wrapper around `StackLayout`, a layout container that lets you stack the child elements vertically (default) or horizontally.

See also:

* [Official top-level documentation](https://docs.nativescript.org/ui/layouts/layout-containers#stacklayout)
* [Detailed API specification](https://docs.nativescript.org/api-reference/modules/_ui_layouts_stack_layout_)

## Examples

### Default stacking

The following example creates a vertical stack of 3 equally-sized elements. Items are stretched to cover the entire width of the screen. Items are placed in the order they were declared in.

```tsx
<$StackLayout backgroundColor={new Color("#3c495e")}>
  <$Label text="first" height={70} backgroundColor={new Color("#43b883")}/>
  <$Label text="second" height={70} backgroundColor={new Color("#289062")}/>
  <$Label text="third" height={70} backgroundColor={new Color("#1c6b48")}/>
</$StackLayout>
```
<img class="md:w-1/2 lg:w-1/3" src="https://art.nativescript-vue.org/layouts/stack_layout_vertical.svg" />

### Horizontal stacking

The following example creates a horizontal stack of 3 equally-sized elements. Items are stretched to cover the entire height of the screen. Items are placed in the order they were declared in.

```tsx
<$StackLayout orientation="horizontal" backgroundColor={new Color("#3c495e")}>
  <$Label text="first" width={70} backgroundColor={new Color("#43b883")}/>
  <$Label text="second" width={70} backgroundColor={new Color("#289062")}/>
  <$Label text="third" width={70} backgroundColor={new Color("#1c6b48")}/>
</$StackLayout>
```
<img class="md:w-1/2 lg:w-1/3" src="https://art.nativescript-vue.org/layouts/stack_layout_horizontal.svg" />

### Stack layout with horizontally aligned children

The following example creates a diagonal stack of items with responsive sizes. Items are vertically stacked.

```tsx
<$StackLayout backgroundColor={new Color("#3c495e")}>
  <$Label
    text="left"
    horizontalAlignment="left"
    width={33}
    height={70}
    backgroundColor={new Color("#43b883")}
  />
  <$Label
    text="center"
    horizontalAlignment="center"
    width={33}
    height={70}
    backgroundColor={new Color("#289062")}
  />
  <$Label
    text="right"
    horizontalAlignment="right"
    width={33}
    height={70}
    backgroundColor={new Color("#1c6b48")}
  />
  <$Label
    text="stretch"
    horizontalAlignment="stretch"
    height={70}
    backgroundColor={new Color("#43b883")}
  />
</$StackLayout>
```
<img class="md:w-1/2 lg:w-1/3" src="https://art.nativescript-vue.org/layouts/stack_layout_vertical_align_children.svg" />

### Horizontal stack layout with vertically aligned children

The following example creates a diagonal stack of items with responsive sizes. Items are horizontally stacked.

```tsx
<$StackLayout orientation="horizontal" backgroundColor={new Color("#3c495e")}>
  <$Label
    text="top"
    verticalAlignment="top"
    width={70}
    height={33}
    backgroundColor={new Color("#43b883")}
  />
  <$Label
    text="center"
    verticalAlignment="center"
    width={70}
    height={33}
    backgroundColor={new Color("#289062")}
  />
  <$Label
    text="bottom"
    verticalAlignment="bottom"
    width={70}
    height={33}
    backgroundColor={new Color("#1c6b48")}
  />
  <$Label
    text="stretch"
    verticalAlignment="stretch"
    width={70}
    backgroundColor={new Color("#43b883")}/>
</$StackLayout>
```
<img class="md:w-1/2 lg:w-1/3" src="https://art.nativescript-vue.org/layouts/stack_layout_horizontal_align_children.svg" />

## Props

| Name | Type | Description |
|------|------|-------------|
`orientation` | `string` | Specifies the stacking direction.<br/>Valid values: `vertical` and `horizontal`.<br/>Default value: `vertical`.

## Extra props for child elements

None.

## React NativeScript-specific props

None for `<$StackLayout>`, nor for any of its children.