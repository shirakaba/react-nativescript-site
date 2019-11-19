---
id: introduction
title: Introduction
sidebar_label: Introduction
---

<!-- Check the [documentation](https://docusaurus.io) for how to use Docusaurus. -->

## What is [NativeScript](https://www.nativescript.org/)?

NativeScript is an open source framework for building truly native mobile applications using JavaScript (or TypeScript), created by Jamie Birch ([GitHub](https://github.com/shirakaba), [Twitter](https://twitter.com/LinguaBrowse)).

## What is [React.js](https://reactjs.org/)?

React is an industry-standard library for developing user interfaces.

## What is React NativeScript?

React NativeScript is a React custom renderer that allows you to describe a NativeScript app using the familiar React 'way of thinking'.

## Did you say [React Native](https://react-native.org/)?

No – React Native is another framework for building truly native mobile applications using JavaScript (or TypeScript). So it fits the same purpose as React NativeScript.

## Why would you use this (and not React Native)?

**In brief:** React NativeScript puts native access at the front of the developer experience.

React Native has a different architecture (the JavaScript Virtual Machine runs on a separate thread to the main/UI thread), and – at the time of writing – it relies on a JSON-serialised bridge to communicate between the native and JS contexts.

This architecture makes native access a chore – any native access from the JS context is necessarily asynchronous, and a lot of boilerplate is needed to set up a JSON-compatible communication interface between the two contexts. Any alterations to native code also require a recompile of the app.

NativeScript (and therefore React NativeScript), by comparison, runs its JS VM on the main thread, and is bridgeless, with JS-native bindings to all the platform's APIs. This means that we can access native functionality synchronously simply by calling it via JS. Native development becomes even faster thanks to JS facilitating hot reload.

## How is its compatibility with the React ecosystem?
​
React NativeScript can use anything that isn't coupled to a particular React renderer. So, for example, Redux will work (as it is simply a state store), but React Navigation (which depends upon React DOM or React Native) won't.

React NativeScript *cannot* consume code from React Native projects – that's a whole large-scale separate project. Support for non-UI plugins from the React Native ecosystem is a long-term area of interest, however.

## Want to get involved?

React NativeScript is an open-source project and contributions are very much encouraged. Join us on the `#react` channel on the [NativeScript Community Slack](https://www.nativescript.org/slack-invitation-form) to chat.

## Who supports it?

Nobody; it's purely been a labour of love. A donation page may pop up at some point in the future, however.

## Is it production-ready?
​
It is feature-equivalent with NativeScript Core, which itself is production-ready (as is React); the question is how well that implementation has been achieved. Until users start picking it up and identifying holes in it, we can't be sure.