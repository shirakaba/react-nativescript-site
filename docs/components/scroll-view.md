---
id: ScrollView
title: ScrollView
contributors: [shirakaba, eddyverbruggen, ikoevska, misterbrownza]
---

`<$ScrollView>` is a UI component that shows a scrollable content area. Content can be scrolled vertically or horizontally.

It's important to note that `<$ScrollView>` extends [`ContentView`](https://docs.nativescript.org/api-reference/classes/_ui_content_view_.contentview), so it can only have a single child element.

See also:

* [Official top-level documentation](https://docs.nativescript.org/ui/components/scroll-view)
* [Detailed API specification](https://docs.nativescript.org/api-reference/classes/_ui_scroll_view_.scrollview)
* [ActivityIndicator](/docs/components/activity-indicator)

---

```tsx
<$ScrollView orientation="horizontal">
  <$StackLayout orientation="horizontal">
    <$Label text="this" />
    <$Label text="text" />
    <$Label text="scrolls" />
    <$Label text="horizontally" />
    <$Label text="if necessary" />
  </$StackLayout>
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
