---
id: Button
title: Button
contributors: [shirakaba, MisterBrownRSA, rigor789, eddyverbruggen, ikoevska]
---

`<Button>` is a UI component that displays a button which reacts to a user gesture (see the official [top-level documentation](https://docs.nativescript.org/ui/components/activity-indicator) and [detailed API specification](https://docs.nativescript.org/api-reference/classes/_ui_button_.button)).

For more information about the available gestures, see [Gestures in the official NativeScript documentation](https://docs.nativescript.org/ui/gestures).

---

```tsx
import { NarrowedEventData } from "react-nativescript/dist/shared/NativeScriptComponentTypings";

<$Button text="Button" onTap={(args: NarrowedEventData<Button>) => {}} />
```

[> screenshots for=Button <]

## Props

| Name | Type | Description |
|------|------|-------------|
| `text` | `string` | Sets the label of the button.
| `textWrap` | `boolean` | Gets or sets whether the widget wraps the text of the label. Useful for longer labels. Default value is `false`.

## Events

| Name | Description |
|------|-------------|
| `onTap` | Emitted when the button is tapped.

## Native component

| Android | iOS |
|---------|-----|
| [`android.widget.Button`](https://developer.android.com/reference/android/widget/Button.html) | [`UIButton`](https://developer.apple.com/documentation/uikit/uibutton)