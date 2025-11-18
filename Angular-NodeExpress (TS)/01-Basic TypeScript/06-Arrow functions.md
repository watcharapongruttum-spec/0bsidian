
So called Anonymous function
- define to variable
- use with ( )

``` ts
let func = () => {
  console.log('This is an anonymous function');
};

func();
```

![[Pasted image 20231115071420.png]]

One line of code, arrow function can be used without { }
``` ts
let func = () => console.log('This is one line anonymous function');

func();
```

# Function as variable
- Declare function as a variable
- use it like a variable

**doSomething** is a function variable
**setTimeout** is a function to be wait until timeout (in millisecond)
``` ts
let doSomething  = () => {
  let dateTime = new Date();
  console.log(dateTime + ' Fuction doSomething is executed...');
}

setTimeout(doSomething, 2000);
setTimeout(doSomething, 3000);
setTimeout(() => {
  let dateTime = new Date();
  console.log(dateTime + " Fuction doSomething is executed...");
}, 4000);
```

![[Pasted image 20231115072009.png]]

**Often use with export and import**

**utils.ts**
``` ts
export default (name: string) => {
  return `Hello ${name}`;
};
```

**main.ts**
``` ts
import anyName from "./utils";

let text = anyName("Aj.M");
console.log(text);
```

![[Pasted image 20231115072207.png]]


