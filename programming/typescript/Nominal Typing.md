# Nominal Typing

Sometimes we want to define types, which share the same data type, e.g. string, but have a different meaning.

In nominal typed languages we can do this easily.

TypeScript is structural typed so we cannot do this out of the box.

## Nominal Utility Class

Definition: 

```typescript
export type Nominal<Name extends string, Tag, Type = {}> = Type & {
    readonly __tuid__: { name: Name; tag: Tag };
};
```

Usage:

```typescript
export type BooleanFieldName = Nominal<'BooleanFieldName', { readonly id: unique symbol }, string>;
export type ChoiceFieldName = Nominal<'ChoiceFieldName', { readonly id: unique symbol }, string>;


let booleanField: BooleanFieldName = 'MyField' as BooleanFieldName;
let choiceField: ChoiceFieldName = 'OtherField' as ChoiceFieldName;

booleanField = choiceField; //error
booleanField = 'foo'; //error

booleanField === 'MyField'; // true
console.log(`${booleanField}`); //works as expected

```


## Libraries
- https://github.com/gcanti/newtype-ts
- https://github.com/unional/type-plus#nominal-type