---
id: Label
title: Label
---
<!-- contributors: [shirakaba, MisterBrownRSA, rigor789, eddyverbruggen, ikoevska] -->

`<label>` is a UI component that displays read-only text.

**IMPORTANT**: This `<label>` is **not** the same as the HTML `<label>`.

See also:

* [Official top-level documentation](https://docs.nativescript.org/ui/components/label)
* [Detailed API specification](https://docs.nativescript.org/api-reference/classes/_ui_label_.label)

---

You can either use the `<label>` element's `text` prop or enter text as a child node.

```tsx
import * as React from "react";

<label>This is a Label</label>
```

<!-- [> screenshots for=Label <] -->

### Styling the label

If you need to style parts of the text, you can use a combination of a [`FormattedString`](https://docs.nativescript.org/angular/ui/ng-ui-widgets/formatted-string) and [`Span`](https://docs.nativescript.org/api-reference/classes/_text_span_.span) elements.

You can either use the `<span>` element's `text` prop or enter text as a child node.

```tsx
import * as React from "react";
import { Color } from "@nativescript/core";

<label textWrap={true}>
  <formattedString>
    <span>This text has a </span>
    <span color={new Color("red")}>red </span>
    <span>piece of text. </span>
    <span fontStyle="italic">Also, this bit is italic, </span>
    <span fontWeight="bold">and this bit is bold.</span>
  </formattedString>
</label>
```

## Props

| Name | Type | Description |
|------|------|-------------|
| `text` | `string` | Gets or sets the text of the label.
| `textWrap` | `boolean` | Gets or sets whether the label wraps text.<br/>Default value: `false`.

## Native component

| Android | iOS |
|---------|-----|
| [`android.widget.TextView`](https://developer.android.com/reference/android/widget/TextView.html) | [`UILabel`](https://developer.apple.com/documentation/uikit/uilabel)
