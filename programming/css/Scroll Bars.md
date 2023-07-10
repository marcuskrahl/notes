When scroll bars are shown for overflow, they shrink the width of the content of an element (between border and padding)

This space can be reserved even if there is no scrollbar yet, with `scrollbar-gutter: stable`
Then some whitespace is reserved where a scrollbar might appear in the future
This prevents layout shifts
`scrollbar-gutter: stable both-edges;` to symmetrically reserve space (scrollbar may be shown either left or right of the element)