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
