---
id: TextField
title: TextField
---
<!-- contributors: [shirakaba, MisterBrownRSA, rigor789, TheOriginalJosh, eddyverbruggen, ikoevska] -->

`<$TextField>` is an input component that creates an editable single-line box.

`<$TextField>` extends [`TextBase`](https://docs.nativescript.org/api-reference/classes/_ui_text_base_.textbase) and [`EditableTextBase`](https://docs.nativescript.org/api-reference/classes/_ui_editor_text_base_.editabletextbase) which provide additional properties and events.

See also:

* [Official top-level documentation](https://docs.nativescript.org/ui/components/text-field)
* [Detailed API specification](https://docs.nativescript.org/api-reference/modules/_ui_text_field_)

---

<!-- TODO: explain that setState must be performed (e.g. on blur) to sync native text value with that of React state. -->

```tsx
import { $TextField } from "react-nativescript";

<$TextField text={textFieldValue} hint="Enter text..." />
```

<!-- [> screenshots for=TextField <] -->

## Props

| Name | Type | Description |
|------|------|-------------|
| `text` | `string` | Sets the value of the field.
| `hint` | `string` | Sets the placeholder text.
| `editable` | `boolean` | When `true`, indicates that the user can edit the value of the field.
| `maxLength` | `number` | Limits input to the spcified number of characters.
| `secure` | `boolean` | Hides the entered text when `true`. Use this property to create password input fields.<br/>Default value: `false`.
| `keyboardType` | [`KeyboardType`](https://docs.nativescript.org/api-reference/modules/__nativescript_core_#keyboardtype) | Shows a custom keyboard for easier text input.<br/>Valid values: `datetime`, `phone`, `number`, `url`, or `email`.
| `returnKeyType` | [`ReturnKeyType`](https://docs.nativescript.org/api-reference/modules/__nativescript_core_#returnkeytype) | Sets the label of the return key.<br/>Valid values: `done`, `next`, `go`, `search`, or `send`.
| `autocorrect` | `boolean` | Enables or disables autocorrect.
| `onBlur` | `(args: `[`EventData`](https://docs.nativescript.org/api-reference/interfaces/__nativescript_core_.eventdata)`) => void` | Emitted when the field loses focus.
| `onFocus` | `(args: `[`EventData`](https://docs.nativescript.org/api-reference/interfaces/__nativescript_core_.eventdata)`) => void` | Emitted when the field gains focus.
| `onReturnPress` | `(args: `[`EventData`](https://docs.nativescript.org/api-reference/interfaces/__nativescript_core_.eventdata)`) => void` | Emitted when the return key is pressed.
| `onTextChange` | `(args: `[`EventData`](https://docs.nativescript.org/api-reference/interfaces/__nativescript_core_.eventdata)`) => void` | Emitted when the text changes.

## Native component

| Android | iOS |
|---------|-----|
| [`android.widget.EditText`](https://developer.android.com/reference/android/widget/EditText.html) | [`UITextField`](https://developer.apple.com/documentation/uikit/uitextfield)
