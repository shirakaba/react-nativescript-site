---
id: HtmlView
title: HtmlView
---
<!-- contributors: [shirakaba, MisterBrownRSA, rigor789, ikoevska] -->

`<$HtmlView>` is a UI component that lets you show static HTML content.

See also:

* [Official top-level documentation](https://docs.nativescript.org/ui/components/html-view)
* [Detailed API specification](https://docs.nativescript.org/api-reference/classes/_ui_html_view_.htmlview)
* [`<$WebView>`](/docs/components/web-view)

---

```tsx
import { $HtmlView } from "react-nativescript";

<$HtmlView html="<div><h1>HtmlView</h1></div>" />
```

<!-- [> screenshots for=HtmlView <] -->

## Props

| Name | Type | Description |
|------|------|-------------|
| `html` | `string` | The HTML content to be shown.

## Native component

| Android | iOS |
|---------|-----|
| [`android.widget.TextView`](https://developer.android.com/reference/android/widget/TextView.html) | [`UITextView`](https://developer.apple.com/documentation/uikit/uitextview)