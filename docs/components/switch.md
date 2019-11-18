---
id: Switch
title: Switch
---
<!-- contributors: [shirakaba, MisterBrownRSA, rigor789, ikoevska] -->

`<$Switch>` is a UI component that lets users toggle between two states.

The default state is `false` or OFF.

See also:

* [Official top-level documentation](https://docs.nativescript.org/ui/components/switch)
* [Detailed API specification](https://docs.nativescript.org/api-reference/classes/_ui_switch_.switch)

---

```tsx
<$Switch checked={true} />
```

<!-- [> screenshots for=Switch <] -->

## Props

| Name | Type | Description |
|------|------|-------------|
| `checked` | `boolean` | Gets or sets the value of the switch selection.<br/>Default value: `false`.
| `onToggle`| `(args: `[`EventData`](https://docs.nativescript.org/api-reference/interfaces/__nativescript_core_.eventdata)`) => void` | Emitted when the value of the switch changes.

## Native component

| Android | iOS |
|---------|-----|
| [`android.widget.Switch`](https://developer.android.com/reference/android/widget/Switch.html) | [`UISwitch`](https://developer.apple.com/documentation/uikit/uiswitch)
