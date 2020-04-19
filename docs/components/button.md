---
id: Button
title: Button
---
<!-- contributors: [shirakaba, MisterBrownRSA, rigor789, eddyverbruggen, ikoevska] -->

`<Button>` is a UI component that displays a button which reacts to a user gesture.

See also:

* [Official top-level documentation](https://docs.nativescript.org/ui/components/activity-indicator)
* [Detailed API specification](https://docs.nativescript.org/api-reference/classes/_ui_button_.button)
* Official top-level documentation for [Gestures](https://docs.nativescript.org/ui/gestures)

---

```tsx
import * as React from "react";
import { EventData } from "@nativescript/core";

<button
  text="Button"
  onTap={(args: EventData) => {
    const button = args.object;
  }}
/>
```

<!-- [> screenshots for=Button <] -->

## Props

| Name | Type | Description |
|------|------|-------------|
| `text` | `string` | Sets the label of the button.
| `textWrap` | `boolean` | Sets whether the widget wraps the text of the label. Useful for longer labels. Default value is `false`.
| `onTap` | `(args: `[`EventData`](https://docs.nativescript.org/api-reference/interfaces/__nativescript_core_.eventdata)`) => void` | Emitted when the `Button` is tapped.

## Native component

| Android | iOS |
|---------|-----|
| [`android.widget.Button`](https://developer.android.com/reference/android/widget/Button.html) | [`UIButton`](https://developer.apple.com/documentation/uikit/uibutton)
