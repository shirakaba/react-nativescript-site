---
id: ActionBar
title: ActionBar
---
<!-- contributors: [shirakaba, rigor789, eddyverbruggen, ikoevska] -->

`<actionBar>` is a UI component that provides a toolbar at the top of the activity window. 

This component is the NativeScript abstraction for the Android [app bar](https://developer.android.com/training/appbar/) and the iOS [navigation bar](https://developer.apple.com/design/human-interface-guidelines/ios/bars/navigation-bars/).

See also:

* [Official top-level documentation](https://docs.nativescript.org/ui/components/action-bar)
* [Detailed API specification](https://docs.nativescript.org/api-reference/classes/_ui_action_bar_.actionbar)
* [`<$ActionItem>`](/docs/components/action-item)
* [`<$NavigationButton>`](/docs/components/navigation-button)

---

#### Using a title

```tsx
import * as React from "react";

<actionBar title="MyApp" />
```

#### Using a custom title view

```tsx
import * as React from "react";

<actionBar>
  <stackLayout orientation="horizontal">
    <image src="res://icon" width={40} height={40} verticalAlignment="center" />
    <label text="NativeScript" fontSize={24} verticalAlignment="center" />
  </stackLayout>
</actionBar>
```

<!-- TODO: check whether android.*attributes are strictly settable only on ActionItem as I had previously thought. -->

<!-- #### Setting an app icon for Android

```tsx
<actionBar title="My App" android.icon="res://icon" android.iconVisibility="always" />
``` -->

#### Removing the border

By default, a border is drawn at the bottom of the `<actionBar>`. In addition to the border, on iOS devices a translucency filter is also applied over the `<actionBar>`.

To remove this styling from your app, you can set the `flat` property to `true`.

```tsx
import * as React from "react";

<actionBar title="My App" flat={true} />
```

## Props

| Name | Type | Description |
|------|------|-------------|
| `title` | `string` | Sets the title shown in the bar.
| `flat` | `boolean` | Removes the border on Android and the translucency on iOS. Default value is `false`.

<!-- | `android.icon` | `string` | Sets the icon to be shown on Android devices. -->
<!-- | `android.iconVisibility` | `string` | Sets icon visibility on Android devices. -->

## Native component

| Android | iOS |
|---------|-----|
| [`android.widget.Toolbar`](https://developer.android.com/reference/android/widget/Toolbar.html)   | [`UINavigationBar`](https://developer.apple.com/documentation/uikit/uinavigationbar)