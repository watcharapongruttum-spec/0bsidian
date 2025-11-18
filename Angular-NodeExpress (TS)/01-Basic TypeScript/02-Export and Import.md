Create utils.ts


**utils.ts**
``` ts
const myText = 'Hello Aj.M';
```

**main.js**
``` ts
import { myText } from './utils'
console.log(myText);
```

Error Cannot import
![[Pasted image 20231114102407.png]]

Export for using in other files
**utils.ts**
``` ts
export const myText = 'Hello Aj.M';
```

![[Pasted image 20231114102644.png]]

Only one default in a file
``` ts
export const myText = 'Hello Aj.M';
export let anotherText = 'I am Aj.M';
export default 'A Leturer in CS MSU';
```

Calling default without { } and MUST declare a name (ex. thisIsDefault)
``` ts
import { myText, anotherText } from "./utils";
import thisIsDefault from "./utils";

console.log(myText);
console.log(anotherText);
console.log(thisIsDefault);
```

![[Pasted image 20231114200533.png]]

# var, let and const

var = Traditional JavaScript declaration
let = Value can be changed
const = "Constant" = Value cannot be changed

```ts
let text = "Hello";
text = "Hello Test";

const constText = "Hello";
constText = "Hello Test";
```

Value cannot be changed
![[Pasted image 20231114204428.png]]