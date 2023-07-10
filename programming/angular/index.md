

# Content Projection

```html
<!-- my.component.html -->
<div>
    <ng-content></ng-content>
    <ng-content select=".rest"></ng-content>
</div>

<!-- Usage --> 
<my-component>
    <span class="rest">Going into some other slot</span> 
    <p>This is the thing I want to project</p>
</my-component>

<!-- ngProjectAs - use this when projected content should not be wrapped in an element -->

<my-component>
    <ng-container ngProjectAs=".rest">Some plain text which is directly inserted</ng-container>
</my-component>
```


# Template tricks

## `ngNonBindable`

Disable interpolation for this element

```html
<div ngNonBindable>The following braces will be ignored {{ this is valid content }}</div>
```

## `ngPreserveWhitespaces`

Angular Compiler will not remove whitespace automatically

```html
<span ngPreserveWhitespace>     The spaces infront are being kept </span>
```

## `&ngsp;`

Same as non breaking whitespace but this one is being kept by angular


```html
<span>We really need a break between this&ngsp;and this</span>
```

## Alternative Syntax for defining bindings

```html
<my-component
  #component
  [@animation]=”animation”
  [value]=”value”
  [(banana)]=”twoWayBoundValue”
  (output)=”onOutput($event)”
  (click)=”onClick()”
></my-component>

<!-- alternative -->
<my-component
  ref-component
  bind-animate-animation=”animation”
  bind-value=”value”
  bindon-banana=”twoWayBoundValue”
  on-output=”onOutput($event)”
  on-click=”onClick()”
></my-component>
```


## APP_INITIALIZER

DI token to do something when the Angular app is initializing, e.g. before any Component is loaded. 
This may also do async calls which block further initialization.
May be used for loading a config file.

```typescript
function initializeAppFactory(httpClient: HttpClient): () => Observable<any> {
 return () => httpClient.get("https://someUrl.com/api/user")
   .pipe(
      tap(user => { ... })
   );
}

@NgModule({
  imports: [BrowserModule, HttpClientModule],
  declarations: [AppComponent],
  bootstrap: [AppComponent],
  providers: [{
    provide: APP_INITIALIZER,
    useFactory: initializeAppFactory,
    deps: [HttpClient],
    multi: true
  }]
})
export class AppModule {}
```