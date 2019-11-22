---
id: navigation
title: Navigation
---
<!-- contributors: [shirakaba] -->

## Introduction

### Non-native navigation

Using non-native navigation would be preferable, as they interoperate better with the React abstraction. However, there is no officially recommended non-native navigation library.

React Navigation is not supported (yet). It's likely a very big task to add React NativeScript support to React Navigation, as each different React renderer needs to provide their own implementation.

Simpler renderer-independent routing frameworks like React Router may work out-of-the-box, however.

For now, the most well characterised navigation pattern is native navigation (see next section).

### Native navigation

*Note: This preliminary documentation on native navigation is mostly copied from my sample real-world app, [`rpstrackerrns`](https://github.com/shirakaba/rpstrackerrns), so it may make more sense just to read it in context over at that repository's [README page](https://github.com/shirakaba/rpstrackerrns/blob/master/README.md).*

There are a few possible native navigation patterns, but they're all just different ways of invoking [NativeScript Core navigation](https://docs.nativescript.org/core-concepts/navigation) from React. The key idea is to ensure that the target Page is mounted, and tell the visible Frame to navigate to it. This practically always requires registering references on the React components that wrap the underlying NativeScript Frame/Page instances.

## Frame to root Page

A Frame is only useful once it has navigated to an initial 'root' page. To navigate your Frame to a Page as early as possible in its lifecycle, see my usage of the `componentDidMount()` method in the Frame components in [`app/AppRootAnonymous.tsx`](https://github.com/shirakaba/rpstrackerrns/blob/master/AppRootAnonymous.tsx) or [`app/AppRootAuthenticated.tsx`](https://github.com/shirakaba/rpstrackerrns/blob/master/app/AppRootAuthenticated.tsx).

## Page to Page

To be precise, you must ask the *Frame* to navigate to a new Page. When doing so, the NativeScript Core API that React NativeScript makes use of here gives some options about how exactly to do this.

In React NativeScript, I allow Page components to be nested inside other Page components so that it's easier to coordinate the rendering lifecycle of a dependent Page. I welcome the community to build a better solution to improve upon this rather odd state-of-the-art.

I explored an alternative pattern for rendering Pages "out-of-tree" on-demand (shown in [`app/shared/helpers/navigation/nav-react.helper.tsx`](https://github.com/shirakaba/rpstrackerrns/tree/master/app/shared/helpers/navigation/nav-react.helper.tsx)), but it leads to crashes in certain circumstances, so I can't recommend it; instead, please use the pattern of nesting any dependent (target) Pages inside their source Pages.

### Clearing 'back' history upon navigation

This prevents a 'back' button appearing in the ActionBar (if an ActionBar is visible at all, which it isn't in a few of these cases).

See how `clearHistory` is set to `true` in:

* the `onLoginTap()` and `onGotoRegisterTap()` methods of [`app/views/pages/login/LoginPage.tsx`](https://github.com/shirakaba/rpstrackerrns/tree/master/app/views/pages/login/LoginPage.tsx), and;
* the `onGoToLoginTap()` method of [`app/views/pages/register/RegisterPage.tsx`](https://github.com/shirakaba/rpstrackerrns/blob/master/app/views/pages/register/RegisterPage.tsx), and;
* the `onLogoutTap()` method of [`app/views/pages/backlog/BacklogPage.tsx`](https://github.com/shirakaba/rpstrackerrns/blob/master/app/views/pages/backlog/BacklogPage.tsx).

### Preserving 'back' history upon navigation

This ensures that a 'back' button will appear in any ActionBar for the given Page (if visible).

See how `clearHistory` is set to `false` or left unspecified in:

* the `onSettingsTap()` and `onListItemTap()` methods of [`app/views/pages/backlog/BacklogPage.tsx`](https://github.com/shirakaba/rpstrackerrns/blob/master/app/views/pages/backlog/BacklogPage.tsx).

### Taking action upon 'back' navigation

An example of this is left in the comments of `onNavigatedFromDetailPage()` and `onNavigatedFromSettingsPage()` in [`app/views/pages/backlog/BacklogPage.tsx`](https://github.com/shirakaba/rpstrackerrns/blob/master/app/views/pages/backlog/BacklogPage.tsx).

There wasn't much use for it in this particular app.

## See also

There is far more to be said than I can cover here, so, from the official NativeScript Core docs:

* [Navigation](https://docs.nativescript.org/core-concepts/navigation)
* [Nested navigation](https://docs.nativescript.org/core-concepts/nested-navigation)