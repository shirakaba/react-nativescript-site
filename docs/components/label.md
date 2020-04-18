---
id: Label
title: Label
---
<!-- contributors: [shirakaba, MisterBrownRSA, rigor789, eddyverbruggen, ikoevska] -->

`<$Label>` is a UI component that displays read-only text.

**IMPORTANT**: This `<$Label>` is **not** the same as the HTML `<label>`.

See also:

* [Official top-level documentation](https://docs.nativescript.org/ui/components/label)
* [Detailed API specification](https://docs.nativescript.org/api-reference/classes/_ui_label_.label)

---

```tsx
import * as React from "react";
import { $Label } from "react-nativescript";

<$Label text="Label" />
```

<!-- [> screenshots for=Label <] -->

### Styling the label

If you need to style parts of the text, you can use a combination of a [`FormattedString`](https://docs.nativescript.org/angular/ui/ng-ui-widgets/formatted-string) and [`Span`](https://docs.nativescript.org/api-reference/classes/_text_span_.span) elements.

```tsx
import * as React from "react";
import { $Label, $FormattedString, $Span } from "react-nativescript";
import { Color } from "@nativescript/core";

<$Label textWrap={true}>
  <$FormattedString>
    <$Span text="This text has a " />
    <$Span text="red " color={new Color("red")} />
    <$Span text="piece of text. " />
    <$Span text="Also, this bit is italic, " fontStyle="italic" />
    <$Span text="and this bit is bold." fontWeight="bold" />
  </$FormattedString>
</$Label>
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
