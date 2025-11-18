# Basic operations


- ( ) + - * / % 
- ++ --
- += -=
- > < >= <=  !=
- ? (nullable) ! (null assertion)

# == VS ===

#### In JavaScript
Operation == is used to compare only value (automatic convert and check)
Operation === is used to compare only value and type (but JavaScript has no type, so auto type)

#### In TypeScript
Operation == is used to compare only value (same type)
Operation === is used to compare only value and type (same as == )

*Recommended!*  use === as in JavaScript but Aj.M prefers == 

# Concatenation

``` ts
const s : string = "This is some text ";
const n : number = 1;
console.log(s + n);
```

![[Pasted image 20231115061628.png]]

``` ts
const s = "This is some text ";
const n = 1;
const m = 2;
console.log(s + n + m);
console.log(s + (n + m));
```

![[Pasted image 20231115061654.png]]