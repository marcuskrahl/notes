


# Loading images

Prevent long loading time, choose most appropriate format based on browser support, show placeholder
- `loading=lazy` => Only load image when user scrolls to it

```html
<style>
    img { max-width: 100%; height: auto; }
</style>

<picture>
    <source sizes="(max-width: 600px) 100vw, 600px"
        srcset="donuts-1920w.avif 1920w,
                donuts-1280w.avif 1280w,
                donuts-640w.avif 640w" type="image/avif">
    <source sizes="(max-width: 600px) 100vw, 600px"
        srcset="donuts-1920w.jpg 1920w,
                donuts-1280w.jpg 1280w,
                donuts-640w.jpg 640w" type="image/jpeg">

    <img loading="lazy"
         decoding="async"
         height="1100" width="2000"
         src="donuts.png"
         style="background-size: cover; background-image: url('placeholder.png')">

</picture>
```

Source: https://www.smashingmagazine.com/2021/04/humble-img-element-core-web-vitals/
