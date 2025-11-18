# Create new component

```sh
ng g c components/databinding --skip-tests
```

![[Pasted image 20231120073207.png]]

Clean up app.component.html

**app.component.html**
```html
<app-databinding></app-databinding>
```

![[Pasted image 20231120073336.png]]

Import Module (manual or automatic)

**app.component.ts**
![[Pasted image 20231120073521.png]]

![[Pasted image 20231120073440.png]]


# One way binding
## TS => HTML

Using of **{{ }}**

**databinding.component.ts**
```ts
export class DatabindingComponent {
  greeting = 'Hello World!!!';
}
```

**databinding.component.html**
``` html
<p>databinding works!</p>
<h1>{{greeting}}</h1>
```

![[Pasted image 20231120074323.png]]

Json data

**databinding.component.ts**
```ts
export class DatabindingComponent {
  greeting = 'Hello World!!!';
  landmarks = [
    {
      idx: 14,
      name: 'ภูเขาฟูจิ',
      country: 'ญี่ปุ่น',
      detail:
        'ภูเขาฟูจิ เป็นภูเขาที่สูงที่สุดในญี่ปุ่น และอาจกล่าวได้ว่าเป็นภูเขาที่สวยที่สุดในโลก มีความสูงถึง 3,776 เมตร ตั้งอยู่ระหว่างจังหวัดยะมะนะชิและชิซุโอะกะ และสามารถมองเห็นได้จากโตเกียวและโยโกฮาม่าในวันที่ท้องฟ้าปลอดโปร่ง วิธีที่จะได้เห็นภูเขาฟูจิที่ง่ายที่สุด คือ นั่งชมจากรถไฟสายโทไกโดที่วิ่งระหว่างเมืองโตเกียวและโอซาก้า ถ้าคุณนั่งชินกันเซ็นจากโตเกียวที่มุ่งหน้าไปยังนาโงย่า เกียวโต และโอซาก้า ช่วงที่จะได้เห็นภูเขาฟูจิ คือ ช่วงสถานีชิน-ฟูจิ หรือประมาณ 40-45 นาที หลังจากออกจากโตเกียว ซึ่งจะมองเห็นได้ทางด้านขวามือของรถไฟ แต่สำหรับผู้ที่อยากชมภูเขาฟูจิอย่างเต็มอิ่ม และแวดล้อมด้วยธรรมชาติที่งดงามขอเชิญที่ ทะเลสาบทั้งห้า (Fuji Five Lake or Fujigoko) หรือที่ ฮะโกะเนะ ซึ่งเป็นรีสอร์ทบ่อน้ำพุร้อนและเป็นหนึ่งใน อุทยานแห่งชาติ Fuji-Hakone-Izu',
      url: 'https://img.kapook.com/u/panadda/4_3.jpg',
    },
    {
      idx: 17,
      name: 'พระราชวังอิมพีเรียล',
      country: 'ญี่ปุ่น',
      detail:
        'พระราชวังอิมพีเรียล แต่เดิมมีชื่อว่า พระราชวังเอะโดะ อีก หนึ่งสถานท่องเที่ยวที่สำคัญแห่งหนึ่งในประวัติศาสตร์ ตั้งอยู่ที่เมืองโตเกียว เพราะเป็นสถานที่ประทับของสมเด็จพระจักรพรรดิแห่งราชวงศ์เมจิ แห่งประเทศญี่ปุ่น เดิมที่นี่เป็นหมู่บ้านประมงเล็กที่ชื่อ เอะโดะ ที่ถูกตั้งเป็นฐานที่มั่น รวมทั้งถูกตั้งเป็นศูนย์กลางของรัฐบาลทหาร ต่อมาได้ขยายเมืองให้ใหญ่ขึ้น จนมีประชากรและพื้นที่เมืองขนาดใหญ่มากขึ้น หลังจากนั้นเข้าสู่ยุคปฏิรูปเมจิ การล้มล้างการปกครองแบบโชกุนลง จักรพรรดิเมจิจึงย้ายเมืองหลวงมาที่เอะโดะ และเปลี่ยนชื่อเมืองเป็นโตเกียวในปัจจุบัน ที่นี่จึงเป็นศูนย์กลางทางการปกครองและวัฒนธรรมของประเทศ และถูกเปลี่ยนให้เป็นพระราชวังในเวลาต่อมา มีชื่อเรียกว่า พระราชวังอิมพิเรียล ในปัจจุบัน',
      url: 'https://img.kapook.com/u/panadda/1_3.jpg',
    },
    {
      idx: 11,
      name: 'หมู่บ้านกังหันลมโบราณ Zaanse Schans',
      country: 'เนเธอร์แลนด์',
      detail:
        'เป็นพื้นที่อุตสาหกรรมที่สำคัญที่สุดแห่งหนึ่งในประเทศเนเธอร์แลนด์ มีกังหันลมนับร้อยแห่ง ซึ่งใช้ช่วยในการผลิตสีทาไม้ น้ำมัน มัสตาร์ด กระดาษ และผลิตภัณฑ์อื่นๆ ปัจจุบันหมู่บ้านแห่งนี้ได้ถูกจัดตั้งเป็นพิพิธภัณฑ์ ร้านขายของที่ระลีก และศูนย์ฝึกอบรม แต่บางหลังก็ยังใช้เป็นที่อยู่อาศัยส่วนตัวอีกด้วย',
      url: 'https://image.makewebeasy.net/makeweb/0/FJ8KH0VZs/GL/zaanse_schans.jpg',
    },
    {
      idx: 10,
      name: 'คลองอัมสเตอร์ดัม Amsterdam',
      country: 'เนเธอร์แลนด์',
      detail:
        'อัมสเตอร์ดัมเมืองหลวงแห่งคลองของเนเธอร์แลนด์ ในอดีตคลองเหล่านี้ถูกใช้ในการสัญจรและการขนส่ง แต่ในปัจจุบันลำคลองทุกสายถูกใช้ในเชิงการท่องเที่ยว อัมสเตอร์ดัมเป็นเมืองที่มีทัศนียภาพอันงดงามรวมทั้งตึกรามบ้านช่องและสถาปัตยกรรมต่างๆซึ่งยังคงเป็นศิลปะโบราณแบบสเปนผสมเรอเนอซองส์ ตลอดจนเรือนแพที่จอดตามลำคลองก็ล้วนแล้วแต่สวยงามแปลกตา',
      url: 'https://www.travelguideline.net/wp-content/uploads/2020/01/amsterdam-canal-2.jpg',
    },
  ];
}
```

