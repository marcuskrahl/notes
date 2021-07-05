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


## Content sizing

### Width

- `width: auto`: take as much horizontal space as possible
- `width: max-content`: take as much space needed for the content which may overflow the parent container
- `width: min-content`: take as much space needed for the largest element in the content, e.g. the largest word

- `width: fit-content`: This is the same as `width: auto; min-width: min-content; max-width: max-content`. The content stays inside the box and shrinks if necessary. And takes at most content width horizontal space
    - this does not work in flexbox or grid environments
- `fit-content(200px)`: This may be used in the definition of grid templates. It is equal to `min(min(max-content, available-size), max(min-content, 200px))`
    - take the available space or the space needed for its content whichever is smaller
    - also take the space needed for a single content item, but at least 200px
    - set the final width to whichever value is smaller 
    - this allows grid elements to take a smaller space than available, e.g. to make room for other elements

