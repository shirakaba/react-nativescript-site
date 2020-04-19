---
id: Frame
title: Frame
---
<!-- contributors: [shirakaba, rigor789, PieterHartzer] -->

`<frame>` is a UI component used to display [`<page>`](/en/docs/elements/components/page) elements. Every app needs at least a single `<frame>`  element, usually set as the root element.

See also:

* [Official top-level documentation](https://docs.nativescript.org/ui/components/frame)
* [Detailed API specification](https://docs.nativescript.org/api-reference/classes/_ui_frame_.frame)

---

#### Multiple Frames

If you need to create multiple frames, you can do so by wrapping them in a Layout, for example if you want to have 2 frames side-by-side:

```tsx
import * as React from "react";

<gridLayout columns={[new ItemSpec(1, "star"), new ItemSpec(1, "star")]} rows={[]}>
  <frame col={0}/>
  <frame col={1}/>
</gridLayout>
```

#### A frame with a default page

```tsx
import * as React from "react";
import { Frame } from "@nativescript/core";

interface Props {
  forwardedRef: React.RefObject<Frame>;
}

class AppContainer extends React.Component<Props, State> {
  private readonly pageRef: React.RefObject<Page> = React.createRef<Page>();

  componentDidMount() {
    const frame: Frame = this.props.forwardedRef.current!;
    frame.navigate({
      create: () => {
        const page: Page = this.pageRef.current!;
        return page;
      }
    });
  }

  render() {
    const { forwardedRef } = this.props;

    return (
      <frame ref={forwardedRef}>
        <page ref={this.pageRef}>
          <actionBar title="Default Page Title" />
          <gridLayout>
            <label text="Default Page Content" />
          </gridLayout>
        </page>
      </frame>
    );
  }
}
```

#### A frame with a default page from an external component

```tsx
import * as React from "react";
import HomePage from './HomePage';

<frame>
  <HomePage />
</frame>
```

## Native component

| Android | iOS |
|---------|-----|
| [`org.nativescript.widgets.ContentLayout`](https://github.com/NativeScript/tns-core-modules-widgets/blob/master/android/widgets/src/main/java/org/nativescript/widgets/ContentLayout.java) | [`UINavigationController`](https://developer.apple.com/documentation/uikit/uinavigationcontroller)
