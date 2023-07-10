
No custom code neccessary: 

```typescript
import { takeUntilDestroyed } from '@angular/core/rxjs-interop';

export class Component implements OnInit{
  data;

  constructor(private service: DataService) {
    this.service.getData()
      .pipe(takeUntilDestroyed())
      .subscribe(response => this.data = response)
  }
}
```