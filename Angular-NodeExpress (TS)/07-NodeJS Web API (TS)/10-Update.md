**trip.ts**
```ts
router.put("/:id", (req, res) => {
  let id = +req.params.id;
  let trip: TripPostRequest = req.body;
  let sql =
    "update  `trip` set `name`=?, `country`=?, `destinationid`=?, `coverimage`=?, `detail`=?, `price`=?, `duration`=? where `idx`=?";
  sql = mysql.format(sql, [
    trip.name,
    trip.country,
    trip.destinationid,
    trip.coverimage,
    trip.detail,
    trip.price,
    trip.duration,
    id
  ]);
  conn.query(sql, (err, result) => {
    if (err) throw err;
    res
      .status(201)
      .json({ affected_row: result.affectedRows });
  });
});
```

![[Pasted image 20231108075219.png]]

# Dynamic fields update
Merge to original data
- Get original first
- Merge new

**dbconnect.ts**
```ts
export const queryAsync = util.promisify(conn.query).bind(conn);
```

**trip.ts**
```ts
import { conn, queryAsync } from "../dbconnect";

...

router.put("/:id", async (req, res) => {
  let id = +req.params.id;
  let trip: TripPostRequest = req.body;
  let tripOriginal: TripPostRequest | undefined;

  let sql = mysql.format("select * from trip where idx = ?", [id]);

  let result = await queryAsync(sql);
  const rawData = JSON.parse(JSON.stringify(result));
  console.log(rawData);
  tripOriginal = rawData[0] as TripPostRequest;
  console.log(tripOriginal);

  let updateTrip = {...tripOriginal, ...trip};
  console.log(trip);
  console.log(updateTrip);

    sql =
      "update  `trip` set `name`=?, `country`=?, `destinationid`=?, `coverimage`=?, `detail`=?, `price`=?, `duration`=? where `idx`=?";
    sql = mysql.format(sql, [
      updateTrip.name,
      updateTrip.country,
      updateTrip.destinationid,
      updateTrip.coverimage,
      updateTrip.detail,
      updateTrip.price,
      updateTrip.duration,
      id,
    ]);
    conn.query(sql, (err, result) => {
      if (err) throw err;
      res.status(201).json({ affected_row: result.affectedRows });
    });
});
```

![[Pasted image 20231108093806.png]]

![[Pasted image 20231108093849.png]]

