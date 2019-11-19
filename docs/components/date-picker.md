---
id: DatePicker
title: DatePicker
---
<!-- contributors: [shirakaba, MisterBrownRSA, rigor789, ikoevska] -->

`<$DatePicker>` is a UI component that lets users select a date from a pre-configured range.

See also:

* [Official top-level documentation](https://docs.nativescript.org/ui/components/date-picker)
* [Detailed API specification](https://docs.nativescript.org/api-reference/classes/_ui_date_picker_.datepicker)
* [`<$TimePicker>`](/docs/components/time-picker)

---

```tsx
import * as React from "react";
import { $DatePicker } from "react-nativescript";
import { EventData } from "@nativescript/core";

<$DatePicker
  date={new Date()}
  onDateChange={(args: EventData) => {
    const datePicker = args.object;
  }}
/>
```

<!-- [> screenshots for=DatePicker <] -->

## Props

| Name | Type | Description |
|------|------|-------------|
| `date` | `Date` | Sets the complete date.
| `minDate` | `Date` | Sets the earliest possible date to select.
| `maxDate` | `Date` | Sets the latest possible date to select.
| `day` | `number` | Sets the day.
| `month` | `number` | Sets the month.
| `year` | `number` | Sets the year.

## Events

| Name | Description |
|------|-------------|
| `dateChange` | Emitted when the selected date changes.

## Native component

| Android |	iOS |
|---------|-----|
| [`android.widget.DatePicker`](https://developer.android.com/reference/android/widget/DatePicker.html) | [`UIDatePicker`](https://developer.apple.com/documentation/uikit/uidatepicker)
