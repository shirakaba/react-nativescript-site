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

```tsx
import * as React from "react";

<page>
  <actionBar title="My App" />
  <gridLayout>
    <label>My Content</label>
  </gridLayout>
</page>
```

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