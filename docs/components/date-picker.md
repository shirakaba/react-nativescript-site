---
id: DatePicker
title: DatePicker
contributors: [shirakaba, MisterBrownRSA, rigor789, ikoevska]
---

`<$DatePicker>` is a UI component that lets users select a date from a pre-configured range (see the official [top-level documentation](https://docs.nativescript.org/ui/components/date-picker) and [detailed API specification](https://docs.nativescript.org/api-reference/classes/_ui_date_picker_.datepicker)).

> See also: [TimePicker](/docs/components/time-picker).

---

```tsx
import { NarrowedEventData } from "react-nativescript/dist/shared/NativeScriptComponentTypings";

<$DatePicker
  date={new Date()}
  onDateChange={(args: NarrowedEventData<DatePicker>) => {}}
/>
```

[> screenshots for=DatePicker <]

## Props

| Name | Type | Description |
|------|------|-------------|
| `date` | `Date` | Gets or sets the complete date.
| `minDate` | `Date` | Gets or sets the earliest possible date to select.
| `maxDate` | `Date` | Gets or sets the latest possible date to select.
| `day` | `number` | Gets or sets the day.
| `month` | `number` | Gets or sets the month.
| `year` | `number` | Gets or sets the year.

## Events

| Name | Description |
|------|-------------|
| `dateChange` | Emitted when the selected date changes.

## Native component

| Android |	iOS |
|---------|-----|
| [`android.widget.DatePicker`](https://developer.android.com/reference/android/widget/DatePicker.html) | [`UIDatePicker`](https://developer.apple.com/documentation/uikit/uidatepicker)
