---
id: ScrollView
title: ScrollView
---
<!-- contributors: [shirakaba, eddyverbruggen, ikoevska, misterbrownza] -->

`<scrollView>` is a UI component that shows a scrollable content area. Content can be scrolled vertically or horizontally.

It's important to note that `<scrollView>` extends [`ContentView`](https://docs.nativescript.org/api-reference/classes/_ui_content_view_.contentview), so it can only have a single child element.

See also:

* [Official top-level documentation](https://docs.nativescript.org/ui/components/scroll-view)
* [Detailed API specification](https://docs.nativescript.org/api-reference/classes/_ui_scroll_view_.scrollview)
* [`<activityIndicator>`](/docs/components/activity-indicator)

---

```tsx
import * as React from "react";

<scrollView orientation="horizontal">
  <stackLayout orientation="horizontal">
    <label text="this" />
    <label text="text" />
    <label text="scrolls" />
    <label text="horizontally" />
    <label text="if necessary" />
  </stackLayout>
</ScrollView>
```

<!-- [> screenshots for=ScrollView <] -->

## Props

| name | type | description |
|------|------|-------------|
| `orientation` | `string` | Sets the direction in which the content can be scrolled: `horizontal` or `vertical`.<br/>Default value: `vertical`.
| `scrollBarIndicatorVisible` | `boolean` | Specifies if the scrollbar is visible.<br/>Default value: `true`.
| `onScroll` | `(args: `[`ScrollEventData`](https://docs.nativescript.org/api-reference/interfaces/_ui_scroll_view_.scrolleventdata)`) => void` | Emitted when a scroll event occurs.

## Native component

| Android | iOS |
|---------|-----|
| [`android.view`](https://developer.android.com/reference/android/view/View.html) | [`UIScrollView`](https://developer.apple.com/documentation/uikit/uiscrollview)
