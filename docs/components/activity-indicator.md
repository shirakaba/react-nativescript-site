---
id: ActivityIndicator
title: ActivityIndicator
contributors: [shirakaba, MisterBrownRSA, rigor789, ikoevska]
---

`<$ActivityIndicator>` is a UI component that shows a progress indicator signaling to the user of an operation running in the background.

See also:

* [Official top-level documentation](https://docs.nativescript.org/ui/components/activity-indicator)
* [Detailed API specification](https://docs.nativescript.org/api-reference/classes/_ui_activity_indicator_.activityindicator)

---

```tsx
<$ActivityIndicator busy={true} />
```

[> screenshots for=ActivityIndicator <]

## Props

| Name | Type | Description |
|------|------|-------------|
| `busy` | `Boolean` | Gets or sets whether the indicator is active. When `true`, the indicator is active.

## Native component

| Android | iOS |
|---------|-----|
| [`android.widget.ProgressBar` (indeterminate = true)](https://developer.android.com/reference/android/widget/ProgressBar.html)	| [`UIActivityIndicatorView`](https://developer.apple.com/documentation/uikit/uiactivityindicatorview)