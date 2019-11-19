---
id: installation
title: Environment Setup
sidebar_label: Environment Setup
---
<!-- contributors: [shirakaba, rigor789, TheOriginalJosh, eddyverbruggen, ikoevska] -->


To use React NativeScript, you'll need to set up your system with NativeScript CLI and its dependencies (as well as any tooling for native app development, if not yet installed).

This page is essentially a summary of the more detailed [official NativeScript docs](https://docs.nativescript.org/start/quick-setup) for setting up the NativeScript CLI and its dependencies.

## Prerequisites

* Node.js;
* NativeScript CLI;
* Windows (for developing Android applications on Windows), or;
* macOS (for developing iOS and Android applications on macOS), or;
* Linux (for developing Android applications on Linux).

## Node.js

Download and install the latest LTS version of Node.js from https://nodejs.org/. Restart your terminal and verify the installation was successful by running node --version.

## NativeScript CLI

To install the NativeScript CLI, open your terminal and run:

```sh
npm install -g nativescript
```

Verify the installation was successful by running `tns` in your terminal. You should see a list of the available commands.

## Windows

Check the system requirements and follow the setup instructions for the Android SDK on Windows:

[Advanced setup: Windows](https://docs.nativescript.org/start/ns-setup-win)

## macOS

Check the system requirements and follow the setup instructions for Xcode and the Android SDK on macOS:

[Advanced setup: macOS](https://docs.nativescript.org/start/ns-setup-os-x)

## Linux

Check the system requirements and follow the setup instructions for the Android SDK on Linux:

[Advanced setup: Linux](https://docs.nativescript.org/start/ns-setup-linux)