Sharing data between components
# Service
Application Scope
- store any data in the application
**- refresh browser, data will be lost**

```sh
ng g s service/appdata --skip-tests
```

![[Pasted image 20231121223646.png]]

**appdata.service.ts**
```ts
import { Injectable } from '@angular/core';

@Injectable({
  providedIn: 'root'
})
export class AppdataService {
  members = Array<Member>();
  constructor() { }
}

export class Member {
  id : number = 0;
  fullname : string = '';
  image : string = '';
}
```

**member.component.ts**
```ts
  addMember(){
    let member = new Member();
    member.id = Math.random();
    member.fullname = 'Test Fullname';
    member.image = 'Test Image';
    this.appData.members.push(member);
    console.log(this.appData.members);
  }
  ```

**member.component.html**
```html
<button (click)="addMember()">Add Member</button>
```

![[Pasted image 20231121224722.png]]
##### Refresh browser, data will be lost
![[Pasted image 20231121224807.png]]

# SessionStorage
Browser Scope
- key-value pair (string)

**member.component.html**
```html
<button (click)="addMemberSession()">Add Member Session</button>
```

**member.component.ts**
```ts
  addMemberSession() {
    let members = [];
    if(sessionStorage.getItem('members')){
        members = JSON.parse(sessionStorage.getItem('members')!);
    }
    let member = new Member();
    member.id = Math.random();
    member.fullname = 'Test Fullname';
    member.image = 'Test Image';
    members.push(member);
    sessionStorage.setItem('members', JSON.stringify(members));

    console.log(sessionStorage.getItem('members'));
  }```

![[Pasted image 20231122060452.png]]

Refresh = Data available
Close browser = Data lost

# LocalStorage
Persistance
- key-value pair (string)

**member.component.html**
```html
<button (click)="addMemberLocalStorage()">Add Member LocalStorage</button>
```

**member.component.ts**
```ts
  addMemberLocalStorage() {
    let members = [];
    if (localStorage.getItem('members')) {
      members = JSON.parse(localStorage.getItem('members')!);
    }
    let member = new Member();
    member.id = Math.random();
    member.fullname = 'Test Fullname';
    member.image = 'Test Image';
    members.push(member);
    localStorage.setItem('members', JSON.stringify(members));

    console.log(localStorage.getItem('members'));
  }
  ```

![[Pasted image 20231122061059.png]]

Refresh = Data available
Close browser = Data available