**databinding.component.html**
```html
<p>databinding works!</p>
<h1>{{greeting}}</h1>
<h2>{{landmarks[0].name}}</h2>
<h3>{{landmarks[0].country}}</h3>
<p>{{landmarks[0].detail}}</p>
<img src="{{landmarks[0].url}}">
```

![[Pasted image 20231120100700.png]]

# Two-ways binding
## TS <==> HTML

Using of **[(ngModel)]**
- Import FormModule

**databinding.component.ts**
```ts
import { MatInputModule } from '@angular/material/input';

...

export class DatabindingComponent {

text = '';
```

**databinding.component.html**
```html
<mat-form-field appearance="outline">
  <input matInput placeholder="Text here.." value="" [(ngModel)]="text"/>
</mat-form-field>
{{text}}
```

Constantly changed when inputing text
![[Pasted image 20231120102657.png]]

## Material UI Select

**databinding.component.ts**
```ts
import { MatSelectModule } from '@angular/material/select';

...

export class DatabindingComponent {
  text = '';
  country = '';
```

**databinding.component.html**
```html
<mat-form-field appearance="outline">
  <mat-label>ประเทศ</mat-label>
  <select matNativeControl required [(ngModel)]="country">
    <option value="ญี่ปุ่น">ญี่ปุ่น</option>
    <option value="เนเธอร์แลนด์">เนเธอร์แลนด์</option>
  </select>
</mat-form-field>
{{country}}
```

![[Pasted image 20231120104054.png]]

Select changed and execute function

**databinding.component.ts**
```ts
  selectCountry() {
    console.log('Selected value: ' + this.country);
  }
```

**databinding.component.html**
```html
<mat-form-field appearance="outline">
  <mat-label>ประเทศ</mat-label>
  <select
    matNativeControl
    required
    [(ngModel)]="country"
    (ngModelChange)="selectCountry()"
  >
    <option value="ญี่ปุ่น">ญี่ปุ่น</option>
    <option value="เนเธอร์แลนด์">เนเธอร์แลนด์</option>
  </select>
</mat-form-field>
{{ country }}
```

![[Pasted image 20231120104610.png]]

![[Pasted image 20231120104635.png]]

# Data passing by function's parameter
Using **#** id

**databinding.component.html**
```html
<mat-form-field appearance="outline">
  <input
    #inputText
    matInput
    placeholder="Text here.."
    value=""
    [(ngModel)]="text"
  />
</mat-form-field>
{{ text }}
<button mat-flat-button color="primary" (click)="btnClick(inputText)">
  OK
</button>
<br />
```

**databinding.component.ts**
```ts
export class DatabindingComponent {
btnClick(text: HTMLInputElement) {
  console.log(text.value);
}
```

![[Pasted image 20231120111425.png]]

![[Pasted image 20231120111457.png]]





