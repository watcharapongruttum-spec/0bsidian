Json Data
Add to assets folder
![[landmark.json]]

# New component (landmarks)

```sh
ng g c components/landmarks --skip-tests
```

Clean up and changed to landmark component

**app.component.html**
```html
<app-landmarks></app-landmarks>
```

## Loading Json data
https://www.angularjswiki.com/angular/how-to-read-local-json-files-in-angular/

**tsconfig.json**
```ts
  "compilerOptions": {
    "resolveJsonModule": true, 
```

![[Pasted image 20231120114145.png]]

**app.component.html**
```html
<app-landmarks></app-landmarks>
```

**landmarks.component.ts**
```ts
import { Component } from '@angular/core';
import { CommonModule } from '@angular/common';
import jsonData from '../../../assets/landmark.json';
@Component({
  selector: 'app-landmarks',
  standalone: true,
  imports: [CommonModule],
  templateUrl: './landmarks.component.html',
  styleUrl: './landmarks.component.scss'
})
export class LandmarksComponent {
  landmarks = jsonData;
  constructor(){
    console.log(this.landmarks);
  }
}
```

![[Pasted image 20231120114314.png]]

![[Pasted image 20231120114427.png]]

# Display data on HTML

**landmarks.component.html**
```html
<div style="margin: 20px">
  id: <input type="text" #id /><button (click)="findOne(id)">Find</button>
</div>
```

**landmarks.component.ts**
```ts
export class LandmarksComponent {
  landmarks = jsonData;
  constructor() {
    console.log(this.landmarks);
  }
  findOne(id: HTMLInputElement) {
    console.log(id.value);
  }
}
```

![[Pasted image 20231120122243.png]]

Loop to find by id

**landmarks.component.ts**
```ts
  findOne(id: HTMLInputElement) {
    console.log(id.value);
    this.landmark = null;
    for (const lm of this.landmarks) {
      if (lm.idx.toString() == id.value) {
        console.log(lm);
        this.landmark = lm;
        return;
      }
    }
  }
```

![[Pasted image 20231120212513.png]]

## \*ngIf
Condition check before display data
- Use in HTML

**landmarks.component.html**
```html
<div *ngIf="landmark; else elseBlock">
  <h1>{{ this.landmark.name }}</h1>
  <h2>{{ this.landmark.name }}</h2>
  <h3>{{ this.landmark.country }}</h3>
  <p>{{ this.landmark.detail }}</p>
  <img src="{{ this.landmark.url }}" />
</div>
<ng-template #elseBlock>
  <div>Landmark not found</div>
</ng-template>
```

![[Pasted image 20231120213926.png]]

## \*ngFor
Loop display data
- Loop on the element that ngFor is put
- Use in HTML

**landmarks.component.html**
```html
<div *ngIf="landmark; else elseBlock">
  <h1>{{ this.landmark.name }}</h1>
  <h2>{{ this.landmark.name }}</h2>
  <h3>{{ this.landmark.country }}</h3>
  <p>{{ this.landmark.detail }}</p>
  <img src="{{ this.landmark.url }}" />
</div>
<ng-template #elseBlock>
  <div style="display: flex; flex-direction: column">
    <div *ngFor="let lm of landmarks">
      <h1>{{ lm.name }}</h1>
      <h2>{{ lm.name }}</h2>
      <h3>{{ lm.country }}</h3>
      <p>{{ lm.detail }}</p>
      <img src="{{ lm.url }}" width="300px" />
    </div>
  </div>
</ng-template>
```

![[Pasted image 20231120215735.png]]

# CSS Styling
# External CSS Styling
External CSS file

https://fonts.google.com/
![[Pasted image 20231120221139.png]]

**landmarks.component.scss**
```scss
@import url('https://fonts.googleapis.com/css2?family=Noto+Sans+Linear+B&family=Noto+Sans+Thai&display=swap');

.ggfont {
  font-family: "Noto Sans Linear B", sans-serif;
  font-family: "Noto Sans Thai", sans-serif;
}
```

Use ggfont
**landmarks.component.html**
```html
<div *ngIf="landmark; else elseBlock" class="ggfont">
  <h1>{{ this.landmark.name }}</h1>
  <h2>{{ this.landmark.name }}</h2>
  <h3>{{ this.landmark.country }}</h3>
  <p>{{ this.landmark.detail }}</p>
  <img src="{{ this.landmark.url }}" />
</div>
<ng-template #elseBlock>
  <div style="display: flex; flex-direction: column" class="ggfont">
    <div *ngFor="let lm of landmarks">
      <h1>{{ lm.name }}</h1>
      <h2>{{ lm.name }}</h2>
      <h3>{{ lm.country }}</h3>
      <p>{{ lm.detail }}</p>
      <img src="{{ lm.url }}" width="300px" />
    </div>
  </div>
</ng-template>
```

![[Pasted image 20231120221256.png]]

# Internal CSS Styling
Using of **style** tag

```html
<style>
    h3 {
        color: red;
    }
</style>
```

![[Pasted image 20231120221646.png]]

# Inline CSS Styling
Using of **style** property

```html
  <div style="display: flex; flex-direction: column" class="ggfont">
    <div *ngFor="let lm of landmarks">
      <h1>{{ lm.name }}</h1>
      <h2>{{ lm.name }}</h2>
      <h3>{{ lm.country }}</h3>
      <p>{{ lm.detail }}</p>
      <img src="{{ lm.url }}" width="300px" />
    </div>
  </div>
  ```

![[Pasted image 20231120221841.png]]

