---
id: ActionItem
title: ActionItem
---
<!-- contributors: [shirakaba, rigor789, ikoevska] -->

`<actionItem>` is a UI component that lets you add action buttons to the `<actionBar>` component.

See also:

* [Official top-level documentation](https://docs.nativescript.org/ui/components/action-bar#actionitem)
* [Detailed API specification](https://docs.nativescript.org/api-reference/classes/_ui_action_bar_.actionitem)
* [`<actionBar>`](/docs/components/action-bar)
* [`<navigationButton>`](/docs/components/navigation-button)

---

#### Introduction to Node Roles

An ActionItem is a child of the ActionBar, which is a complex component that can contain child components serving different roles (e.g. navigation button, title view, or action item). React NativeScript provides a `nodeRole` property so that you can make it explicit what role each given child serves.

Take care not to miss the `nodeRole` property that we set in the following examples, to see which children (and grandchildren) require which roles.

See: [Node Roles](/docs/core-concepts/node-roles)


#### Basic use

```tsx
import * as React from "react";

<actionBar title="My App">
  <actionItem
    nodeRole={"actionItems"}
    onTap={onTapShare}
    ios={{
      systemIcon: 9,
      position: "left" as const
    }}
    android={{
      systemIcon: "ic_menu_share" as const,
      position: "actionBar" as const
    }}
  />
  <actionItem
    nodeRole={"actionItems"}
    onTap={onTapDelete}
    ios={{
      systemIcon: 16,
      position: "right" as const
    }}
    android={{
      position: "popup" as const
    }}
    text="delete"
  />
</actionBar>
```

#### Using custom icons as well as platform-specific positioning

Specify the `systemIcon` as `undefined`. I know, it's weird; it's behaviour that's inherited from NativeScript Core.

```tsx
import * as React from "react";

<actionBar title="My App">
  <actionItem
    nodeRole={"actionItems"}
    onTap={onTapShare}
    ios={{
      systemIcon: undefined,
      position: "left" as const
    }}
    android={{
      systemIcon: undefined,
      position: "actionBar" as const
    }}
  />
  <actionItem
    nodeRole={"actionItems"}
    onTap={onTapDelete}
    ios={{
      systemIcon: undefined,
      position: "right" as const
    }}
    android={{
      systemIcon: undefined,
      position: "popup" as const
    }}
    text="delete"
  />
</actionBar>
```

#### Conditionally showing action items

You can use the `visibility` prop (inherited from `View`) to show `<actionItem>` components based on a condition.

```tsx
import * as React from "react";

<actionBar title="My App">
  <actionItem
    nodeRole={"actionItems"}
    onTap={onTapEdit}
    visibility={isEditing ? "hidden" : "visible"}
    ios={{
      systemIcon: 2,
      position: "right" as const
    }}
    android={{
      systemIcon: "ic_menu_edit"
    }}
  />
  <actionItem
    nodeRole={"actionItems"}
    onTap={onTapSave}
    visibility={isEditing ? "visible" : "hidden"}
    ios={{
      systemIcon: 3,
      position: "right" as const
    }}
    android={{
      systemIcon: "ic_menu_save"
    }} />
  <actionItem
    nodeRole={"actionItems"}
    onTap={onTapCancel}
    visibility={isEditing ? "visible" : "hidden"}
    ios={{
      systemIcon: 1,
      position: "ic_menu_close_clear_cancel" as const
    }}
  />
</actionBar>
```

## Props

| Name | Type | Description |
|------|------|-------------|
| `ios.systemIcon` | `number` | Sets the icon of the `ActionItem` for iOS. The value must be a number from the [`UIBarButtonSystemItem` enumeration](https://developer.apple.com/documentation/uikit/uibarbuttonitem/systemitem).
| `android.systemIcon` | `string` | Sets the icon of the `ActionItem` for Android. The value must be the name of a [drawable resource](https://developer.android.com/guide/topics/resources/drawable-resource).
| `ios.position` | `string` | Sets the position of the `ActionItem` within the `ActionBar` for iOS.<br/>Valid values: `left` or `right`.<br/>Default value is `left`.
| `android.position` | `string` | Sets the position of the `ActionItem` within the `ActionBar` for Android.<br/>Valid values:<br/>`actionBar` (places the item in the ActionBar)<br/>`popup` (places the item in the options menu; renders items as text)<br/>`actionBarIfRoom` (places the item in the `ActionBar` if there is enough room for it there; otherwise, placess it in the options menu)<br/>Default value is `actionBar`.
| `onTap` | `(args: `[`EventData`](https://docs.nativescript.org/api-reference/interfaces/__nativescript_core_.eventdata)`) => void` | Emitted when the `ActionItem` is tapped.

## Native component

| Android | iOS |
|---------|-----|
| [`android.widget.Toolbar`](https://developer.android.com/reference/android/widget/Toolbar.html) | [`UINavigationItem`](https://developer.apple.com/documentation/uikit/uinavigationitem)