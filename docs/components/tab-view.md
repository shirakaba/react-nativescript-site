---
id: TabView
title: TabView
---
<!-- contributors: [shirakaba, MisterBrownRSA, rigor789, eddyverbruggen, ikoevska, kharysharpe, ramsesmoreno] -->

`<tabView>` is a navigation component that shows content grouped into tabs and lets users switch between tabs.

See also:

* [Official top-level documentation](https://docs.nativescript.org/ui/components/tab-view)
* [Detailed API specification](https://docs.nativescript.org/api-reference/classes/_ui_tab_view_.tabview)
* [`<tabViewItem>`](/docs/components/tab-view-item)

---

#### Introduction to Node Roles

The TabView component takes TabViewItem components as children. For technical reasons, each TabViewItem child must specify a `nodeRole` property.

More details here: [Node Roles](/docs/core-concepts/node-roles)

#### Basic use

```tsx
import * as React from "react";
import { SelectedIndexChangedEventData } from "tns-core-modules/ui/tab-view/tab-view";

<tabView
  selectedIndex={selectedIndex}
  onSelectedIndexChange={(args: SelectedIndexChangedEventData) => {
    const { oldIndex, newIndex } = args;
    console.log(`Changed from tab index ${oldIndex} -> ${newIndex}.`);
  }}
>
  <tabViewItem nodeRole="items" title="Tab 1">
    <label text="Content for Tab 1" />
  </tabViewItem>
  <tabViewItem nodeRole="items" title="Tab 2">
    <label text="Content for Tab 2" />
  </tabViewItem>
</tabView>
```

**NOTE:** Currently, `TabViewItem` expects a single child element. In most cases, you might want to wrap your content in a layout.

<!-- [> screenshots for=TabView <] -->

#### Adding icons to tabs

```tsx
import * as React from "react";

<tabView selectedIndex={selectedIndex} iosIconRenderingMode="alwaysOriginal">
  <tabViewItem nodeRole="items" title="Tab 1" iconSource="~/images/icon.png">
    <label text="Content for Tab 1" />
  </tabViewItem>
  <tabViewItem nodeRole="items" title="Tab 2" iconSource="~/images/icon.png">
    <label text="Content for Tab 2" />
  </tabViewItem>
</tabView>
```
**NOTE:** You can use images for tab icons instead of icon fonts. For more information about how to control the size of icons, see [Working with image from resource folders](https://docs.nativescript.org/ui/image-resources).

## Props

| Name | Type | Description |
|------|------|-------------|
| `selectedIndex` | `number` | Sets the currently selected tab. Default is `0`.
| `tabTextColor` | [`Color`](https://docs.nativescript.org/api-reference/classes/__nativescript_core_.color) | (Style property) Sets the text color of the tabs titles.
| `tabBackgroundColor` | [`Color`](https://docs.nativescript.org/api-reference/classes/__nativescript_core_.color) | (Style property) Sets the background color of the tabs.
| `selectedTabTextColor` | [`Color`](https://docs.nativescript.org/api-reference/classes/__nativescript_core_.color) | (Style property) Sets the text color of the selected tab title.
| `androidTabsPosition` | `string` | Sets the position of the TabView in Android platform<br/>Valid values: `top` or `bottom`.
| `onSelectedIndexChange`| `(args: `[`SelectedIndexChangedEventData`](https://docs.nativescript.org/api-reference/interfaces/__nativescript_core_.selectedindexchangedeventdata_4)`) => void` | Emitted when an item on the TabView is tapped.

## Native component

| Android | iOS |
|---------|-----|
| [`android.support.v4.view.ViewPager`](https://developer.android.com/reference/android/support/v4/view/ViewPager.html) | [`UITabBarController`](https://developer.apple.com/documentation/uikit/uitabbarcontroller)
