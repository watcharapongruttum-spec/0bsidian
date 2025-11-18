Get and Delete can be called in the same way
- Asynchronous function
	- then/catch
	- async/await

With Path Param
	- using \`\` with ${ }
	-
**call-api.component.html**
```html
<mat-form-field appearance="outline" style="padding-left: 20px">
  <input matInput #keyword/>
</mat-form-field>
<button mat-raised-button color="primary" (click)="findOne(keyword)">FindOne</button>
```

**call-api.component.ts**
```ts
  async findOne(input: HTMLInputElement) {
    console.log(input.value);
    const url = `http://localhost/tripbooking/trip/${input.value}`;
    let data = await lastValueFrom(this.http.get(url));
    this.trips = data as TripGetResponse[];
    console.log(this.trips);
    console.log(this.trips[0].name);
    console.log('Call Completed');
  }
  ```

![[Pasted image 20231123203845.png]]

With QueryString Params { }
	- using  { }
	- 
**call-api.component.html**
```html
<mat-form-field appearance="outline" style="padding-left: 20px">
  <input matInput #name/>
</mat-form-field>
<button mat-raised-button color="primary" (click)="findName(name)">FindName</button>
```

**call-api.component.ts**
```ts
  async findName(input: HTMLInputElement) {
    console.log(input.value);
    const url = 'http://localhost/tripbooking/trip';
    let data = await lastValueFrom(
      this.http.get(url, {
        params: {
          name: input.value
        },
      })
    );
    this.trips = data as TripGetResponse[];
    console.log(this.trips);
    console.log(this.trips[0].name);
    console.log('Call Completed');
  }
  ```

![[Pasted image 20231123204947.png]]

## DELETE use **delete** method
