# Auto break words

```css
.break-word {
    overflow-wrap: break-word;
    word-wrap: break-word;
    -ms-word-break: break-all;
    word-break: break-word;
    -ms-hyphens: auto;
    -moz-hyphens: auto;
    -webkit-hyphens: auto;
    hyphens: auto;
}
```

# Prevent 300ms delay on mobile

```css
a, button {
    touch-action: manipulation;
}
```

# detect element layout changes at runtime

- [`ResizeObserver`](https://developer.mozilla.org/en-US/docs/Web/API/ResizeObserver)
- triggers event handler when element dimensions change
- provides values of new dimensions
