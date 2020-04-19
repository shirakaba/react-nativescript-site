---
id: WebView
title: WebView
---
<!-- contributors: [shirakaba, MisterBrownRSA, rigor789, eddyverbruggen, ikoevska] -->

`<webView>` is a UI component that lets you show web content in your app. You can pull and show content from a URL or a local HTML file, or you can render static HTML content.

See also:

* [Official top-level documentation](https://docs.nativescript.org/ui/components/web-view)
* [Detailed API specification](https://docs.nativescript.org/api-reference/classes/_ui_web_view_.webview)
* [`<htmlView>`](/docs/components/html-view)

---

```tsx
import * as React from "react";

<webView src="http://nativescript-vue.org/" />

<webView src="~/html/index.html" />

<webView src="<div><h1>Some static HTML</h1></div>" />
```

<!-- [> screenshots for=WebView <] -->

## Props

| Name | Type | Description |
|------|------|-------------|
| `src` | `string` | Gets or sets the displayed web content.<br/>Valid values: an absolute URL, the path to a local HTML file, or static HTML.
| `onLoadStarted` | `(args: `[`LoadEventData`](https://docs.nativescript.org/api-reference/interfaces/__nativescript_core_.loadeventdata)`) => void` | Emitted when the page has started loading in the `<webView>`.
| `onLoadFinished` | `(args: `[`LoadEventData`](https://docs.nativescript.org/api-reference/interfaces/__nativescript_core_.loadeventdata)`) => void` | Emitted when the page has finished loading in the `<webView>`.

## Native component

| Android | iOS |
|---------|-----|
| [`android.webkit.WebView`](https://developer.android.com/reference/android/webkit/WebView) | [`WKWebView`](https://developer.apple.com/documentation/webkit/wkwebview)