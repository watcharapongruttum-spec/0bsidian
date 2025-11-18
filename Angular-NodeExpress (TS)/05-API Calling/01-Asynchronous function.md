**A**synchronous communication
- Do not wait
# New Application

```sh
ng new angular-api-calling
cd angular-api-calling
code .
```

MUI Installation
```shell
ng add @angular/material
```

Router Recap to new page
```sh
ng g c pages/async-demo --skip-tests
```

**app.router.ts**
```ts
export const routes: Routes = [
    {path: '', component: AsyncDemoComponent }
];
```

**app.component.html**
```html
<router-outlet></router-outlet>
```

![[Pasted image 20231122220410.png]]

# Normal function
- Top to bottom
- Wait until finish
- 
**async-demo.component.html**
```html
<p>async-demo works!</p>
<button  mat-raised-button color="primary" (click)="btnClick()">Run</button>
```

**async-demo.component.ts**
```ts
export class AsyncDemoComponent {
  btnClick() {
    this.normalFunction('1' + new Date());
    this.normalFunction('2' + new Date());
  }
  normalFunction(text: string) {
    console.log(text);
  }
}
```

![[Pasted image 20231123065431.png]]

# Promise
asynchronous function that does not wait for the result, but promise to come back when the process is finished
- use **async** keyword

**async-demo.component.ts**
```ts
  async delay(ms: number) {
    return await new Promise((resolve) => setTimeout(resolve, ms));
  }

  btnClick() {
    this.normalFunction('1' + new Date());
    this.normalFunction('2' + new Date());

    this.delay(2000);
    console.log('3 ' + new Date());
    this.delay(2000);
    console.log('4 ' + new Date());
  }
  ```

![[Pasted image 20231123065857.png]]


# Calling Promise (async) function using then, catch

**async-demo.component.ts**
```ts
  btnClick() {
    this.normalFunction('1' + new Date());
    this.normalFunction('2' + new Date());

    this.delay(2000).then(() => {
      console.log('3 ' + new Date());
    });

    this.delay(2000).then(() => {
      console.log('4 ' + new Date());
    });
  }
  ```
  
![[Pasted image 20231123070058.png]]

**async-demo.component.ts**
```ts
  btnClick() {
    this.normalFunction('1' + new Date());
    this.normalFunction('2' + new Date());

    this.delay(2000).then(() => {
      console.log('3 ' + new Date());
      this.delay(2000).then(() => {
        console.log('4 ' + new Date());
      });
    });
  }
  ```

![[Pasted image 20231123070253.png]]

**async-demo.component.ts**
```ts
  btnClick() {
    this.normalFunction('1' + new Date());
    this.normalFunction('2' + new Date());

    this.delay(2000).then(() => {
      console.log('3 ' + new Date());
      this.delay(2000).then(() => {
        console.log('4 ' + new Date());
      });
    });

     console.log('5 ' + new Date());
  }
  ```

![[Pasted image 20231123070426.png]]

**async-demo.component.ts**
```ts
  btnClick() {
    this.normalFunction('1' + new Date());
    this.normalFunction('2' + new Date());

    this.delay(2000).then(() => {
      console.log('3 ' + new Date());
      this.delay(2000).then(() => {
        console.log('4 ' + new Date());
        this.delay(2000).then(() => {
          console.log('5 ' + new Date());
        });
      });
    });

    console.log('6 ' + new Date());
  }
  ```
![[Pasted image 20231123070636.png]]

##### This is called CallBack Hell

#### Async/Await
Wait async method to finish
- **await** function MUST be called in async 

**async-demo.component.ts**
```ts
  async btnClick() {
    this.normalFunction('1' + new Date());
    this.normalFunction('2' + new Date());

    await this.delay(2000);
    console.log('3 ' + new Date());
    await this.delay(2000);
    console.log('4 ' + new Date());
  }
  ```

![[Pasted image 20231123071039.png]]

![[Pasted image 20231123071007.png]]


