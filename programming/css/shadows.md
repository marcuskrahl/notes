# Shadows

- Light should come from a single source in a page
  - Most often top and slightly to the left
  - Use same ratio of horizontal and vertical offset on whole page
- Move object towards the user, by increasing top and left offset, increasing blur and  decreasing opacity
  - e.g `box-shadow: 2.0px 4.0px 4.0px hsl(0deg 0% 0% / 0.44);` vs `box-shadow: 6.0px 12.0px 12.0px hsl(0deg 0% 0% / 0.31);` 
- Define shadow color based on background color 
  - match hue but decrease saturation and lightness

## Layering

- Use multiple layers of shadow instead of a single layer to create more lifelike shadows
- Online tool to create layers: https://shadows.brumm.af/

```css
box-shadow: 
      0 1px 1px hsl(0deg 0% 0% / 0.075),
      0 2px 2px hsl(0deg 0% 0% / 0.075),
      0 4px 4px hsl(0deg 0% 0% / 0.075),
      0 8px 8px hsl(0deg 0% 0% / 0.075),
      0 16px 16px hsl(0deg 0% 0% / 0.075)
```

## `drop-shadow`

- GPU accelerated instead of CPU bound
- follows contour of HTML element

