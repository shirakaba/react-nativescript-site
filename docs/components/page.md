---
id: Page
title: Page
---
<!-- contributors: [shirakaba, rigor789, ikoevska] -->

`<page>` is a UI component that represents an application screen. NativeScript apps typically consist of one or more `<page>` that wrap content such as an [`<actionBar>`](/docs/components/action-bar) and other UI widgets.

See also:

* [Official top-level documentation](https://docs.nativescript.org/ui/components/page)
* [Detailed API specification](https://docs.nativescript.org/api-reference/classes/_ui_page_.page)

---

### Basic example

```tsx
import * as React from "react";

<page>
  <actionBar title="My App" />
  <gridLayout>
    <label>My Content</label>
  </gridLayout>
</page>
```

#### The special case of the ActionBar child

It doesn't matter whether the `<actionBar>` is a first child, last child, or middle child of `<page>`. React NativeScript will automatically detect it using an `child instanceof Page` check, and set it as the ActionBar for the Page. **Note:** You can skip this check by explicitly setting `<actionBar nodeRole="actionBar">`, but it's not a major performance concern.

Any non-ActionBar child will be handled as the content view. Page only supports a single child, so if you want to insert multiple children on the Page (which is normally the case!), you should use a LayoutBase such as GridLayout to enscapsulate them.

***Out of interest:** You'd expect to be able to set ActionBar as the content view by specifying `<actionBar nodeRole="content">`, but it's not supported in NativeScript Core, so React NativeScript doesn't support it either!*

## Props

| Name | Type | Description |
|------|------|-------------|
| `actionBarHidden` | `boolean` | Shows or hides the `<actionBar>` for the page.<br/>Default value: `false`.
| `backgroundSpanUnderStatusBar` | `boolean` | Gets or sets whether the background of the page spans under the status bar.<br/>Default value: `false`.
| `androidStatusBarBackground` | [`Color`](https://docs.nativescript.org/api-reference/classes/__nativescript_core_.color) | (Android-only) Gets or sets the color of the status bar on Android devices.
| `enableSwipeBackNavigation` | `boolean` | (iOS-only) Gets or sets whether the page can be swiped back on iOS.<br/>Default value: `true`.
| `statusBarStyle` | `string` | Gets or sets the style of the status bar.<br/>Valid values:<br/>`light`,<br/>`dark`.
| `onNavigatedFrom` | `(args: `[`NavigatedData`](https://docs.nativescript.org/api-reference/interfaces/_ui_page_.navigateddata.html)`) => void` | Emitted after the app has navigated away from the current page.
| `onNavigatedTo` | `(args: `[`NavigatedData`](https://docs.nativescript.org/api-reference/interfaces/_ui_page_.navigateddata.html)`) => void` | Emitted after the app has navigated to the current page.
| `onNavigatingFrom` | `(args: `[`NavigatedData`](https://docs.nativescript.org/api-reference/interfaces/_ui_page_.navigateddata.html)`) => void` | Emitted before the app has navigated away from the current page.
| `onNavigatingTo` | `(args: `[`NavigatedData`](https://docs.nativescript.org/api-reference/interfaces/_ui_page_.navigateddata.html)`) => void` | Emitted before the app has navigated to the current page.

## Native component

| Android | iOS |
|---------|-----|
| [`org.nativescript.widgets.GridLayout`](https://github.com/NativeScript/tns-core-modules-widgets/blob/master/android/widgets/src/main/java/org/nativescript/widgets/GridLayout.java) | [`UIViewController`](https://developer.apple.com/documentation/uikit/uiviewcontroller)