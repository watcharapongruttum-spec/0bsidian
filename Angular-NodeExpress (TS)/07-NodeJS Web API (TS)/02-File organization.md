![[Pasted image 20231107234900.png]]

**default.ts**
```ts
import express from "express";

export const router = express.Router();

router.get('/', (req, res)=>{
    res.send('Get in index.ts');
});

```

#### link app.ts to index.ts
**app.ts**
```ts
import express from "express";
import { router as index } from "./api/index";

export const app = express();

app.use("/", index);
// app.use("/", (req, res) => {
//   res.send("Hello World!!!");
// });
```

![[Pasted image 20231107235026.png]]

#### create trip.ts
![[Pasted image 20231107235115.png]]

**trip.ts**
```ts
import express from "express";

export const router = express.Router();

router.get("/", (req, res) => {
  res.send("Get in trip.ts");
});
```

#### link app.ts to trip.ts
**app.ts**
```ts
import express from "express";
import { router as index } from "./api/index";
import { router as trip } from "./api/trip";

export const app = express();

app.use("/", index);
app.use("/trip", trip);

```

![[Pasted image 20231107235412.png]]


