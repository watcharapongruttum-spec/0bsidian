External components make life easier.

# Material UI
- Material UI is a standard UI design from Google. It is also used in flutter and react
- https://material.angular.io
- Free for community use

Installation
```shell
ng add @angular/material
```

![[Pasted image 20231118061509.png]]

**Look at texts, font is now changed**
![[Pasted image 20231118061559.png]]

# MUI Components
https://material.angular.io/components/categories

#### How to use the component in general
1. Import component's module
2. Call component
3. Customize ts and css

# ToolBar
https://material.angular.io/components/toolbar

![[Pasted image 20231118062101.png]]

![[Pasted image 20231118062123.png]]

**header.component.ts**
```ts
import { MatToolbarModule } from '@angular/material/toolbar';

...

imports: [CommonModule, MatToolbarModule],
```

**header.component.html**
```html
<mat-toolbar>
    <span>My Application</span>
</mat-toolbar>
<p>header works!</p>
```

![[Pasted image 20231118062531.png]]

**header.component.html**
```html
<mat-toolbar>
  <div
    style="
      width: 100%;
      display: flex;
      flex-direction: row;
      justify-content: space-between;
    "
  >
    <span>My Application</span>
    <span>LOGIN</span>
  </div>
</mat-toolbar>
<p>header works!</p>
```

![[Pasted image 20231118063307.png]]


# Flex Layout
Widely used
https://css-tricks.com/snippets/css/a-guide-to-flexbox/

![[Pasted image 20231118065213.png]]

**app.component.html**
```html
<app-header></app-header>
<div
  style="
    width: auto;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
  "
>
  <h1>Hello World!!!</h1>
</div>
```

![[Pasted image 20231118070212.png]]

**app.component.html**
```html
margin-top: -100px;
```

![[Pasted image 20231118070401.png]]

# Card
https://material.angular.io/components/card

![[Pasted image 20231118070859.png]]

```html
  <mat-card>
    <mat-card-header>
      <mat-card-title>Actions Buttons</mat-card-title>
      <mat-card-subtitle>Start</mat-card-subtitle>
    </mat-card-header>
    <mat-card-actions>
      <button mat-button>LIKE</button>
      <button mat-button>SHARE</button>
    </mat-card-actions>
  </mat-card>
  ```

*Buttons are not the same*
![[Pasted image 20231118070824.png]]

# Button
https://material.angular.io/components/button

**app.component.ts**
```ts
import { Component } from '@angular/core';
import { CommonModule } from '@angular/common';
import { RouterOutlet } from '@angular/router';
import { HeaderComponent } from './components/header/header.component';
import { MatCardModule } from '@angular/material/card';
import { MatButtonModule } from '@angular/material/button';


@Component({
  selector: 'app-root',
  standalone: true,
  imports: [
    CommonModule,
    RouterOutlet,
    HeaderComponent,
    MatCardModule,
    MatButtonModule,
  ],
  templateUrl: './app.component.html',
  styleUrl: './app.component.scss',
})
export class AppComponent {
  title = 'angular-ui';
}
```

![[Pasted image 20231118071623.png]]

![[Pasted image 20231118071719.png]]

**app.component.html**
```html
    <mat-card-actions>
      <button mat-button color="primary">TEXT</button> &nbsp;
      <button mat-raised-button color="primary">RAISED</button> &nbsp;
      <button mat-flat-button color="primary">FLAT</button> &nbsp;
      <button mat-stroked-button color="primary">STROKE</button> &nbsp;
    </mat-card-actions>
```

![[Pasted image 20231120054452.png]]

# Input
https://material.angular.io/components/input/

elements to work with [`<mat-form-field>`](https://material.angular.io/components/form-field/overview)

**app.component.html**
``` html
    <mat-card-content>
      <form class="example-form">
        <mat-form-field class="example-full-width" appearance="outline">
          <mat-label>Favorite food</mat-label>
          <input matInput placeholder="Ex. Pizza" value="Sushi" />
        </mat-form-field>
        <br />
        <mat-form-field class="example-full-width">
          <mat-label>Leave a comment</mat-label>
          <textarea matInput placeholder="Ex. It makes me feel..."></textarea>
        </mat-form-field>
      </form>
    </mat-card-content>
```

![[Pasted image 20231120064327.png]]

### Input is too big and font is too small?

**style.scss**
```scss
// At the first line
@use '@angular/material' as mat;

.dense-1 {
    @include mat.all-component-densities(-1);
}

.dense-2 {
    @include mat.all-component-densities(-2);
}

.dense-3 {
    @include mat.all-component-densities(-3);
}
```

**app.component.html**
```html
        <mat-form-field
          class="example-full-width dense-3"
          appearance="outline"
          style="font-size: 14pt"
        >
```

![[Pasted image 20231120070015.png]]

# Icons
https://fonts.google.com/icons
https://material.angular.io/components/icon

![[Pasted image 20231120070927.png]]

**app.component.html**
```html
<mat-icon fontIcon="restaurant"></mat-icon>
```

![[Pasted image 20231120071104.png]]


