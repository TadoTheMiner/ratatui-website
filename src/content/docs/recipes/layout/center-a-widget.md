---
title: How to Center Widgets
sidebar:
  order: 2
  label: Center a Widget
---

## Problem

You want to center a widget within some area of your TUI's layout.

## Solution

To center a widget in any area, create a [`Rect`] that is centered within the area. You can
calculate the x and y positions of the widget by subtracting the widget width and height from the
enclosing area's width and height, respectively, and dividing by 2.

More simply, you can use the `.centered_vertically()` and `.centered_horizontally()` methods on rect
### Centering horizontally

```rust
{{ #include @code/recipes/how-to-misc/src/layout.rs:imports }}

{{ #include @code/recipes/how-to-misc/src/layout.rs:horizontal }}
```

### Centering vertically

```rust
{{ #include @code/recipes/how-to-misc/src/layout.rs:imports }}

{{ #include @code/recipes/how-to-misc/src/layout.rs:vertical }}
```

### Centering both horizontally and vertically

You can use the `.centered` method to get a centered `Rect`.

```rust collapse={1-13}
{{ #include @code/recipes/how-to-misc/src/layout.rs:center }}
```

### Centering a widget

You can use these methods to draw any widget centered on the containing area.

```rust
{{ #include @code/recipes/how-to-misc/src/layout.rs:render }}
```

### Popups

A common use case for this feature is to create a popup style dialog block. For this, typically,
you'll want to use the [`Clear`] widget to clear the popup area before rendering your content to it.
The following is an example of how you might do that:

```rust
{{ #include @code/recipes/how-to-misc/src/layout.rs:render_popup }}
```

## Summary

The [`Layout`] struct provides a simple way to center a widget in a terminal. You can use the
`Horizontal` and `Vertical` layouts to center a widget on the x and y axes, respectively. You can
also use the `Flex` enum to specify the alignment of the widget within the containing area. There
are more advanced layout options available in the [`Layout`] struct but not covered in this recipe,
which you can use to create more complex layouts.

:::note

There is no method for vertically aligning text within an area yet. We recommend prewrapping the
text using the [textwrap crate] and then using the line count to work out where to render the text.

:::

Full code for this recipe is available in the website repo at:
<https://github.com/ratatui/ratatui-website/blob/main/code/recipes/src/layout.rs>

## See also

There are several third party widget libraries for making popups easy to use:

- [tui-popup](https://crates.io/crates/tui-popup)
- [tui-confirm-dialog](https://crates.io/crates/tui-confirm-dialog)

[textwrap crate]: https://crates.io/crates/textwrap
[`Rect`]: https://docs.rs/ratatui/latest/ratatui/struct.Rect.html
[`Layout`]: https://docs.rs/ratatui/latest/ratatui/layout/struct.Layout.html
[`Flex`]: https://docs.rs/ratatui/latest/ratatui/layout/enum.Flex.html
