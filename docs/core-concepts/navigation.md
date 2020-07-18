---
id: navigation
title: Navigation
---
<!-- contributors: [shirakaba] -->

## Introduction

To understand the full range of options for navigation in React NativeScript, we must first explore the options in NativeScript Core (for which React NativeScript acts as a React wrapper).

### NativeScript Core navigation methods

NativeScript Core provides two main methods of navigation, summarised in their [Navigation docs](https://docs.nativescript.org/core-concepts/navigation):

* Stack-based navigation, via the [Frame](https://docs.nativescript.org/ui/components/frame) and [Page](https://docs.nativescript.org/ui/components/page) components.
* Tab-based navigation, via the deprecated [TabView](https://docs.nativescript.org/ui/components/tab-view) component, or, as of NativeScript 6, the newer [Tabs](https://docs.nativescript.org/ui/components/tabs) or [BottomNavigation](https://docs.nativescript.org/ui/components/bottom-navigation) components.

[Nested navigation](https://docs.nativescript.org/core-concepts/nested-navigation) is also possible.

These navigation methods are fully native, i.e. the components involved are all wrappers around iOS/Android navigation solutions. Thus, you can expect excellent performance and a robust appearance.

### React NativeScript navigation methods

#### DON'T use the NativeScript navigators directly

React NativeScript wraps all of the aforementioned components as React components, but it's fiddly to use them directly as all the navigation actions are non-declarative, meaning they don't map well to React and you have to do a lot of ref-handling. Without special care, you may find the navigator model going out of sync with your React state (e.g. due to neglecting to update the history stack upon user interaction).

Thus, I **strongly recommend** to not use `<frame>`, `<page>`, `<tabView>`, `<tabs>`, or `<bottomNavigation>` directly. It's a good way to lose your weekend chasing bugs.

#### DO use React NativeScript Navigation

Instead, I've implemented [**React Navigation v5**](https://reactnavigation.org/docs/getting-started) library for React NativeScript, which uses those navigation components under-the-hood. I've unimaginatively named it [`react-nativescript-navigation`](https://github.com/shirakaba/react-nativescript-navigation/tree/master/react-nativescript-navigation).

It has all the same APIs as React Navigation, and implements both a TabNavigator and a StackNavigator (SwitchNavigators are [no longer necessary](https://reactnavigation.org/docs/upgrading-from-4.x/#switch-navigator) as of React Navigation v5).

##### Getting started

* Read the README on the [`react-nativescript-navigation`](https://github.com/shirakaba/react-nativescript-navigation/tree/master/react-nativescript-navigation) repo for basic usage details.
* Refer to the [React Navigation v5 docs](https://reactnavigation.org/docs/getting-started) for full detail on how to navigate.
