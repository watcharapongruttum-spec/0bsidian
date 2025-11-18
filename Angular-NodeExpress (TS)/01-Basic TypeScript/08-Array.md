Using of **\[ \]**

Functions
- push(**item**) = add item to the array
- indexOf(**item**) = find index of the item
- splice(**index**,  **len**) =  remove item at the index with number of element to be remove
``` ts
let activiies = ['Sports', 'Programming', 'Eating', 'Sleeping'];
activiies.push('BoardGaming');
console.log(activiies);

let idx = activiies.indexOf('programming');
console.log(idx);

activiies.splice(idx,1);
console.log(activiies);

activiies = ["Sports", "Programming", "Eating", "Sleeping"];
activiies.push("BoardGaming");

idx = activiies.indexOf("Programming");
console.log(idx);

activiies.splice(idx, 1);
console.log(activiies);
```

![[Pasted image 20231116073938.png]]

# Array functions

Using of **arrow function**

**findIndex** = find the first indexes with custom condition
``` ts
let activiies = ['Sports', 'Programming', 'Eating', 'Sleeping'];
activiies.push('BoardGaming');
console.log(activiies);

let indexes = activiies.findIndex((item)=>{
  return item.toLowerCase() === 'eating';
});

console.log(indexes);
```

![[Pasted image 20231116074549.png]]

**filter** = filter items with custom condition
``` ts
let activiies = ["Sports", "Programming", "Eating", "Sleeping"];
activiies.push("BoardGaming");
console.log(activiies);

let filtered = activiies.filter((item) => item.endsWith("ing"));

console.log(filtered);
```

![[Pasted image 20231116074713.png]]

**map** = fetch all items in an array **Often use**
``` ts
let activiies = ['Sports', 'Programming', 'Eating', 'Sleeping'];
activiies.push('BoardGaming');
console.log(activiies);

activiies.map((item)=>{
  console.log(item);  
});
```

![[Pasted image 20231116074834.png]]

## Other functions

![[Pasted image 20231029123448.png]]

# Spread operator
for spreading items in array or object

``` ts 
let activiies = ["Sports", "Programming", "Eating", "Sleeping"];
let newActiviies = ["Traveling", "Gaming"];
let allActivities = [activiies, newActiviies];
console.log(allActivities);
```

Result will be arrays in array
![[Pasted image 20231116202915.png]]

``` ts
let activiies = ["Sports", "Programming", "Eating", "Sleeping"];
let newActiviies = ["Traveling", "Gaming"];
let allActivities = [...activiies, ...newActiviies];
console.log(allActivities);
```

Items will be spread to new array
![[Pasted image 20231116203155.png]]

Another example
``` ts
let user = {
  name : 'Aj.M',
  postion : 'Lecturer'
}

let admin = {
  isAdmin : true,
  user
}

console.log(admin);
```

Object user in object admin
![[Pasted image 20231116203322.png]]

Spread object's attributes
``` ts
let user = {
  name : 'Aj.M',
  postion : 'Lecturer'
}

let admin = {
  isAdmin : true,
  ...user
}

console.log(admin);
```

![[Pasted image 20231116203528.png]]



