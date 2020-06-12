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
* [`<actionItem>`](/docs/components/action-item)
* [`<navigationButton>`](/docs/components/navigation-button)

---

#### Introduction to Node Roles

ActionBars are a complex component that can contain child components serving different roles (e.g. navigation button, title view, or action item). React NativeScript provides a `nodeRole` property so that you can make it explicit what role each given child serves.

Take care not to miss the `nodeRole` property that we set in the following examples, to see which children (and grandchildren) require which roles.

See: [Node Roles](/docs/core-concepts/node-roles)

#### Using a title

```tsx
import * as React from "react";

<actionBar title="MyApp" />
```

#### Using a custom title view

```tsx
import * as React from "react";

<actionBar>
  <stackLayout nodeRole={"titleView"} orientation="horizontal">
    <image src="res://icon" width={40} height={40} verticalAlignment="center" />
    <label text="NativeScript" fontSize={24} verticalAlignment="center" />
  </stackLayout>
</actionBar>
```

#### Removing the border

By default, a border is drawn at the bottom of the `<actionBar>`. In addition to the border, on iOS devices a translucency filter is also applied over the `<actionBar>`.

To remove this styling from your app, you can set the `flat` property to `true`.

```tsx
import * as React from "react";

<actionBar title="My App" flat={true} />
```

#### Adding buttons


```tsx
import * as React from "react";

<actionBar>
  <label nodeRole={"titleView"}>Hello Title View</label>
  <actionItem nodeRole={"actionItems"}>
    <button nodeRole={"actionView"}>One</button>
  </actionItem>
  <actionItem nodeRole={"actionItems"}>
    <button nodeRole={"actionView"}>Two</button>
  </actionItem>
  <actionItem nodeRole={"actionItems"}>
    <button nodeRole={"actionView"}>Three</button>
  </actionItem>
</actionBar>
```

#### Setting an app icon for Android

```tsx
import * as React from "react";

<actionBar title="My App" android={{ icon: "res://icon", iconVisibility: "always" }} />
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