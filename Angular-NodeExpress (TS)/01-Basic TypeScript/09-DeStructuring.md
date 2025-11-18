De-structure to multiple variables
``` ts
let [fullname, position] = ['Aj.M', 'Front-end Developer'];
console.log(fullname);
console.log(position);
```

![[Pasted image 20231116203700.png]]

Or use to change attribute names
``` ts
let { fullname: namex, position, salary: income } = {
  fullname: "Aj.M",
  position: "Back-end Developer",
  salary : 250000
};
console.log(namex);
console.log(position);
console.log(income);
```

![[Pasted image 20231116203922.png]]





