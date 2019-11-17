---
id: SearchBar
title: SearchBar
contributors: [shirakaba, MisterBrownRSA, rigor789, ikoevska]
---

`<$SearchBar>` is a UI component that provides a user interface for entering search queries and submitting requests to the search provider.

See also:

* [Official top-level documentation](https://docs.nativescript.org/ui/components/search-bar)
* [Detailed API specification](https://docs.nativescript.org/api-reference/classes/_ui_search_bar_.searchbar)

---

```tsx
<$SearchBar hint="Search hint" text="searchPhrase" onTextChange={onTextChanged} onSubmit={onSubmit} onClose={onClose} />
```

[> screenshots for=SearchBar <]

## Props

| Name | Type | Description |
|------|------|-------------|
| `hint` | `string` | Sets placeholder text for the input area.
| `text` | `string` | Sets the value of the search query.
| `textFieldBackgroundColor` | `Color` | Sets the background color of the input area.
| `textFieldHintColor` | `Color` | Sets the color of the placeholder text.
| `onTextChange` | `(args: `[`EventData`](https://docs.nativescript.org/api-reference/interfaces/__nativescript_core_.eventdata)`) => void` | Emitted when the text is changed.
| `onSubmit` | `(args: `[`EventData`](https://docs.nativescript.org/api-reference/interfaces/__nativescript_core_.eventdata)`) => void` | Emitted when the search input is submitted.
| `onClose` | `(args: `[`EventData`](https://docs.nativescript.org/api-reference/interfaces/__nativescript_core_.eventdata)`) => void` | Emitted when the search bar is closed.
| `onClear` | `(args: `[`EventData`](https://docs.nativescript.org/api-reference/interfaces/__nativescript_core_.eventdata)`) => void` | Emitted when the current search input is cleared through the **X** button in the input area.

## Native Component

| Android | iOS |
|---------|-----|
| [`android.widget.SearchView`](https://developer.android.com/reference/android/widget/SearchView.html)	| [`UISearchBar`](https://developer.apple.com/documentation/uikit/uisearchbar)
