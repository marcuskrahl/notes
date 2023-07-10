
## `prefer-color-scheme`

- renders css based on users preference in operating system
- can also be used to dynamically load css `<link media="(prefers-color-scheme:dark)" rel="stylesheet" href="dark.css" />`

## `color-scheme`

- force the default browser styling into light or dark mode
	- benefit: this will style all elements even when there is no custom css rule, also scrollbars, ...
- e.g. `color-scheme: dark`
- can also be set via meta tag: `<meta name="color-scheme" content="light dark" />`
- Colors of the scheme can be used in css properties:
```css
section {
  background-color: Canvas;
  color: CanvasText;
} 
```
- more colors - see: https://www.w3.org/TR/css-color-4/#css-system-colors