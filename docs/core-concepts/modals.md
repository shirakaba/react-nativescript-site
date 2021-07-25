---
id: modals
title: Modals
---
<!-- contributors: [mayerlench, shirakaba] -->

Modals act like overlays, the goal here is to show a component modally. 
The question is, where do we put our modal content in our component tree, because we dont want it to be visible untill it's presented

The solution here is to use [React portals](https://reactjs.org/docs/portals.html).
Portals provide a first-class way to render children into a DOM node that exists outside the DOM hierarchy of the parent component.

We will also need to make use of [refs](https://reactjs.org/docs/refs-and-the-dom.html). Refs will give us access to functions like 
showModal and closeModal from our component tree and our portal

Here is a [github repo](https://github.com/mayerlench/react-nativescript-modals) that has a working example of modals, bottomsheets and snackbars! Go ahead and test it for yourself!

## Example: Modal
A working example on opening and closing a modal

```tsx
import { AbsoluteLayout, StackLayout } from '@nativescript/core';
import * as React from 'react'
import * as RNS from 'react-nativescript'

// This is needed to keep the reconciler aware that it's the same portal on each render
const portalRoot = new RNS.NSVRoot();
const portalLabel = "Unique label to describe my portal";

export default function Modal() {
    const containerRef = React.useRef(null); // A ref to the container 
    const portalRef = React.useRef(null); // A ref for the react portal

    const handleOpenModal = () => {
        const containerView = containerRef.current?.nativeView as StackLayout
        const portalView = portalRef.current?.nativeView as AbsoluteLayout

        containerView.showModal(portalView, {
            animated: true,
            //fullscreen: true, // uncomment to make modal fullscreen 
            context: {},
            closeCallback: (args) => {
                console.log(`Closed with args`, args);
            }
        });
    }

    const handleCloseModal = () => {
        const portalView = portalRef.current?.nativeView as AbsoluteLayout

        portalView.closeModal({ name: 'react-nativescript is king' })
    }

    return (
        <>
            <stackLayout ref={containerRef}>
                <button text="Open Modal" onTap={handleOpenModal} />
            </stackLayout>

            {/*
                This portal is not rendered below the button.
                It's rendered into a null root, effectively creating a new DOM tree.
            */}
            {RNS.createPortal(
                (
                    <absoluteLayout ref={portalRef}>
                        <stackLayout style={{ margin: 100 }}>
                            <label text="Nice, you created a modal" />
                            <button text="Close Modal" onTap={handleCloseModal} />
                        </stackLayout>
                    </absoluteLayout>
                ),
                portalRoot,
                portalLabel
            )}
        </>
    );
}
```

## Example: Bottomsheets
Similar to creating modal with portals, we can do the same with bottomsheet using a third party library

First, a bit of setup to install the ui-material-bottomsheet
- Run `npm i --save @nativescript-community/ui-material-bottomsheet`
- In your app.ts add the following code

app.ts
```tsx
import { install } from '@nativescript-community/ui-material-bottomsheet'
install()
```

Now create this component and render it
```tsx
import { ViewWithBottomSheetBase } from '@nativescript-community/ui-material-bottomsheet/bottomsheet-common';
import { StackLayout } from '@nativescript/core';
import * as React from 'react'
import * as RNS from 'react-nativescript'

// This is needed to keep the reconciler aware that it's the same portal on each render
const portalRoot = new RNS.NSVRoot();
const portalLabel = "bottomsheet:Unique label to describe my portal";

export default function BottomSheetTest() {
    // A ref to the container 
    const containerRef = React.useRef(null);

    // A ref for the react portal
    const portalRef = React.useRef(null);

    const handleOpenModal = () => {
        const container = containerRef.current!.nativeView as ViewWithBottomSheetBase
        container.showBottomSheet({
            view: portalRef.current!.nativeView,
            context: {},
            closeCallback: (args) => {
                console.log(`Closed with args`, args);
            }
        });
    }

    const handleCloseModal = () => {
        const portalView = portalRef.current?.nativeView as StackLayout

        portalView.closeBottomSheet({ name: 'react-nativescript is king' })
    }

    return (
        <>
            <stackLayout ref={containerRef}>
                <button text="Open bottom sheet" onTap={handleOpenModal} />
            </stackLayout>
            {/*
                This portal is not rendered below the button.
                It's rendered into a null root, effectively creating a new DOM tree.
            */}
            {
                RNS.createPortal(
                    (
                        <stackLayout ref={portalRef} style={{ margin: 100 }}>
                            <label text="This is a bottom sheet!" />
                            <button text="Close Bottom Sheet" onTap={handleCloseModal} />
                        </stackLayout>
                    ),
                    portalRoot,
                    portalLabel
                )
            }
        </>
    );
}
```

## Example: Snackbars
Heres another example of using a third party libary to display a snackbar. 

This snackbar will display anchored above a view that will be passed to it. Since we want the snackbar to be on bottom of screen, we will use the view from our parent component's ref and use [forwardRef](https://reactjs.org/docs/forwarding-refs.html) to pass it to child component.

First, a bit of setup to install the ui-material-snackbar
- Run `npm i --save @nativescript-community/ui-material-snackbar`

Create this component 
```tsx
import * as React from "react";
import { SnackBar } from '@nativescript-community/ui-material-snackbar';

const snackbar = new SnackBar();

export const SnackBarTest = React.forwardRef((props, ref: any) => {

    function showSimpleSnackbar() {
        const view = ref.current?.nativeView

        snackbar.action({
            actionText: `I'm a simple snackbar`,
            message: 'This is a snack',
            view
        }).then(result => console.log('Simple Snackbar:', result));
    }

    return (
        <button text="Show Snack" onTap={showSimpleSnackbar} />
    );
})
```

In your parent component, import the snackbar component and pass it a ref
```tsx
import * as React from "react";
import { StyleSheet } from "react-nativescript";
import Modal from "./Modal";
import BottomSheet from "./BottomSheet";
import { SnackBarTest } from "./SnackBar";

export function HomeScreen() {
    const containerRef = React.useRef(null)
    return (
        <flexboxLayout style={styles.container} ref={containerRef}>
            <Modal />
            <BottomSheet />
            <SnackBarTest ref={containerRef} />
        </flexboxLayout>
    );
}

const styles = StyleSheet.create({
    container: {
        height: "100%",
        flexDirection: "column",
        justifyContent: "center",
    }
});
```
