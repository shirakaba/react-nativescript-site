---
id: devtools
title: Using React Devtools
sidebar_label: Using React Devtools
---

You can debug React NativeScript applications using the standalone version of React DevTools.

However, as these depend upon a WebSockets implementation (which NativeScript doesn't natively support), you'll need to supply that yourself.

## Step 1: Install dependencies

```sh
cd <project-folder>

# If you already have `react-devtools` installed globally,
# you could simply rely upon the global installation instead.
# i.e.: `npm install -g react-devtools`
npm install --save-dev react-devtools

tns plugin add nativescript-websockets
```

> Warning: This plugin is now only being maintained under a commercial licence (`tns plugin add @pro-plugins/nativescript-websockets`), so we'll have to hope that this freely licenced one remains viable. 🤞

## Step 2: Initialise the Devtools

```typescript
import 'nativescript-websockets'; // Import for side-effects.

Object.defineProperty(global, 'WebSocket', {
    value: (global as any).WebSocket
});

Object.defineProperty(global, '__DEV__', { value: true });

const { connectToDevTools } = require('react-devtools-core');
const wsInstance = connectToDevTools({
    host: 'localhost',
    port: 8097,
    resolveRNStyle: null,
    isAppActive: () => true,
});
```

## Step 3: Set up security

The Devtools communicate unencrypted over `localhost`, so you'll need to make a security exception for app communications over this channel.

*Note: You should remove this exception in the production build of the app if you purely introduced it for the sake of Devtools.*

### iOS

Add the following exception to your `<my-project>/app/App_Resources/iOS/Info.plist`:

```xml
<key>NSAppTransportSecurity</key>
<dict>
    <key>NSExceptionDomains</key>
    <dict>
        <key>localhost</key>
        <dict>
            <key>NSExceptionAllowsInsecureHTTPLoads</key>
            <true/>
        </dict>
    </dict>
</dict>
```

### Android

You'll have to look it up yourself (sorry – I'm not an Android developer).

## Step 4: Run the Devtools

```sh
# If installed globally
react-devtools

# If installed locally
./node_modules/.bin/react-devtools
```

## Step 5: Rebuild and run your app

```sh
rm -rf platforms

tns run android
# or
tns run ios
```

If your machine and app are configured properly, you should see a few components in the component tree of the standalone React DevTools.

## Troubleshooting

### Sanity test

This event listener should be triggered if the Devtools is able to communicate with the app.

```typescript
(window as any).__REACT_DEVTOOLS_GLOBAL_HOOK__.on(
    'react-devtools',
    (agent: any) => {
        console.log(`Got 'react-devtools' callback!`);
    }
);
```