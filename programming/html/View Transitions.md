- Transitions between pages, even for [[Multi Page Applications]] 

```html
<meta name="view-transition" content="same-origin" />
```
- Elements with same CSS `view-transition-name` morph into each other
- Control transition effect with pseudo elements:
```css
/* Old stuff going out */
::view-transition-old(hero) {
  animation: fade 0.2s linear forwards;
}

/* New stuff coming in */
::view-transition-new(hero) {
  animation: fade 0.3s linear reverse;
}

@keyframes fade {
  from {
    opacity: 1;
  }
  to {
    opacity: 0;
  }
}
```