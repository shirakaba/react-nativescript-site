---
id: Progress
title: Progress
---
<!-- contributors: [shirakaba, MisterBrownRSA, rigor789, eddyverbruggen, ikoevska] -->

`<progress>` is a UI component that shows a bar to indicate the progress of a task.

See also:

* [Official top-level documentation](https://docs.nativescript.org/ui/components/progress)
* [Detailed API specification](https://docs.nativescript.org/api-reference/classes/_ui_progress_.progress)
* [`<activityIndicator>`](/docs/components/activity-indicator)

---

```tsx
import * as React from "react";

function getTaskCompletionPercent(){
    // Just a stub method to illustrate the concept.
    return 10;
}

<progress value={getTaskCompletionPercent()} maxValue={100} />
```

<!-- [> screenshots for=Progress <] -->

## Props

| Name | Type | Description |
|------|------|-------------|
| `value` | `number` | Sets the current value of the progress bar. Must be within the range of 0 to `maxValue`.
| `maxValue` | `number` | Sets the maximum value of the progress bar.<br/>Default value: `100`.

## Native Component

| Android | iOS |
|---------|-----|
| [`android.widget.ProgressBar` (indeterminate = false)](https://developer.android.com/reference/android/widget/ProgressBar.html) | [`UIProgressView`](https://developer.apple.com/documentation/uikit/uiprogressview)
