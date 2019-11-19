---
id: Slider
title: Slider
---
<!-- contributors: [shirakaba, MisterBrownRSA, rigor789, eddyverbruggen, ikoevska] -->

`<$Slider>` is a UI component that provides a slider control for picking values within a specified numeric range.

See also:

* [Official top-level documentation](https://docs.nativescript.org/ui/components/slider)
* [Detailed API specification](https://docs.nativescript.org/api-reference/classes/_ui_slider_.slider)

---

```tsx
import { $Slider } from "react-nativescript";

<$Slider value={0} onValueChange={onValueChange} />
```

<!-- [> screenshots for=Slider <] -->

## Props

| Name | Type | Description |
|------|------|-------------|
| `value` | `number` | Sets the currently selected value of the slider.<br/>Default value: `0`.
| `minValue` | `number` | Sets the minimum value of the slider.<br/>Default value: `0`.
| `maxValue` | `number` | Sets the maximum value of the slider.<br/>Default value: `100`.
| `onValueChange`| `(args: `[`EventData`](https://docs.nativescript.org/api-reference/interfaces/__nativescript_core_.eventdata)`) => void` | Emitted when the value of the slider changes.

## Native component

| Android | iOS |
|---------|-----|
| [`android.widget.SeekBar`](https://developer.android.com/reference/android/widget/SeekBar.html) | [`UISlider`](https://developer.apple.com/documentation/uikit/uislider)
