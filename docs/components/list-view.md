---
id: ListView
title: ListView
---
<!-- contributors: [shirakaba, MisterBrownRSA, rigor789, eddyverbruggen, ikoevska] -->

`<ListView>` is a UI component that shows items in a vertically scrolling list. To set how the list shows individual items, you can specify different templates using a combination of the `cellFactories` rendering method and the `itemTemplateSelector`.

Importantly, ListView is a "virtual list", i.e. it uses cell recycling (just like the native iOS/Android lists). This has implications for the behaviour of the ListView's cells, which will be detailed in this article.

See also:

* [Official top-level documentation](https://docs.nativescript.org/ui/components/list-view)
* [Detailed API specification](https://docs.nativescript.org/api-reference/classes/_ui_list_view_.listview)

---

## Using `<ListView>` with a single template

```tsx
import * as React from "react";
import { ListView } from "react-nativescript";
import { ItemEventData } from "@nativescript/core";

type MyItem = { text: string };;

const cellFactory = (item: MyItem) => {
  return <label text={item.text} />;
};

const onItemTap = (args: ItemEventData) => {
  const index: number = args.index;
  const item: MyItem = items[index];
  console.log(`Tapped item index ${index}: "${text}".`);
};

function SingleTemplate(props: { items: MyItem[] }){
  /**
   * If cellFactory or onItemTap have a dependency on any props,
   * you can of course bring them into this scope.
   */
  return (
    <ListView
      items={items}
      cellFactory={cellFactory}
      onitemTap={onItemTap}
    />
  );
}
```

`cellFactory` is the function that renders a list cell, given an input item.

`onitemTap` runs when tapping a cell. For handling taps on list items, please use this prop rather than adding event listeners on the individual items themselves, as event listeners in the cells may not be reliable due to cell recycling.

---

<!-- [> screenshots for=ListView <] -->

## Using `<ListView>` with multiple templates

If you want to display several different formats of cell (i.e. with different UI element hierarchies) in the same list, don't use conditional rendering, as it is not performant with respect to the cell recycling that ListViews perform.

Instead, use templates. This allows React to focus on updating individual properties on elements rather than adding/removing UI elements from the tree (which is memory-intensive, due to rapid re-instantiation of elements).

See [Alexander Vakrilov's brilliant article](https://medium.com/@alexander.vakrilov/faster-nativescript-listview-with-multiple-item-templates-8f903a32e48f) on why templates optimise ListView performance when multiple different UI trees are required.

```tsx
import * as React from "react";
import { ListView } from "react-nativescript";
import { ItemEventData } from "tns-core-modules/ui/list-view/list-view";

type MyEvenItem = { textEven: string };
type MyOddItem = { textOdd: string };
type MyItem = MyEvenItem | MyOddItem;

const items: MyItem[] = [{ textEven: "hi" }, { textOdd: "hi" }];

function itemTemplateSelector(item: MyItem, index: number, items: MyItem[]): string {
  return index % 2 === 0 ? "even" : "odd";
}

const evenCellFactory = (item: MyOddItem) => {
  return <label text={item.textEven} color={"green"}/>;
};

const oddCellFactory = (item: MyOddItem) => {
  return <label text={item.textOdd} color={"orange"}/>;
};


const cellFactories = new Map([
  [
    "odd",
    {
      placeholderItem: {
        text: "some odd text"
      },
      cellFactory: oddCellFactory
    }
  ],

  [
    "even",
    {
      placeholderItem: {
        text: "some even text"
      },
      cellFactory: evenCellFactory
    }
  ],
]);

const onItemTap = (args: ItemEventData) => {
  const index: number = args.index;
  const item: MyItem = items[index];
  const isEven: boolean = itemTemplateSelector(index) === "even";
  const itemText: string = isEven ?  
    (item as MyEvenItem).textEven :
    (item as MyOddItem).textOdd;

  console.log(`Tapped item index ${index} (${isEven ? "even" : "odd"}): "${itemText}".`);
};

function MultipleTemplates(props: { items: MyItem[] }){
  /**
   * If any of the functions have a dependency on any props,
   * you can of course bring them into this scope.
   */
  return (
    <ListView
      items={items}
      itemTemplateSelector={itemTemplateSelector}
      cellFactories={cellFactories}
      onitemTap={onItemTap}
    />
  );
}
```

`itemTemplateSelector` must return the name of a template, which must match a key in the Map that you pass into the `cellFactories` prop.

`cellFactories` takes a `Map<string, { placeholderItem: any, cellFactory: CellFactory }>`. The string key should be matched by `itemTemplateSelector`, and the cellFactory is written just as it is in the single-template example above. `placeHolderItem` is the item that React NativeScript will use to intialise the cell before later reconciling it with an actual item from your list of items. The placeholder item should exactly match the schema of the item you'll be handling in `cellFactory`.

## Updating the list of items in the `<ListView>`

To update the list of items in the ListView, it is best to use NativeScript's ObservableArray for the list, as this will fire events at the ListView to prompt its model to update. This avoids React re-rendering the ListView altogether (no the below method will not trigger a list re-render).

```tsx
import * as React from "react";
import { ListView } from "react-nativescript";
import { ItemEventData, ObservableArray } from "@nativescript/core";

type MyItem = { text: string };;
const itemsToLoad: number = 100;
const items: ObservableArray<MyItem> = new ObservableArray(
    [...Array(itemsToLoad).keys()]
    .map((value: number) => ({ text: `Item ${value.toString()}` }))
  );
let loadMoreTimeout?: any;

const cellFactory = (item: MyItem) => {
  return <label text={item.text} />;
};

const onItemTap = (args: ItemEventData) => {
  const index: number = args.index;
  const item: MyItem = items[index];
  console.log(`Tapped item index ${index}: "${text}".`);
};

function SingleTemplate(props: {}){
  const loadMoreRef = React.useRef(true);
  const loadMoreTimeoutRef = React.useRef(undefined);

  React.useEffect(() => {
    clearTimeout(loadMoreTimeoutRef.current!);
  }, []);

  const onLoadMoreItems = (args: ItemEventData) => {
    if(!loadMore.current){
        console.log(`[onLoadMoreItems] debouncing.`);
        return;
    }

    console.log(`[onLoadMoreItems] permitted.`);

    loadMoreTimeoutRef.current = setTimeout(
      () => {
        const itemsToPush: MyItem[] = [];

        for(let i = items.length; i < + items.length + itemsToLoad; i++){
            const lastValueIncremented: number = i;
    
            itemsToPush.push({
                text: `Item ${lastValueIncremented.toString()}`
            });
        }

        items.push(itemsToPush);
        loadMore = true;
      },
      /* Ample time for a (typical) scroll action's inertia to settle, to avoid list jumpiness. */
      750
    );

    loadMore.current = false;
  };

  return (
    <ListView
      items={items}
      cellFactory={cellFactory}
      onitemTap={onItemTap}
    />
  );
}
```

`onLoadMoreItems` runs when a user drags the list down beyond its limits to prompt a reload of the items.

When accessing an item from an ObservableArray, remember to use the `getItem()` method rather than an array accessor.

## Props

| Name | Type | Description |
|------|------|-------------|
| `items` | `Array<any>` | An array of items to be shown in the `<ListView>`.
| `separatorColor` | [`Color`](https://docs.nativescript.org/api-reference/classes/__nativescript_core_.color) | Sets the separator line color. Set to `transparent` to remove it.
| `onItemTap`| `(args: `[`ItemEventData`](https://docs.nativescript.org/api-reference/interfaces/__nativescript_core_.itemeventdata)`) => void` | Emitted when an item in the `<ListView>` is tapped. To access the tapped item, use `items[args.index]`.

## Methods

Note: You must obtain a reference to the underlying NativeScript `ListView` element in order to call these methods.

| Name | Description |
|------|-------------|
| `refresh()` | Forces the `<ListView>` to reload all its items.

## Native component

| Android | iOS |
|---------|-----|
| [`android.widget.ListView`](https://developer.android.com/reference/android/widget/ListView.html) | [`UITableView`](https://developer.apple.com/documentation/uikit/uitableview)
