---
id: NavigationButton
title: NavigationButton
---
<!-- contributors: [shirakaba, rigor789, ikoevska] -->

`<navigationButton>` is a UI component that provides an abstraction for the Android navigation button and the iOS back button.

Extends [`<actionItem>`](/docs/components/action-item).

See also:

* [Official top-level documentation](https://docs.nativescript.org/ui/components/action-bar#navigationbutton)
* [Detailed API specification](https://docs.nativescript.org/api-reference/classes/_ui_action_bar_.navigationbutton)
* [`<actionBar>`](/docs/components/action-bar)
* [`<actionItem>`](/docs/components/action-item)

---

```tsx
import * as React from "react";

<actionBar title="My App">
  <navigationButton
    text="Go back"
    android={{
      systemIcon: "ic_menu_back"
    }}
    onTap={goBack}
  />
</actionBar>
```

## Props

| Name | Type | Description |
|------|------|-------------|
| `text` | `string` | (iOS-only) Sets the text of the button.
| `android.systemIcon` | `string` | (Android-only) The icon to be shown in the button. You can specify any system icon whose name begins with the `ic_` prefix. For a complete list of the available icons, see [the `R.drawable` Android class](https://developer.android.com/reference/android/R.drawable.html).
| `onTap` | `(args: `[`EventData`](https://docs.nativescript.org/api-reference/interfaces/__nativescript_core_.eventdata)`) => void` | Emitted when the `NavigationButton` is tapped.

## Native component

| Android | iOS |
|---------|-----|
| [`android.widget.Toolbar`](https://developer.android.com/reference/android/widget/Toolbar.html) | [`UINavigationItem`](https://developer.apple.com/documentation/uikit/uinavigationitem)