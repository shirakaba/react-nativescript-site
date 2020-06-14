---
id: plugins
title: Plugins
---
<!-- contributors: [shirakaba, EddyVerbruggen, naderio, rigor789, ikoevska, jlooper] -->

## Introduction

In NativeScript, a plugin is the name for a module that creates an abstraction around something – usually, a cross-platform abstraction around native APIs or UI elements. For example, a plugin to check the device's battery level might provide a common API by which one could inspect the battery level regardless of whether the device be based on iOS or Android.

Plugins work as in [any other NativeScript app](https://docs.nativescript.org/plugins/plugins), but you may wonder how _UI_ plugins work with React NativeScript.

UI plugins work almost identically to how you'd use a NativeScript UI plugin in a NativeScript Angular or NativeScript Vue app.

## Sample use: nativescript-gradient

Let's review how you can use [nativescript-gradient](https://github.com/EddyVerbruggen/nativescript-gradient).

<!-- You can also check its use in the [listview sample](https://github.com/rigor789/nativescript-vue/tree/master/samples/app/app-with-list-view.js). -->

### Install the plugin using the NativeScript CLI

After you have [set up your system for NativeScript development](/docs/getting-started/installation), run the following command:

```sh
$ npm install --save nativescript-gradient
```

> **NOTE:** If your plugin doesn't work right away, you might need to clean the project by removing the Platforms folders:

```shell
$ rm -rf platforms
```

### Register the plugin in your app

Open your app entry file (likely `app.ts`) and add the following call to `registerElement()` anywhere before the call to `start()`:

```ts
import { registerElement } from "react-nativescript";

registerElement('gradient', () => require('nativescript-gradient').Gradient);
```

This requires and registers the plugin into React NativeScript's set of JSX intrinsic elements. The `registerElement()` function expects the name of the `<element>` as the first argument, and a function that returns the plugin as its second argument. Provide the element name exactly as you are supposed to call it in your code (MUST begin with a lower-case first letter, due to the rules of JSX). Provide the plugin name exactly as its npm package name.

### Provide typings for it

This part is rather harder, because it depends on the quality of the typings offered by the plugins author. Unfortunately, plugins authors do not often provide typings that are in the right format for consumption by React. In fact, it feels like typings are very often an afterthought in plugins even for more mature flavours of NativeScript (Angular, Vue, and Core).

One day we may have a CLI tool to auto-generate these typings (it's under construction [here](https://github.com/halfnelson/nativescript-source-to-jsx-def)), but until then, this process shall unfortunately remain a manual affair.

Here's the essence of what you need to do. I would tend to write this code into your entrypoint file, `app.ts`, but it can be placed anywhere, really.

```ts
// app.ts
import { NativeScriptProps, StackLayoutAttributes } from "react-nativescript";
import type { Gradient } from "nativescript-gradient";
import type { PropertyChangeData } from "@nativescript/core/data/observable/observable";

/**
 * NativeScript Gradient extends StackLayout, so it inherits all the
 * same attributes. Thus, we extend StackLayoutAttributes here.
 */
interface GradientAttributes extends StackLayoutAttributes {
    /**
     * These are all the properties supported by NativeScript Gradient.
     * I filled these in manually by inspecting the typings and implementation.
     */
    direction?: string;
    borderRadius?: number;
    colors?: string;

    /**
     * Event handlers in React NativeScript follow React Native
     * naming convention. So, to handle a NativeScript Core event named
     * "borderRadiusChange", pass in a prop to React NativeScript named
     * "onBorderRadiusChange".
     * 
     * Every registered property raises its own corresponding onChange
     * event handler, so here's how to write them if they're of use to you.
     */
    onDirectionChange?: (arg: PropertyChangeData) => any;
    onBorderRadiusChange?: (arg: PropertyChangeData) => any;
    onColorsChange?: (arg: PropertyChangeData) => any;
}

declare global {
    module JSX {
        interface IntrinsicElements {
            /**
             * If determining the GradientAttributes is too much work,
             * you could substitute it for `any` type!
             */
            gradient: NativeScriptProps<GradientAttributes, Gradient>,
        }
    }
}
```

### Use the plugin in your app

```tsx
<gradient direction="to right" colors="#FF0077, red, #FF00FF">
  <label
    text="Best gradient."
    horizontalAlignment="center"
    style={{ color: "white", padding: 20 }}
  />
</gradient>
```
