# Unit Testing


## Automatically create typed spies

Definition:

```typescript
type SpyOf<T> = T &
  {
    [k in keyof T]: T[k] extends (...args: any[]) => infer R ? jest.Mock<R> : T[k];
  };

export function autoSpy<T>(obj: new (...args: any[]) => T): SpyOf<T> {
  const res: SpyOf<T> = {} as any;

  const keys = Object.getOwnPropertyNames(obj.prototype);
  keys.forEach((key) => {
    res[key] = jest.fn(key);
  });

  return res;
}
```

Usage:
```typescript
describe('AuthorComponent', () => {
  it('should do display the author when found by id', () => {
    const service = autoSpy(ServiceMock);
    service.getAuthor.mockReturn({ name: 'me' });
    const c = new AuthorComponent(service);
    c.ngOnInit();
    expect(c.author).toEqual({ name: 'me' });
  });
});
```

Source: https://indepth.dev/posts/1240/create-your-angular-unit-test-spies-automagically 

## SIFERS

SIFERS (Simple Injectable Functions Explicitly Returning State) is a way to structure unit tests. Instead of `beforeEach` calls each test manually invokes a setup method.

Source: https://medium.com/@kolodny/testing-with-sifers-c9d6bb5b362

### Benefits

- Better typing of variables
- No need to define top level scope variables
- Explicit passing of values -> when changing default behaviour
- Allows proper nesting of setup code

