Post and Put can be called in the same way
- Asynchronous function
	- then/catch
	- async/await
- Request Body
	- Form
	- Json
	- File

# Create Input Form

```sh
ng g c pages/postput --skip-tests
```

## Set route (**/postput**)

**postput.component.html**
```html
<p>postput works!</p>
<div
  style="
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 100vw;
  "
>
  <mat-form-field appearance="outline" style="width: 200px">
    <mat-label>Name</mat-label>
    <input matInput [(ngModel)]="name" />
  </mat-form-field>
  <mat-form-field appearance="outline" style="width: 200px">
    <mat-label>Destination</mat-label>
    <mat-select [(ngModel)]="destination">
      @for (distination of distinations; track distination) {
      <mat-option [value]="distination.value">{{
        distination.name
      }}</mat-option>
      }
    </mat-select>
  </mat-form-field>
  <mat-form-field appearance="outline" style="width: 200px">
    <mat-label>Country</mat-label>
    <input matInput [(ngModel)]="country" />
  </mat-form-field>
  <mat-form-field appearance="outline" style="width: 200px">
    <mat-label>Cover Image</mat-label>
    <input matInput [(ngModel)]="cover" />
  </mat-form-field>
  <mat-form-field appearance="outline" style="width: 200px">
    <mat-label>Detail</mat-label>
    <input matInput [(ngModel)]="detail" />
  </mat-form-field>
  <mat-form-field appearance="outline" style="width: 200px">
    <mat-label>Price</mat-label>
    <input matInput [(ngModel)]="price" />
  </mat-form-field>
  <mat-form-field appearance="outline" style="width: 200px">
    <mat-label>Duration</mat-label>
    <input matInput [(ngModel)]="duration" />
  </mat-form-field>
  <button mat-raised-button color="primary" (click)="addNew()" style="width: 200px">
    Add New
  </button>
</div>

```

**postput.component.ts**
``` ts
import { Component } from '@angular/core';
import { CommonModule } from '@angular/common';
import { MatInputModule } from '@angular/material/input';
import { MatSelectModule } from '@angular/material/select';
import { MatButtonModule } from '@angular/material/button';
import { FormsModule } from '@angular/forms';


@Component({
  selector: 'app-postput',
  standalone: true,
  imports: [CommonModule, MatInputModule, MatSelectModule, MatButtonModule, FormsModule],
  templateUrl: './postput.component.html',
  styleUrl: './postput.component.scss',
})
export class PostputComponent {
  name: string = '';
  destination: string = '';
  country: string = '';
  cover: string = '';
  detail: string = '';
  price: number = 0;
  duration: number = 0;

  distinations: Destination[] = [
    { value: 1, name: 'เอเชีย' },
    { value: 2, name: 'ยุโรป' },
    { value: 3, name: 'เอเชียตะวันออกเฉียงใต้' },
    { value: 9, name: 'ประเทศไทย' },
  ];
  addNew() {
    console.log(this.destination);
    
  }
}

interface Destination {
  value: number;
  name: string;
}
```

![[Pasted image 20231123212056.png]]

**postput.component.ts**
``` ts
import { Component } from '@angular/core';
import { CommonModule } from '@angular/common';
import { MatInputModule } from '@angular/material/input';
import { MatSelectModule } from '@angular/material/select';
import { MatButtonModule } from '@angular/material/button';
import { FormsModule } from '@angular/forms';
import { HttpClient, HttpClientModule } from '@angular/common/http';
import { lastValueFrom } from 'rxjs';


@Component({
  selector: 'app-postput',
  standalone: true,
  imports: [
    CommonModule,
    MatInputModule,
    MatSelectModule,
    MatButtonModule,
    FormsModule,
    HttpClientModule,
  ],
  templateUrl: './postput.component.html',
  styleUrl: './postput.component.scss',
})
export class PostputComponent {
  name: string = '';
  destination: string = '';
  country: string = '';
  cover: string = '';
  detail: string = '';
  price: number = 0;
  duration: number = 0;

  distinations: Destination[] = [
    { value: 1, name: 'เอเชีย' },
    { value: 2, name: 'ยุโรป' },
    { value: 3, name: 'เอเชียตะวันออกเฉียงใต้' },
    { value: 9, name: 'ประเทศไทย' },
  ];

  constructor(private http: HttpClient) {}

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
    const url = 'http://localhost/tripbooking/trip';
    const response = await lastValueFrom(this.http.post(url, JSON.stringify(body) ));
    console.log(response);
  }
}

interface Destination {
  value: number;
  name: string;
}

```


![[Pasted image 20231123214318.png]]


## UPDATE uses **put** method

# File upload
multipart/form-data

# Create Upload Form

```sh
ng g c pages/upload --skip-tests
```

## Set route (**/upload**)

**upload.component.html**
```html
<p>upload works!</p>

<input type="file" (change)="onFileSelected($event)" #fileUpload />
<br />
<button
  mat-raised-button
  color="primary"
  (click)="upload()"
  style="width: 200px"
>
  Upload
</button>
```

**upload.component.ts**
```ts
import { Component } from '@angular/core';
import { CommonModule } from '@angular/common';
import { MatInputModule } from '@angular/material/input';
import { MatButtonModule } from '@angular/material/button';
import { FormsModule } from '@angular/forms';
import { HttpClient, HttpClientModule } from '@angular/common/http';
import { lastValueFrom } from 'rxjs';

@Component({
  selector: 'app-upload',
  standalone: true,
  imports: [CommonModule, MatInputModule, FormsModule, HttpClientModule],
  templateUrl: './upload.component.html',
  styleUrl: './upload.component.scss',
})
export class UploadComponent {

  file?: File;
  constructor(private http: HttpClient) {}
  onFileSelected(event: Event) {
    if ((event.target as HTMLInputElement).files){
      this.file = (event.target as HTMLInputElement).files![0];
      console.log(this.file);      
    }
      
  }
  async upload() {
    if (this.file) {
      console.log('Uploading');
      const url = 'http://localhost/tripbooking/upload';
      const formData = new FormData();
      formData.append('file', this.file);

      const response = await lastValueFrom(
        this.http.post(url, formData, )
      );
      console.log(response);
    }
  }
}
```

![[Pasted image 20231123231915.png]]