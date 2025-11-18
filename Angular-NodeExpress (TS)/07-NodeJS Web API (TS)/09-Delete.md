**trip.ts**
```ts
router.delete("/:id", (req, res) => {
  let id = +req.params.id;
  conn.query("delete from trip where idx = ?", [id], (err, result) => {
     if (err) throw err;
     res
       .status(200)
       .json({ affected_row: result.affectedRows });
  });
});
```

![[Pasted image 20231108074618.png]]
