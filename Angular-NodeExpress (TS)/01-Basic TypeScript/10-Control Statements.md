# Selection
Normal if, else if and else
``` ts
const userKey = prompt("Enter your Key");

if(userKey == '1234'){
  console.log('Enter with 1234');
} else if(userKey == '9999'){
  console.log("Enter with 9999");
}else{
  console.log("Enter WRONG key");
}
```

![[Pasted image 20231116204751.png]]

# Loop

For index and For of
``` ts
const users = ["Aj.M", "admin", "user1", "someone"];

for (let index = 0; index < users.length; index++) {
  console.log(users[index]);
}

console.log('=======');

for (const user of users) {
  console.log(user);
}
```

![[Pasted image 20231116205043.png]]

While loop
``` ts
const users = ["Aj.M", "admin", "user1", "someone"];

let idx = 0;
while (idx < users.length) {
  console.log(users[idx]);
  idx++;
}
```

![[Pasted image 20231116205120.png]]


