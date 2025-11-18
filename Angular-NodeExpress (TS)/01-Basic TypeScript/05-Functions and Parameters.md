# Function declaration


use **function** keyword
``` ts
function sayHello(){
  console.log('Hello!');
}

sayHello();
```

![[Pasted image 20231115061905.png]]

# Parameters

Typescript **MUST** define type (unsure type? just put **any**)
``` ts
function sayHello(name : string, age : any){
  console.log('Hello! ' + name + ' ' + age);
}

sayHello("Aj.M", 20);
sayHello('Aj.M', '20');
```

![[Pasted image 20231115062107.png]]

# Default parameters' value

Use **=** to assign default value
``` ts
function sayHello(name : string, age : any, address = 'CS MSU'){
  console.log('Hello! ' + name + ' ' + age + ' ' + address);
}

sayHello("Aj.M", 20);
sayHello("Aj.M", "20", 'Computer Science MSU');
```

![[Pasted image 20231115062318.png]]

# Optional parameters

Use **? after variable** to tell that the variable can be null
``` ts
function sayHello(name : string, age : any, address? : string){
  console.log('Hello! ' + name + ' ' + age + ' ' + address);
}

sayHello("Aj.M", 20);
sayHello("Aj.M", "20", 'Computer Science MSU');
```

![[Pasted image 20231115062525.png]]

# Return value (auto return type)

``` ts
function sayHello(name : string, age : any, address? : string){
  return 'Hello! ' + name + ' ' + age + ' ' + address;
}

let text = sayHello("Aj.M", 20);
console.log(text);

console.log(sayHello("Aj.M", "20", "Computer Science MSU"));
```

![[Pasted image 20231115071105.png]]

# String interpolation

use **\` \`** and **${...}**
``` ts
function sayHello(name: string, age: any, address?: string) {
  return `Hello! ${name} ${age} ${address}`;
}
```

# Function in Function

``` ts
function sayHello(name: string, age: any, address?: string) {
  function show() {
    console.log(text);
  }
  let text = `Hello! ${name} ${age} ${address}`;
  show();
}

sayHello("Aj.M", "20", "Computer Science MSU");
```

![[Pasted image 20231115071257.png]]
