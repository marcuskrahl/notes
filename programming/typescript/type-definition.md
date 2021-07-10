# Type Definition


## Avoid defining types twice

We do not want to define same contexts all over again if we can extract information from a base type. This especially helps when adding new properties to types.

Source: https://fettblog.eu/low-maintenance-types-typescript/

```typescript
const defaultOptions = {
    foo: true,
    bar: 42,
    baz: 'test'
};

function parseOptions(options: Partial<typeof defaultOptions>) {
    const mergedOptions = {...defaultOptions, ...options};
}
```

```typescript
const categories = [
    "foo",
    "bar",
    "baz"
] as const;

type Category = (typeof categories)[number]; // "foo" | "bar" | "baz"
```


```typescript
type ToyBase = {
  name: string;
  price: number;
  quantity: number;
  minimumAge: number;
};

type BoardGame = ToyBase & {
  kind: "boardgame";
  players: number;
}

type Puzzle = ToyBase & {
  kind: "puzzle";
  pieces: number;
}

type Doll = ToyBase & {
  kind: "doll";
  material: "plastic" | "plush";
}

type Toy = BoardGame | Puzzle | Doll;


// use types in context

type ToyKind = Toy["kind"]; // "boardgame" | "puzzle" | "doll"

//helper
type GetKind<Group, Kind> = Extract<Group, { kind: Kind }>

type GroupedToys = {
    [Kind in ToyKind as `${Kind}s`]: GetKind<Toy, Kind>[]
};


//result
type GroupedToys = {
    boardgames: BoardGame[];
    puzzles: Puzzler[];
    dolls: Doll[];
}
```
