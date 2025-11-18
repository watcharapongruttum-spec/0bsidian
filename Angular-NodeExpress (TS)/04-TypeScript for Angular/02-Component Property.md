**advts.component.ts**
```ts
export class AdvtsComponent implements OnInit {
@Input() myProp: any;
ngOnInit(): void {
  console.log(this.myProp);
}
```

**app.component.ts**
```html
<app-advts [myProp]="'Hello This is Prop'"></app-advts>
```

![[Pasted image 20231122075240.png]]





