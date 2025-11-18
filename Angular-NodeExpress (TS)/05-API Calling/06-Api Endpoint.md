Endpoint of API Service
- Easy to manage

# Create configuration constants

**new file in app/config/constants**
![[Pasted image 20231124072220.png]]

**constants.ts**
```ts
import { Injectable } from '@angular/core';

@Injectable({
  providedIn: 'root',
})
export class Constants {
  public readonly API_ENDPOINT: string = 'http://localhost/tripbooking';
}
```

# Create Service Api Endpoint

```sh
ng g s services/api/trip --skip-tests
```

![[Pasted image 20231124072454.png]]

**trip.service.ts**
```ts
import { Injectable } from '@angular/core';
import { HttpClient } from '@angular/common/http';
import { Constants } from '../../config/constants';
import { TripGetResponse } from '../../model/trip_get_res';
import { lastValueFrom } from 'rxjs';

@Injectable({
  providedIn: 'root',
})
export class TripService {
  constructor(private constants : Constants, private http: HttpClient) {}

  public async getTrip(options?: any) {
    const url = this.constants.API_ENDPOINT + '/trip';
    const response = await lastValueFrom(this.http.get(url));
    return response as TripGetResponse[];
  }
}
```

## Inject TripService into call-api.component

**call-api.component.ts**
```ts
export class CallApiComponent {
  constructor(private http: HttpClient, private tripService : TripService) {}
  trips: TripGetResponse[] = [];
```

![[Pasted image 20231124073047.png]]
##### Error: TripService injects (NULL) HttpClient

provide Global HttpClient for the application
**app.config.ts**
```ts
export const appConfig: ApplicationConfig = {
  providers: [provideRouter(routes), provideAnimations(), provideHttpClient()]
};
```

![[Pasted image 20231124073351.png]]

Modify call trips
**call-api.component.ts**
```ts
  async callApi() {
    // const url = 'http://localhost/tripbooking/trip';
    // let data = await lastValueFrom(this.http.get(url));
    // this.trips = data as TripGetResponse[];
    this.trips = await this.tripService.getTrip();

    console.log(this.trips);
    console.log(this.trips[0].name);
    console.log('Call Completed');
  }
```

![[Pasted image 20231124073653.png]]

**trip.service.ts**
```ts
  public async getOneTrip(id: number, options?: any) {
    const url = this.constants.API_ENDPOINT + '/trip/' + id;
    const response = await lastValueFrom(this.http.get(url));
    return response as TripGetResponse[];
  }
```

Modify call trips
**call-api.component.ts**
```ts
  async findOne(input: HTMLInputElement) {
    // console.log(input.value);
    // const url = `http://localhost/tripbooking/trip/${input.value}`;
    // let data = await lastValueFrom(this.http.get(url));
    // this.trips = data as TripGetResponse[];
    this.trips = await this.tripService.getOneTrip(+input.value);

    console.log(this.trips);
    console.log(this.trips[0].name);
    console.log('Call Completed');
  }
```

![[Pasted image 20231124075011.png]]


**trip.service.ts**
```ts
  public async getTripByName(name: string, options?: any) {
    const url = this.constants.API_ENDPOINT + '/trip';
    const response = await lastValueFrom(
      this.http.get(url, {
        params: {
          name: name,
        },
      })
    );
    return response as TripGetResponse[];
  }
```

Modify call trips
**call-api.component.ts**
```ts
  async findName(input: HTMLInputElement) {
    // console.log(input.value);
    // const url = 'http://localhost/tripbooking/trip';
    // let data = await lastValueFrom(
    //   this.http.get(url, {
    //     params: {
    //       name: input.value
    //     },
    //   })
    // );
    // this.trips = data as TripGetResponse[];
    this.trips = await this.tripService.getTripByName(input.value);
    
    console.log(this.trips);
    console.log(this.trips[0].name);
    console.log('Call Completed');
  }
```

![[Pasted image 20231124075307.png]]


**trip.service.ts**
```ts
  public async addNewTrip(trip : any, options?: any) {
    const url = this.constants.API_ENDPOINT + '/trip';
    const response = await lastValueFrom(
      this.http.post(url, JSON.stringify(trip))
    );
    return response;
  }
```

Modify post put trips
**postput.component.ts**
```ts
  constructor(private http: HttpClient, private tripService : TripService) {}

  async addNew() {
    const body = {
      name: this.name,
      country: this.country,
      destinationid: this.destination,
      coverimage: this.cover,
      detail: this.detail,
      price: this.price,
      duration: this.destination,
    };
    
    // const url = 'http://localhost/tripbooking/trip';
    // const response = await lastValueFrom(this.http.post(url, JSON.stringify(body) ));
    const response = await this.tripService.addNewTrip(body);

    console.log(response);
  }
```

![[Pasted image 20231124075935.png]]
