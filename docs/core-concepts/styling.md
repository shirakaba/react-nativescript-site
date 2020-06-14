---
id: styling
title: Styling
---
<!-- contributors: [shirakaba] -->

## Introduction

Styling in NativeScript Core is a complicated affair, because NativeScript elements were primarily expected to be declared in XML (which only supports string types), but also needed to support JavaScript-based imperative usage.

```ts
import { ContentView } from "@nativescript/core";

const cv = new ContentView();

/** 
 * The `style` field belongs to ViewBase.
 * @module ui/core/view-base/view-base.ts
 * The `width` Property in is registered to the Style class
 * @module ui/styling/style-properties.ts
 */
cv.style.width = 100; // Interpreted as 100 display-independent pixels 
cv.style.width = { value: 100, unit: "dip" };

/**
 * ❌ These two string setters are not allowed by typings, but should
 * both technically work as widthProperty uses PercentLength.parse
 *(which accepts a string) under-the-hood.
 */
cv.style.width = "100";
cv.style.width = "100px";


/**
 * `cv.width` is merely a convenience setter, exposed by View,
 * for `cv.style.width`.
 * @module ui/core/view/view-common.ts
 */
cv.width = 100; // Interpreted as 100 display-independent pixels 
cv.width = { value: 100, unit: "dip" };

/**
 * ❌ These two string setters are not allowed by typings, but should
 * both technically work as widthProperty uses PercentLength.parse
 *(which accepts a string) under-the-hood.
 */
cv.width = "100";
cv.width = "100px";
```

It's not clear why the convenience property `cv.width` exists as well as `cv.width`, and if anything it's bewildering. However, as it's an underlying feature of NativeScript Core, React NativeScript has decided to reflect both ways of setting the styles:

```tsx
<contentView width={100} style={{ width: 100 }} />
```

React NativeScript takes React Native's approach of object-based style declarations, rather than React DOM's approach of string-based style declarations. This is better for re-use of styles, and for intellisense.

### What takes priority between shorthand and longhand styles?

If you declare both `width` and `style.width`, the priority order is indeterminate. Whichever one gets set latest by the Host Config will take priority.

I recommend a best practice of: just don't use the shorthand setters like `width` at all. Please use `style` in all cases and ignore the shorthand options altogether.

## Differences from React Native

### Does `style` accept an array?

Not yet, but I hope to support it in future versions. Please use spread for now.

```tsx
// ❌ NOT supported yet!
const extraStyle = { height: 100 };
<contentView style={[{ width: 100 }, extraStyle]} />

// ✅ Use this approach for now instead.
<contentView style={{ width: 100, ...extraStyle }} />
```

### Does `StyleSheet` exist?

Not yet, but I hope to support it in future versions. There is no intelligent re-use of styles yet.

```tsx
// ❌ No "StyleSheet" API exists yet.
const styles = StyleSheet.create({
    fullWidth: { width: "100%" },
    fullHeight: { height: "100%" },
});

// ✅ This is probably the closest equivalent for now.
import { ViewBaseAttributes } from "react-nativescript/dist/shared/NativeScriptJSXTypings";
type RNSStyle = ViewBaseAttributes["style"];

const styles = {
    fullWidth: { width: "100%" } as RNSStyle,
    fullHeight: { height: "100%" } as RNSStyle,
};

// ❌ This is another option, but would be hard to refactor if
// a StyleSheet.create() API were ever released.
const fullWidthStyle: RNSStyle = { width: "100%" };
const fullheightStyle: RNSStyle = { height: "100%" };
```

There may be a better way to type this to avoid constantly having to re-assert `as RNSStyle`. RNS may provide its own `StyleSheet.create()` method in future if only for typings assistance.

## CSS

React NativeScript supports CSS in all the same ways that NativeScript Core supports it. However, as I don't use CSS in React Native apps, I haven't paid attention to it when developing React NativeScript.

Please refer to the [NativeScript Core Styling docs](https://docs.nativescript.org/ui/styling) for comprehensive information on CSS.


## Best practices for upcoming changes to styling

We 

```tsx
// ❌ Don't use shorthand styles.
<contentView width={100} />
// ✅ Do use longhand styles.
<contentView style={{ width: 100 } />

// ✅ Use spread to spread extra styles until array syntax is supported.
<contentView style={{ width: 100, ...extraStyle }} />
```