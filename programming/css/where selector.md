- a [[selector]]
-  always has [[specificity]] of 0
- can be used as browser reset because of 0 [[specificity]]
- related to [[is selector]]


Example:
```css
/* normal usage */
div:where(.red) {
  background-color: red;
}

/* reset usage */
:where(ul, ol) {
  list-style-type: none;
}
```