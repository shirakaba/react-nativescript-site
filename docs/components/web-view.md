---
id: WebView
title: WebView
---
<!-- contributors: [shirakaba, MisterBrownRSA, rigor789, eddyverbruggen, ikoevska] -->

`<$WebView>` is a UI component that lets you show web content in your app. You can pull and show content from a URL or a local HTML file, or you can render static HTML content.

See also:

* [Official top-level documentation](https://docs.nativescript.org/ui/components/web-view)
* [Detailed API specification](https://docs.nativescript.org/api-reference/classes/_ui_web_view_.webview)
* [HtmlView](/docs/components/html-view)

---

```tsx
<$WebView src="http://nativescript-vue.org/" />

<$WebView src="~/html/index.html" />

<$WebView src="<div><h1>Some static HTML</h1></div>" />
```

<!-- [> screenshots for=WebView <] -->

## Props

| Name | Type | Description |
|------|------|-------------|
| `src` | `string` | Gets or sets the displayed web content.<br/>Valid values: an absolute URL, the path to a local HTML file, or static HTML.
| `onLoadStarted` | `(args: `[`LoadEventData`](https://docs.nativescript.org/api-reference/interfaces/__nativescript_core_.loadeventdata)`) => void` | Emitted when the page has started loading in the `<$WebView>`.
| `onLoadFinished` | `(args: `[`LoadEventData`](https://docs.nativescript.org/api-reference/interfaces/__nativescript_core_.loadeventdata)`) => void` | Emitted when the page has finished loading in the `<$WebView>`.

## Native component

| Android | iOS |
|---------|-----|
| [`android.webkit.WebView`](https://developer.android.com/reference/android/webkit/WebView) | [`WKWebView`](https://developer.apple.com/documentation/webkit/wkwebview)