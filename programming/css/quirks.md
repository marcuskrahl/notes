# `overflow-x: auto` and `overflow-y: visible`

Also vice versa. When one of the properties is set to `scroll`, `auto` or `hidden`, the other property cannot be set to `visible` per CSS Standard as this would lead to poor layouting performance when scrolling the container.
