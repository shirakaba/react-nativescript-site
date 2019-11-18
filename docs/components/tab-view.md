---
id: TabView
title: TabView
---
<!-- contributors: [shirakaba, MisterBrownRSA, rigor789, eddyverbruggen, ikoevska, kharysharpe, ramsesmoreno] -->

`<$TabView>` is a navigation component that shows content grouped into tabs and lets users switch between tabs.

See also:

* [Official top-level documentation](https://docs.nativescript.org/ui/components/tab-view)
* [Detailed API specification](https://docs.nativescript.org/api-reference/classes/_ui_tab_view_.tabview)
* [`<$TabViewItem>`](/docs/components/tab-view-item)

---

<!-- TODO: show how to import SelectedIndexChangedEventData_4 from scoped modules -->

```tsx
import { SelectedIndexChangedEventData } from "tns-core-modules/ui/tab-view/tab-view";

<$TabView
  selectedIndex={selectedIndex}
  onSelectedIndexChange={(args: SelectedIndexChangedEventData) => {
    const { oldIndex, newIndex } = args;
    console.log(`Changed from tab index ${oldIndex} -> ${newIndex}.`);
  }}
>
  <$TabViewItem title="Tab 1">
    <$Label text="Content for Tab 1" />
  </$TabViewItem>
  <$TabViewItem title="Tab 2">
    <$Label text="Content for Tab 2" />
  </$TabViewItem>
</$TabView>
```

**NOTE:** Currently, `TabViewItem` expects a single child element. In most cases, you might want to wrap your content in a layout.

<!-- [> screenshots for=TabView <] -->

#### Adding icons to tabs

```tsx
<$TabView selectedIndex={selectedIndex} iosIconRenderingMode="alwaysOriginal">
  <$TabViewItem title="Tab 1" iconSource="~/images/icon.png">
    <$Label text="Content for Tab 1" />
  </$TabViewItem>
  <$TabViewItem title="Tab 2" iconSource="~/images/icon.png">
    <$Label text="Content for Tab 2" />
  </$TabViewItem>
</$TabView>
```
**NOTE:** You can use images for tab icons instead of icon fonts. For more information about how to control the size of icons, see [Working with image from resource folders](https://docs.nativescript.org/ui/image-resources).

## Props

| Name | Type | Description |
|------|------|-------------|
| `selectedIndex` | `Number` | Gets or sets the currently selected tab. Default is `0`.
| `tabTextColor` | `Color` | (Style property) Gets or sets the text color of the tabs titles.
| `tabBackgroundColor` | `Color` | (Style property) Gets or sets the background color of the tabs.
| `selectedTabTextColor` | `Color` | (Style property) Gets or sets the text color of the selected tab title.
| `androidTabsPosition` | `String` | Sets the position of the TabView in Android platform<br/>Valid values: `top` or `bottom`.
| `onSelectedIndexChange`| `(args: `[`SelectedIndexChangedEventData`](https://docs.nativescript.org/api-reference/interfaces/__nativescript_core_.selectedindexchangedeventdata_4)`) => void` | Emitted when an item on the TabView is tapped.

## Native component

| Android | iOS |
|---------|-----|
| [`android.support.v4.view.ViewPager`](https://developer.android.com/reference/android/support/v4/view/ViewPager.html) | [`UITabBarController`](https://developer.apple.com/documentation/uikit/uitabbarcontroller)
