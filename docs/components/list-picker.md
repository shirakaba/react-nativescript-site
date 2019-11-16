---
id: ListPicker
title: ListPicker
contributors: [shirakaba, MisterBrownRSA, rigor789, ikoevska]
---

`<$ListPicker>` is a UI component that lets the user select a value from a pre-configured list.

See also:

* [Official top-level documentation](https://docs.nativescript.org/ui/components/list-picker)
* [Detailed API specification](https://docs.nativescript.org/api-reference/classes/_ui_list_picker_.listpicker)

---

```tsx
import { NarrowedEventData } from "react-nativescript/dist/shared/NativeScriptComponentTypings";

<$ListPicker
  items={listOfItems}
  selectedIndex={0}
  onSelectedIndexChange={(args: NarrowedEventData<ListPicker>) => {
    const listPicker: ListPicker = args.object;
    const index: number = listPicker.selectedIndex;
    const item = listPicker.items[index];
  }}
/>
```

[> screenshots for=ListPicker <]

## Props

| Name | Type | Description |
|------|------|-------------|
| `items` | `Array<string>` | Gets or sets the items displayed as options in the list picker.
| `selectedIndex` | `number` | Gets or sets the index of the currently selected item.

## Events

| Name | Description |
|------|-------------|
| `onSelectedIndexChange`| Emitted when the currently selected option (index) changes. The new index can be retrieved via `args.object.selectedIndex`.

## Native component

| Android | iOS |
|---------|-----|
| [`android.widget.NumberPicker`](https://developer.android.com/reference/android/widget/NumberPicker.html) | [`UIPickerView`](https://developer.apple.com/documentation/uikit/uipickerview)
