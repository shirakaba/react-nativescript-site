---
id: Frame
title: Frame
apiRef: https://docs.nativescript.org/api-reference/classes/_ui_frame_.frame
contributors: [rigor789, PieterHartzer]
---

`<$Frame>` is a UI component used to display [`<$Page>`](/en/docs/elements/components/page) elements. Every app needs at least a single `<$Frame>`  element, usually set as the root element.

See also:

* [Official top-level documentation](https://docs.nativescript.org/ui/components/frame)
* [Detailed API specification](https://docs.nativescript.org/api-reference/classes/_ui_frame_.frame)

---

<!-- #### A single root Frame

If you are migrating from nativescript 3.x and want to preserve the old behavior, the following snippet in your entry file will create a root frame and render your default page.

```js
new Vue({
  render: h => h('Frame', [ h(HomePageComponent) ])
})
``` -->

#### Multiple Frames

If you need to create multiple frames, you can do so by wrapping them in a Layout, for example if you want to have 2 frames side-by-side

```tsx
<$GridLayout columns={[new ItemSpec(1, "star"), new ItemSpec(1, "star")]} rows={[]}>
  <$Frame col={0}/>
  <$Frame col={1}/>
</$GridLayout>
```

#### A frame with a default page

```tsx
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
      <$Frame ref={forwardedRef}>
        <$Page ref={this.pageRef}>
          <$ActionBar title="Default Page Title" />
          <$GridLayout>
            <$Label text="Default Page Content" />
          </$GridLayout>
        </$Page>
      </$Frame>
    );
  }
}
```

#### A frame with a default page from an external component

```tsx
import HomePage from './HomePage';

<$Frame>
  <HomePage />
</$Frame>
```

## Native component

| Android | iOS |
|---------|-----|
| [`org.nativescript.widgets.ContentLayout`](https://github.com/NativeScript/tns-core-modules-widgets/blob/master/android/widgets/src/main/java/org/nativescript/widgets/ContentLayout.java) | [`UINavigationController`](https://developer.apple.com/documentation/uikit/uinavigationcontroller)
