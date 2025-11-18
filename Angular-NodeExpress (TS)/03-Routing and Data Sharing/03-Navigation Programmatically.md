**Router** Object **Injection**

**member.component.ts**
```ts
import { Router, RouterLink, RouterOutlet } from '@angular/router';

...

export class MemberComponent {
  constructor(private router: Router) {}
  changePage1() {
    this.router.navigateByUrl('/member/list');
  }
  changePage2() {
    this.router.navigateByUrl('/member/profile');
  }
}
```

![[Pasted image 20231121194810.png]]

