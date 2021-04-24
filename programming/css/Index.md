# CSS


## Frameworks

### Bootstrap

### [Tailwind CSS](https://tailwindcss.com)

- mostly very specific classes to replace inline styling
- some of the definitions may be reused in other projects, e.g. shadow definitions
- definitions may be grouped into components, e.g. brand button

## Preprocessors

- Sass
- Less

## Best Practices

- BEM
- SMACSS

## Linting

- [Stylelint](https://stylelint.io)

## [Houdini](https://ishoudinireadyyet.com)

- Extension of browser APIs to allow new concepts for existing CSS attributes
- Highly performant as code is only run when the browser needs to rerender an element. Most rendering is done on GPU

### Paint API

- A replacement for everywhere where an image may be set, e.g. border-image, background-image, masks, ...
- Registering: `CSS.paintWorklet.addModule('myimage.js')`
- Usage: `border-image: paint(myimage)`
- `myimage.js` defines a class with a `paint` method whose parameters are a canvas context to draw on, the element dimensions and a style map containing set css variables (if requested by the class via `inputProperties`)
- The passed CSS variables may be animated, but then they need to be defined via `CSS.registerProperty`

### Layout API

- Allows extension of the `display` attribute
- Registering: `CSS.layoutWorklet.addModule('mylayout.js')`
- Usage: `display: layout(mylayout)`
- `mylayout.js` defines a class with a `layout` method whose parameters are the elements dimensions, the border dimensions, children to draw and a style map containing set css variables (if requested by the class via `inputProperties`) 
- The method returns the elements layout (it can grow in height when necessary) and the dimensions and positions of its children
- Children may be given dimensions using `const childFragment = await child.layoutNextFragment()` giving the child concrete dimensions. The dimensions may be restricted to an allowed area or even be set to fixed values.
- The fragment of the child may then be positioned via `inlineOffset` and `blockOffset`
- It seems to be necessary to layout children in the order in which they appear in the passed array. Otherwise layouting seems to not be possible. 
