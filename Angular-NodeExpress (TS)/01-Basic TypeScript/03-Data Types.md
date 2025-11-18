# Typed variables



``` ts
let text1 : string = 'Hello';
let text2 = 'Hello';
let text3 : any = 'Hello';
console.log(typeof(text1));
console.log(typeof(text2));
console.log(typeof(text3));

text1 = 10;
text2 = 10;
text3 = 10;
console.log(text1);
console.log(text2);
console.log(text3);
console.log(typeof(text1));
console.log(typeof(text2));
console.log(typeof(text3));
```

TypeScript is type checked
![[Pasted image 20231114211125.png]]

![[Pasted image 20231114211313.png]]

Types in TypeScript
![[Pasted image 20231029085716.png]]

# Undefined vs Null

undefined = not assigned
null = value of null

``` ts
let u = undefined;
console.log(u);
u = true;
console.log(u);
console.log(typeof u);

let n = null;
console.log(n);
n = true;
console.log(n);
console.log(typeof n);
```

![[Pasted image 20231115061304.png]]

