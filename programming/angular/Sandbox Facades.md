https://blog.simplified.courses/smart-components-ui-components-and-sandbox-facades-in-angular/

## Goal

- divide feature libs (containing smart and dump components) from actual used services

## Implementation

```ts
@Injectable()
export class SandboxFacade {
	public readonly users$ = this.userService.getUsers();
	public addProduct(product: Product): Observable<Product> {
		return this.productService.add(product);
	}
}
```

```ts
@Component()
export class SmartComponent {

	constructor(private facade: SandboxFacade) {
	//facade is the only injected service
	//do something with exposed facade
	}
} 
```