
## Inputs are set for route parameters

- Starting with Angular 16

```typescript
{
  route: "/application/:id",
  data: {
    short: true
  }, 
  resolve: {
    hasPermission: () => of(true)
  }
}
```

can be accessed via

```typescript
class ApplicationComponent {
	@Input() id: string;
	@Input() short: boolean;
	@Input() hasPermission: boolean;
}
```