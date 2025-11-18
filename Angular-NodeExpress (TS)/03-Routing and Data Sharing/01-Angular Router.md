# Create new app

```sh
ng new angular-router
cd angular-router
code .
```

MUI Installation
```shell
ng add @angular/material
```

# Page
Page is just a component
*Recommend: create in pages folder*

```sh
ng g c pages/main --skip-tests
```

![[Pasted image 20231121064656.png]]

# Router
Manage routing path to components
# Router Outlet
Area to display components

**app.routes.ts**
```ts
import { Routes } from '@angular/router';
import { MainComponent } from './pages/main/main.component';

export const routes: Routes = [
    {path: '', component: MainComponent}
];
```

**app.component.html**
```html
<router-outlet></router-outlet>
```

![[Pasted image 20231121065149.png]]

# Page's Component
Components used in a page

```sh
ng g c pages/main/header --skip-tests
```

![[Pasted image 20231121074011.png]]

**main.component.html**
```html
<app-header></app-header>
<p>main works!</p>
```

![[Pasted image 20231121074126.png]]

#### Another page
```sh
ng g c pages/member --skip-tests
```

![[Pasted image 20231121074432.png]]

**member.component.html**
```html
<app-header></app-header>
<p>member works!</p>
```

#### Add route

**app.routes.ts**
```ts
export const routes: Routes = [
    {path: '', component: MainComponent},
    {path: 'member', component: MemberComponent}
];
```

![[Pasted image 20231121075017.png]]

# Page Navigation

### Normal **href** link
Make a new request to get new component

**header.component.html**
```html
<p>header works!</p>
<div style="display: flex; flex-direction: row; justify-content: space-around">
  <a href="">Home</a>
  <a href="/member">Member</a>
</div>
```

![[Pasted image 20231121075500.png]]

### RouterLink
Call component in the application
Import **RouterModule**

**header.component.ts**
```ts
import { Component } from '@angular/core';
import { CommonModule } from '@angular/common';
import { RouterModule } from '@angular/router';


@Component({
  selector: 'app-header',
  standalone: true,
  imports: [CommonModule, RouterModule],
  templateUrl: './header.component.html',
  styleUrl: './header.component.scss'
})
export class HeaderComponent {

}
```

**header.component.html**
```html
<p>header works!</p>
<div style="display: flex; flex-direction: row; justify-content: space-around">
  <a href="">Home</a>
  <a href="/member">Member</a>
  <a routerLink="">Home (RouterLink)</a>
  <a routerLink="/member">Member (RouterLink)</a>
</div>
```

![[Pasted image 20231121094501.png]]



