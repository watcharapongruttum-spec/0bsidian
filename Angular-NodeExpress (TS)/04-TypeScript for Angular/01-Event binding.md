# New Application

```sh
ng new angular-adv-ts
cd angular-adv-ts
code .
```

```sh
ng g c advts --skip-tests
```

**app.component.html**
```html
<app-advts></app-advts>
```

![[Pasted image 20231122072719.png]]
# Events
https://www.positronx.io/useful-list-of-angular-event-types-for-event-binding/

```ts
// Full list of Angular Events
(click)="myFunction()"      
(dblclick)="myFunction()"   
(submit)="myFunction()"
(blur)="myFunction()"  
(focus)="myFunction()" 
(scroll)="myFunction()"
(cut)="myFunction()"
(copy)="myFunction()"
(paste)="myFunction()"
(keyup)="myFunction()"
(keypress)="myFunction()"
(keydown)="myFunction()"
(mouseup)="myFunction()"
(mousedown)="myFunction()"
(mouseenter)="myFunction()"
(drag)="myFunction()"
(drop)="myFunction()"
(dragover)="myFunction()"
```

#### (click)
**advts.component.html**
```html
<button (click)="clickMe()">Click Me</button>
```

**advts.component.ts**
```ts
  clickMe() {
    console.log('Yes you have clicked me');    
  }
```

![[Pasted image 20231122073026.png]]

**advts.component.html**
```html
<p (click)="clickMe()">Lorem ipsum, dolor sit amet consectetur adipisicing elit. Rerum ut eos animi cum, ipsam deserunt commodi nam magni eum dolores at modi reprehenderit officia velit quaerat quae aliquid possimus ullam.</p>
```

![[Pasted image 20231122073235.png]]

#### (change)
fire on enter or unfocus

**advts.component.html**
```html
<input type="text" (change)="onInputChange($event)">
```

**advts.component.ts**
```ts
  onInputChange($event: Event) {
    let target = $event.target as HTMLInputElement;
    console.log(target.value);
  }
```

![[Pasted image 20231122074208.png]]

#### (keyup)
fire on keyboard up
**advts.component.html**
```html
<input type="text" (keyup)="onInputChange($event)">
```

![[Pasted image 20231122074410.png]]


