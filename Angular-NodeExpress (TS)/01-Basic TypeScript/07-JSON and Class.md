JSON **Object** is an object
JSON **String** is a String with no function
- scope with { }
- key - value pair ( : to separate)

**main.ts**
``` ts
const json = {
  name: "Aj.M",
  age: 20,
  work: "Computer Science, MSU",
  show(){
    console.log(this.name);
  }
};
console.log(typeof(json));
console.log(json);
console.log(json.name);
```

![[Pasted image 20231115072440.png]]

# Serialization

### JSON.stringify()
Convert JSON Object to JSON String

``` ts
const json = {
  name: "Aj.M",
  age: 20,
  work: "Computer Science, MSU",
  show(){
    console.log(this.name);
  }
};
console.log(typeof(json));
console.log(json);
console.log(JSON.stringify(json));
console.log(json.name);
```

function is removed
![[Pasted image 20231115072638.png]]

### JSON.parse()
Convert JSON String to JSON Object

``` ts
const json = {
  name: "Aj.M",
  age: 20,
  work: "Computer Science, MSU",
  show(){
    console.log(this.name);
  }
};
let jsonStr: string = JSON.stringify(json);
const jsonObj = JSON.parse(jsonStr);
console.log(jsonObj);
console.log(jsonObj.name);
```

function is removed
![[Pasted image 20231115072936.png]]


# Class
Object Oriented Programming (OOP) Concept
- Attributes, Information Hiding, Encapsulation, Constructor, this
- Setter and Getter

Define class User
``` ts
class User {
  private name: string = "";
  private age: number = 0;
  public work: string = "";
  constructor(name: string) {
    this.name = name;
  }

  public setName(name: string) {
    this.name = name;
  }

  public getName() {
    return this.name;
  }

  public set Age(age: number) {
    this.age = age;
  }

  public get Age() {
    return this.age;
  }
}
```

```ts
let user : User = new User('Aj.M');
user.Age = 20;
user.work = 'CS MSU'
console.log(`${user.getName()} ${user.Age} ${user.work}`);

user.setName("Potchara");
console.log(`${user.getName()} ${user.Age} ${user.work}`);
```

![[Pasted image 20231115094959.png]]

# Overloading function

Need to be declare function signature first
```ts
  add(x: number, y: number): number;
  add(x: string, y: string): string;
  add(x: any, y: any): any {
    if (typeof x === "number" && typeof y === "number") {
      return x + y;
    } else if (typeof x === "string" && typeof y === "string") {
      return x + y;
    } else {
      return x + y;
    }
  }

... 

let text = user.add("1111", "000");
console.log(text);
```

![[Pasted image 20231116073027.png]]

Use Optional parameter (?) is recommended
``` ts
  add(x?: any, y?: any): any {
    if (typeof x === "number" && typeof y === "number") {
      return x + y;
    } else if (typeof x === "string" && typeof y === "string") {
      return x + y;
    } else {
      return x + y;
    }
  }

...

let text = user.add("1111");
console.log(text);
```

![[Pasted image 20231116073432.png]]