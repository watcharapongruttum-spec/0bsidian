# Path params
Dynamic value in the path
- Path Parameter
- Using of **:var** and **ActivatedRoute**

```sh
ng g c pages/member/test --skip-tests
```

**app.router.ts**
```ts
 path: 'member',
    component: MemberComponent,
    children: [
      { path: 'list', component: ListComponent },
      { path: 'profile', component: ProfileComponent },
      { path: 'test/:id', component: TestComponent },
    ],
```

**test.component.ts**
```ts
import { Component } from '@angular/core';
import { CommonModule } from '@angular/common';
import { ActivatedRoute } from '@angular/router';

@Component({
  selector: 'app-test',
  standalone: true,
  imports: [CommonModule],
  templateUrl: './test.component.html',
  styleUrl: './test.component.scss',
})
export class TestComponent {
  id = '';
  constructor(private activeatedRoute: ActivatedRoute) {}

  ngOnInit() {
    this.id = this.activeatedRoute.snapshot.paramMap.get('id') || '';
  }
}
```

![[Pasted image 20231121202653.png]]

**test.component.html**
```html
<p>test works!</p>
{{this.id}}
```

![[Pasted image 20231121202001.png]]

# Query params
Variable in the url

**test.component.ts**
```ts
export class TestComponent {
  id = '';
  constructor(private activeatedRoute: ActivatedRoute) {}

  ngOnInit() {
    this.id = this.activeatedRoute.snapshot.paramMap.get('id') || '';
    this.name = this.activeatedRoute.snapshot.queryParamMap.get('name') || 'No Name';
  }
}
```

**test.component.html**
```html
<p>test works!</p>
{{this.id}} <br>
{{this.name}}
```

![[Pasted image 20231121203025.png]]

![[Pasted image 20231121203051.png]]

# Sending Params 

### RouterLink

add new route
**app.router.ts**
```ts
 {
    path: 'member',
    component: MemberComponent,
    children: [
      { path: 'list', component: ListComponent },
      { path: 'profile', component: ProfileComponent },
      { path: 'test/:id', component: TestComponent },
      { path: 'test', component: TestComponent },
    ],
  },
```

**member.component.html**
```html
<button routerLink="/member/test" [queryParams]="{name:'Aj.M'}">Test QueryParams</button>
```

![[Pasted image 20231121204509.png]]

### Programmatically

add button
**member.component.html**
```html
<button routerLink="/member/test" [queryParams]="{name:'Aj.M'}">Test QueryParams</button>
<button (click)="sendParams()">Test QueryParams (Program)</button>
```

**member.component.ts**
```ts
  sendParams() {
    this.router.navigate(['/member/test'], {
      queryParams: { name: 'Aj.Potchara' },
    });
  }
  ```

![[Pasted image 20231121213515.png]]

##### Call Same Path will not change
- because ngOnInit is nor re-executeon showing component
- change the receiving parameter to asynchronous function

**test.component.ts**
```ts
  constructor(private activeatedRoute: ActivatedRoute) {
    activeatedRoute.queryParamMap.subscribe((params) => {
      this.name =
        this.activeatedRoute.snapshot.queryParamMap.get('name') || 'No Name';
    });
  }
  ```

![[Pasted image 20231121213848.png]]

![[Pasted image 20231121213515.png]]

#### Tip
### Same URL Reload
**app.config.ts**
```ts
export const appConfig: ApplicationConfig = {
  providers: [
    provideRouter(routes, withRouterConfig({onSameUrlNavigation:'reload'})),
    provideAnimations(),
  ],
};
```