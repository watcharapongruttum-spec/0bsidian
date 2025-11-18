
# Path params

**trip.ts**
```ts
router.get("/:id", (req, res) => {
  res.send("Get in trip.ts id: " + req.params.id);
});
```

![[Pasted image 20231108000324.png]]

# Query params

**trip.ts**
```ts
router.get("/", (req, res) => {
  if (req.query.id) {
    res.send("Get in trip.ts Query id: " + req.query.id);
  } else {
    res.send("Get in trip.ts");
  }
});
```

![[Pasted image 20231108000602.png]]

# Body String

``` ts
router.post("/", (req, res) => {
  let body = req.body; 
  res.send("Get in trip.ts body: " + body);
});
```


![[Pasted image 20231108002037.png]]

##### Data is undefined

#### Using body-parser

```shell
npm install body-parser
```

**app.ts**
```ts
import { router as index } from "./api/index";
import { router as trip } from "./api/trip";
import bodyParser from "body-parser";

export const app = express();

app.use(bodyParser.text());
app.use("/", index);
app.use("/trip", trip);
```

![[Pasted image 20231108002557.png]]


![[Pasted image 20231108002511.png]]

**app.ts**
```ts
import { router as index } from "./api/index";
import { router as trip } from "./api/trip";
import bodyParser from "body-parser";

export const app = express();

app.use(bodyParser.text());
app.use(bodyParser.json());
app.use("/", index);
app.use("/trip", trip);
```

![[Pasted image 20231108002731.png]]

**trip.ts**
```ts
router.post("/", (req, res) => {
  let body = req.body; 
  res.send("Get in trip.ts body: " + JSON.stringify(body));
});
```

![[Pasted image 20231108002928.png]]

