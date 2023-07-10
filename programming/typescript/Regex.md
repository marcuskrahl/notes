
## Matching Letters and Digits

Prefer:
```ts
/^\p{Letter}+\p{Number}$/u
```

- The u flag at the and indicates Unicode support. 
- This will pickup letters and numbers as defined in the language. 