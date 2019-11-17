---
id: Placeholder
title: Placeholder
contributors: [shirakaba, moeddami]
---

`<$Placeholder>` allows you to add any native widget to your application. To do that, you need to put a Placeholder somewhere in the UI hierarchy and then create and configure the native widget that you want to appear there. Finally, pass your native widget to the event arguments of the creatingView event.

See also:

* [Official top-level documentation](https://docs.nativescript.org/ui/components/placeholder)
* [Detailed API specification](https://docs.nativescript.org/api-reference/classes/_ui_placeholder_.placeholder)

---

```tsx
import { isIOS, isAndroid } from "tns-core-modules/platform/platform";

<$Placeholder onCreatingView={() => {
  if(isIOS){
    const nativeView = new UILabel();
    nativeView.text = "Native View - iOS";
    args.view = nativeView;
  } else if(isAndroid) {
    const nativeView = new android.widget.TextView(args.context);
    nativeView.setSingleLine(true);
    nativeView.setEllipsize(android.text.TextUtils.TruncateAt.END);
    nativeView.setText("Native View - Android");
    args.view = nativeView;
  } else {
    console.warn("Unsupported platform! Did they finally make NativeScript for desktop?");
  }
}}} />
```
