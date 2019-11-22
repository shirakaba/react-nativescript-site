---
id: native-access
title: Native Access
---
<!-- contributors: [shirakaba] -->

React NativeScript has all the same native bindings that NativeScript does! You can synchronously call into the Objective-C (iOS) or Java (Android) runtime using JavaScript. All data types can be marshaled back and forth between native and JS. And when using TypeScript, you benefit from having full typings to aid auto-complete rather than having to guess at call signatures.

## Basic example: Initialising a `UIViewController` in iOS

Let's forget about our React-based UI for a moment. You can write this code anywhere in your React NativeScript codebase and it'll work, thanks to the native bindings provided by NativeScript's JavaScript Virtual Machine that React NativeScript runs in.

### Native code

NativeScript's iOS bindings are between the Obj-C and JS runtimes. Here's how to initialise a `UIViewController` in Obj-C:

```objc
// Obj-C
[[UIViewController alloc] init];
```

Here's that same code in Swift in case you're more of a Swift thinker. Although please note that the bindings are ultimately between the Obj-C and JS runtimes, so Swift-specific call signatures will be missing.

```swift
// Swift
UIViewController.alloc().init()
```

### Equivalent NativeScript bindings

Here's what we'd write in JS to call that Obj-C method. There are elaborate rules to how call signatures are converted between Obj-C and JS, but I find it easiest just to rely on the TypeScript typings (`tns-platform-declarations`). Here they are for [iOS](https://github.com/NativeScript/NativeScript/tree/master/tns-platform-declarations/ios/objc-x86_64) and [Android](https://github.com/NativeScript/NativeScript/tree/master/tns-platform-declarations/android).

```js
// Javascript
UIViewController.alloc().init();
```


## UI manipulation example: Augmenting a WebView and SearchBar in iOS

### Preliminary explanation

An important thing to keep in mind when dealing with the native context is that there are two layers of wrappers around the underlying native elements:

```
JS/NATIVE UI HIERARCHY

- React NativeScript's `<$WebView>` component (JS)
    - NativeScript Core UI's `WebView` component (JS)
        - iOS's WKWebView element (native), or;
        - Android's android.webkit.WebView element (native).
```

... And they each have their own lifecycle. Note that both the JS UI components are *invisible* in themselves – they merely provide the logic to manage an underlying native view.

Here's what happens upon React's render when you insert a `<$WebView>` component into your JSX tree.

1. `<$WebView>` is rendered.
2. The `WebView` instance managed by the is subsequently mounted into the NativeScript UI hierarchy as a child of another NativeScript UI element (for example a `StackLayout`, as in the below example).
3. The underlying native element (`WKWebView` for iOS; or `android.webkit.WebView` for Android) is "loaded".

When a native element is "loaded", it exists in the native application and you can perform native operations on it. So to actually interact with a native element, you have to get a reference to it **no sooner than** the `onLoaded` event! And conversely, don't try to interact with it after the `onUnloaded` event (as it will have been removed from the app's view tree, and may be deallocated from that event onwards).

Of course, if you want to run view-independent code (e.g. text tokenisation), you can run that at any moment from app startup onwards.

### Worked example

In this example, I make a basic browser (with just a searchbar and a webview). I accessed the native context to do two things:

1. Stop the SearchBar from auto-correcting and auto-capitalising my input text;
2. Inject some JavaScript into every page I visit (to change the background colour to red).

You'll see that any modules that are globally accessible in the iOS runtime are also globally accessible in the NativeScript JS runtime! And all native libraries are implicitly imported (this may be slimmed down in future), so you don't need ever need to import any native frameworks.

```tsx
/// <reference types="tns-platform-declarations/ios" />

import * as React from "react";
import { WebView, SearchBar, EventData, isIOS } from "@nativescript/core";
import { $WebView, $SearchBar, $StackLayout } from "react-nativescript";

interface Props {
}

interface State {
  src: string;
  searchText: string;
}

export class BrowserExample extends React.Component<Props, State> {
  constructor(props) {
    super(props);

    this.state = {
      searchText: "",
      src: "https://www.birchlabs.co.uk",
    };
  }

  onSearchbarLoaded = (args: EventData) => {
    const sb: SearchBar = args.object as SearchBar;

    if (!isIOS) {
      console.warn(`[SearchBar] iOS-only example.`);
      return;
    }

    const nativeSb: UISearchBar = sb.ios as UISearchBar;
    nativeSb.autocorrectionType = UITextAutocorrectionType.No;
    nativeSb.autocapitalizationType = UITextAutocapitalizationType.None;
  };

  onWebViewLoaded = (args: EventData) => {
    console.log(`[ONLOADED] WebView`);
    const wv: WebView = args.object as WebView;

    if (!isIOS) {
      console.warn(`[WebView] I've only altered the native code for iOS.`);
      return;
    }

    const nativeWv: WKWebView = wv.ios as WKWebView;
    nativeWv.configuration.userContentController.addUserScript(
      WKUserScript.alloc().initWithSourceInjectionTimeForMainFrameOnly(
        `document.body.style.backgroundColor = "red";`,
        WKUserScriptInjectionTime.AtDocumentEnd,
        false,
      )
    );
    nativeWv.reload();
  };

  render() {
    return (
      <$StackLayout>
        <$SearchBar text={this.state.searchText} onLoaded={this.onSearchbarLoaded} />
        <$WebView
          width={{ value: 100, unit: "%" }}
          height={{ value: 100, unit: "%" }}
          src={this.state.src}
          onUrlChange={(args) => {
            this.setState({ src: (args.object as WebView).src });
          }}
          onLoaded={this.onWebViewLoaded}
        />
      </$StackLayout>
    );
  }
}
```

## See also

There is far more to be said than I can cover here, so, from the official NativeScript Core docs:

* [Accessing native APIs through Javascript](https://docs.nativescript.org/core-concepts/accessing-native-apis-with-javascript)
* [iOS runtime overview](https://docs.nativescript.org/core-concepts/ios-runtime/Overview)
* [Android runtime overview](https://docs.nativescript.org/core-concepts/android-runtime/overview)
