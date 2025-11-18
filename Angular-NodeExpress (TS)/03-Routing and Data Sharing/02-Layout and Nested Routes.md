Problem: Header Component need to be add in every pages

- Show header outside the router-outlet
- Remove  header from main and member pages
**app.component.html**
```html
<app-header></app-header>
<router-outlet></router-outlet>
```

# Nested routes

#### router-outlet display concept
/level1/level2/level3
**root** router-outlet/**child** router-outlet /**grandchild** router-outlet  

**app.routes.ts**
```ts
export const routes: Routes = [
  { path: '', component: MainComponent },
  {
    path: 'member',
    component: MemberComponent,
    children: [
      { path: 'list', component: ListComponent },
      { path: 'profile', component: ProfileComponent },
    ],
  },
];
```

- app = level1
	- member = level2
		- list = level3
		- profile = level3
![[Pasted image 20231121191733.png]]

- app.component.html = **root** router-outlet
	- member.compnent.html = **child** router-outlet 

**member.component.html**
```html
<!-- <app-header></app-header> -->
<p>member works!</p>
<button routerLink="/member/list">List Members</button>
<button routerLink="/member/profile">Member Profile</button>
<router-outlet></router-outlet>
```

![[Pasted image 20231121192351.png]]

# Handling Page Not Found (404)

```sh
ng g c pages/pagenotfound --skip-tests
```

Add wildcard route to Page not found component
```ts
  //Wild Card Route for 404 request
  { path: '**', component: PagenotfoundComponent },
  ```

![[Pasted image 20231121193300.png]]
