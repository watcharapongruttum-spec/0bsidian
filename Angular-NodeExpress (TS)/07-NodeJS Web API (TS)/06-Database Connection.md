https://www.npmjs.com/package/mysql

```shell
npm install mysql
npm i --save-dev @types/mysql
```

# Pooling connections

```ts
import mysql from "mysql";

export const conn = mysql.createPool({
  connectionLimit: 10,
  host: "localhost",
  user: "tripbooking",
  password: "tripbooking@csmsu",
  database: "tripbooking",
});
```

**trip.ts**
```ts
router.get("/", (req, res) => {
  conn.query('select * from trip', (err, result, fields)=>{
    res.json(result);
  });
});
```

![[Pasted image 20231108005246.png]]


