# Layout Primitive Components
Pure HTML and CSS, no JavaScript.

Rather than controlling layout properties via class name, it is possible to safely use attributes on any element with a [valid custom-element name](https://html.spec.whatwg.org/#valid-custom-element-name), such as `x-grid`, even if that element is not defined in the CustomElementRegistry.

By leveraging [`[attr~=value]`](https://developer.mozilla.org/en-US/docs/Web/CSS/Attribute_selectors) CSS selectors, one can construct complex responsive utilities based on whitespace-separated attributes. Combining these two techniques results in a powerful, expressive API that is simple to use and requires JavaScript or SSR considerations.

## Responsive Attribute
A responsive attribute consists of a value (most often an `<integer>`), and one or more responsive values prefixed by a breakpoint and colon (`sm:`, `md:`, `lg:`, `xl:`).

```html
<x-grid gap="4 sm:8 md:16 lg:24 xl:32" />
```

## `x-grid`

**Attributes**

- `cols` is a responsive attribute representing the number of columns per row at a given breakpoint.
- `gap` is a responsive attribute which accepts an `<integer>` following Tailwind's [default spacing scale](https://tailwindcss.com/docs/customizing-spacing#default-spacing-scale) (but named after the pixel values rather than the scale name). It applies both `row-gap` and `column-gap` properties. 
- `dense` is a boolean attribute which enables `dense` packing inside of the grid.

**Custom Properties**
- `--row-height` determines the height of all rows in the grid.
- `--col-ratio` applies an `aspect-ratio` to `x-col` elements as an alternative to setting `--row-height`.
- `--row-gap` applies a specific `row-gap` value.
- `--col-gap` applies a specific `column-gap` value.

## `x-col`

**Attributes**

- `span` is a responsive attribute which accepts `1-12|row`, representing the number of columns to span. Defaults to `1`.
- `start` is a responsive attribute representing the column on which to start. Defaults to `auto`.
- `end` is a responsive attribute representing the column on which to end. Defaults to `auto`. Note that this `<integer>` represents the *end* track of a column (so `end="8"` will stretch up until column 9.)
