---
id: TimePicker
title: TimePicker
---
<!-- contributors: [shirakaba, MisterBrownRSA, rigor789, ikoevska] -->

`<timePicker>` is a UI component that lets users select time. 

See also:

* [Official top-level documentation](https://docs.nativescript.org/ui/components/time-picker)
* [Detailed API specification](https://docs.nativescript.org/api-reference/classes/_ui_time_picker_.timepicker)
* [`<datePicker>`](/docs/components/date-picker)

---

```tsx
import * as React from "react";

<timePicker hour={selectedHour} minute={selectedMinute} />
```

`<timePicker>` provides two-way data binding using `v-model`.

<!-- [> screenshots for=TimePicker <] -->

## Props

| Name | Type | Description |
|------|------|-------------|
| `hour` | `number` | Sets the selected hour.
| `minute` | `number` | Sets the selected minute.
| `time` | `Date` | Sets the selected time.
| `minHour` | `number` | Sets the minimum selectable hour.
| `maxHour` | `number` | Sets the maximum selectable hour.
| `minMinute` | `number` | Sets the minimum selectable minute.
| `maxMinute` | `number` | Sets the maximum selectable minute.
| `minuteInterval` | `number` | Sets the selectable minute interval. For example: 5 or 15 minutes.<br/>Default value: `1`.
| `onTimeChange` | `(args: `[`EventData`](https://docs.nativescript.org/api-reference/interfaces/__nativescript_core_.eventdata)`) => void` | Emitted when the selected time changes.

## Native component

| Android | iOS |
|---------|-----|
| [`android.widget.TimePicker`](https://developer.android.com/reference/android/widget/TimePicker) | [`UIDatePicker`](https://developer.apple.com/documentation/uikit/uidatepicker)
