---
id: node-roles
title: Node Roles
---
<!-- contributors: [shirakaba] -->

NativeScript Core includes a number of complex components which accept children acting in a variety of different roles.

React NativeScript therefore provides a `nodeRole` property so that you can make it explicit what role each given child serves.

## Example: RadSideDrawer

RadSideDrawer takes two children. One child is the Main Content, while the other is the Drawer Content.

```tsx
import * as React from "react";

// NOTE: RadSideDrawer is a non-core component (provided by a plugin), so there would be a necessary registration step for it at the start of the app.

<radSideDrawer>
  <stackLayout nodeRole="mainContent">
    <label>This is the Main Content</label>
  </stackLayout>

  <stackLayout nodeRole="drawerContent">
    <label>This is the Drawer Content</label>
  </stackLayout>

  <stackLayout>
    <label>So what happens with this child?</label>
  </stackLayout>
</radSideDrawer>
```

The `nodeRole` informs React NativeScript to append children in the following manner:

```tsx
// In the case of nodeRole="mainContent":
sideDrawer.mainContent = child;

// In the case of nodeRole="drawerContent":
sideDrawer.drawerContent = child;

// In the case of no nodeRole, if a suitable guard has been set up for this
// component, then ideally it would no-op with an informative message:
console.warn(`No nodeRole was specified, so unable to add this child.`);

// But if not, the default behaviour may happen:
sideDrawer._addChildFromBuilder(child.constructor.name, child);
```

The result of `sideDrawer._addChildFromBuilder(child.constructor.name, child)` is indeterministic; it depends how that method has been implemented in the NativeScript Core component. In some cases (such as many single-child components), it actually gives a desirable result. But in many cases, it may result in an error being thrown, or a no-op, or one of the children with an explicit nodeRole being replaced by this child.

Fortunately there aren't too many of these components, and hopefully a warning will appear in the console to tell you if ever a `nodeRole` is missing. The best I can advise is to read the documentation carefully!

