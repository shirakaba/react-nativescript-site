---
id: quick-start
title: Quick Start
sidebar_label: Quick Start
---

<!-- If you don't want the hassle of installing and configuring your system before you can have a taste of React NativeScript, the NativeScript Playground has you covered. -->

Provided you already have your system ready for native development (see [Getting Started with NativeScript](https://www.nativescript.org/getting-started-with-nativescript) from the NativeScript official documentation), you can start by using the `tns-template-blank-react` starter boilerplate:

```sh
tns create my-blank-react --template tns-template-blank-react

cd my-blank-react
npm install

tns preview
# or
tns run ios
# or
tns run android
```
This set of commands performs the following operations on your system:

1. Creates a project using the `tns-template-blank-react` template.
2. Switches to the directory containing the newly created project.
3. Installs any npm dependencies locally.
4. If executing `tns preview`, produces a QR code which can be used to preview the app on a device.
5. If executing `tns run`, builds and runs the project on all connected devices or in native emulators.