
**trip.ts**
```ts
router.get("/:id", (req, res) => {
  let id = +req.params.id;
  conn.query("select * from trip where idx = ?" , [id], (err, result, fields) => {
  if (err) throw err;
    res.json(result);
  });
});
```

![[Pasted image 20231108005733.png]]

# Multiple Query Params as Option

```ts
router.get("/search/fields", (req, res) => {
  conn.query(
    "select * from trip where (idx IS NULL OR idx = ?) OR (name IS NULL OR name like ?)",
    [ req.query.id, "%" + req.query.name + "%"],
    (err, result, fields) => {
    if (err) throw err;
      res.json(result);
    }
  );
});
```

![[Pasted image 20231108011415.png]]

