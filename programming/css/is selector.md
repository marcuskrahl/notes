- usually used to avoid repeating css statements
- always assumes [[specificity]] of the highest [[selector]] inside
- related to [[where selector]]

Example:

```css
a[href]:is(:hover, :active, .selected) {
	color: cornflowerblue;
}
```

