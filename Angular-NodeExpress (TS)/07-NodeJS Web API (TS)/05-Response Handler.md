# Status Code
200 - OK
**201 - Created**
400 - Bad Request
...

**trip.ts**
```ts
router.post("/", (req, res) => {
let body = req.body;
res.status(201);
res.send("Get in trip.ts body: " + JSON.stringify(body));
});
```

![[Pasted image 20231108003319.png]]

# JSON

**trip.ts**
```ts
router.post("/", (req, res) => {
let body = req.body;
res.status(201);
res.send("Get in trip.ts body: " + JSON.stringify(body));
});
```

![[Pasted image 20231108003535.png]]

#### Chaining

**trip.ts**
```ts
router.post("/", (req, res) => {
  let body = req.body;
  res
    .status(201)
    .json({ text: "Get in trip.ts body: " + JSON.stringify(body) });
});
```
