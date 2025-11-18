# HttpClient
https://angular.io/api/common/http/HttpClient

Create page and set route to the new page
```sh
ng g c pages/call-api --skip-tests
```

![[Pasted image 20231123071827.png]]

**callapi.component.html**
```html
<button mat-raised-button color="primary" (click)="callApi()">Call API</button>
```

**callapi.component.ts**
```ts
export class CallApiComponent {
  callApi() {}
}
```

### Test API
http://localhost/tripbooking/ping

![[Pasted image 20231123072323.png]]

# Calling Api using Observable

![[Pasted image 20231123073317.png]]

**callapi.component.ts**
```ts
import { Component } from '@angular/core';
import { CommonModule } from '@angular/common';
import { MatButtonModule } from '@angular/material/button';
import { HttpClient, HttpClientModule } from '@angular/common/http';

@Component({
  selector: 'app-call-api',
  standalone: true,
  imports: [CommonModule, MatButtonModule, HttpClientModule],
  templateUrl: './call-api.component.html',
  styleUrl: './call-api.component.scss',
})
export class CallApiComponent {
  constructor(private http: HttpClient) {}
  callApi() {
    const url = 'http://localhost/tripbooking/trip';
    this.http.get(url).subscribe((data: any) => {
      console.log(data);
    });
    
	console.log('Call Completed');
  }
}
```

![[Pasted image 20231123073530.png]]

# Calling Api using Async/Await
using of **lastValueFrom()** function

**callapi.component.ts**
```ts
  async callApi() {
    const url = 'http://localhost/tripbooking/trip';
    let data = await lastValueFrom(this.http.get(url));
    console.log(data);

    console.log('Call Completed');
  }
```

![[Pasted image 20231123074642.png]]

# Calling API based on HTTP Methods
- GET
	- Params
- POST
	- Body (Json)
- PUT
	- Body (Json)Body (Json)
- DELETE
	- Params

![[Pasted image 20231106095432.png]]

# Modelling
- Defined data type for request and response
- Using of the interface

![[Pasted image 20231106095508.png]]

![[Pasted image 20231106095651.png]]

![[Pasted image 20231123075350.png]]

![[Pasted image 20231123075501.png]]

**trip_get_res.ts**
```ts
export interface TripGetResponse {
  idx: number;
  name: string;
  country: string;
  destinationid: number;
  coverimage: string;
  detail: string;
  price: number;
  duration: number;
}
```

**callapi.component.ts**
```ts
  async callApi() {
    const url = 'http://localhost/tripbooking/trip';
    let data = await lastValueFrom(this.http.get(url));
    let trips = data as TripGetResponse[];
    console.log(trips);
    console.log(trips[0].name);
    console.log('Call Completed');
  }
```

![[Pasted image 20231123080046.png]]

# Display response in the component

![[Pasted image 20231123080321.png]]

**callapi.component.ts**
```ts
export class CallApiComponent {
  constructor(private http: HttpClient) {}
  trips : TripGetResponse[] = [];

  async callApi() {
    const url = 'http://localhost/tripbooking/trip';
    let data = await lastValueFrom(this.http.get(url));
    this.trips = data as TripGetResponse[];
    console.log(this.trips);
    console.log(this.trips[0].name);
    console.log('Call Completed');
  }
}
```

**callapi.component.html**
```html
<h2 *ngFor="let trip of this.trips">{{trip.name}}</h2>
```

![[Pasted image 20231123080633.png]]



