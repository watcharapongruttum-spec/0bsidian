
# CORS

```shell
npm install cors @types/cors
```


**app.ts**
```ts
import cors from "cors";

... 

app.use(
  cors({
    origin: "http://yourapp.com",
  })
);
```

![[Pasted image 20231108113429.png]]

Test Calling from React (Previous section)

**tripapi.tsx**
``` ts
import axios from "axios";
import { TripsGetResponse } from "../model/TripsGetResponse";

// const HOST: string = "http://localhost/tripbooking";
const HOST: string = "http://localhost:3000";

export class TripService {
  async getAllTrips() {
    const url = HOST + "/trip";
    const response = await axios.get(url);
    const trips: TripsGetResponse[] = response.data;
    return trips;
  }
  async getTripsById(id: number) {
    const url = HOST + `/trip/${id}`;
    const response = await axios.get(url);
    const trips: TripsGetResponse[] = response.data;
    return trips;
  }
}
```

![[Pasted image 20231108114535.png]]

**app.ts**
```ts
import cors from "cors";

... 

app.use(
  cors({
    origin: "*",
  })
);
```

![[Pasted image 20231108113537.png]]


# JWT

```shell
npm install express-jwt
npm install jsonwebtoken
```

**jwtauthen.ts**
```js
import { expressjwt, Request as JWTRequest } from "express-jwt";
import jwt from "jsonwebtoken";

export const secret = "this-is-top-secret";
export const jwtAuthen = expressjwt({
  secret: secret,
  algorithms: ["HS256"],
}).unless({
  path: ["/", "/register", "/login", "/testtoken"],
});

export function generateToken(payload: any, secretKey: string): string {
  const token: string = jwt.sign(payload, secretKey, {
    expiresIn: "30d", // expires in 30 days
    issuer: "CS-MSU"
  });
  return token;
}

export function verifyToken(
  token: string,
  secretKey: string
): { valid: boolean; decoded?: any; error?: string } {
  try {
    const decodedPayload: any = jwt.verify(token, secretKey);
    return { valid: true, decoded: decodedPayload };
  } catch (error) {
    return { valid: false, error: JSON.stringify(error) };
  }
}
```

**app.ts**
```ts
import { jwtAuthen, generateToken, secret } from "./jwtauthen";

...

app.use(jwtAuthen, (err: any, req: any, res: any, next: any) => {
  if (err.name === "UnauthorizedError") {
    res.status(err.status).send({ message: err.message });
    return;
  }
  next();
});

// Test Token
app.use("/testtoken", (req, res) => {
    const payload: any = { username: "Aj.M" }; 
    const jwttoken = generateToken(payload, secret);
  res.status(200).json({
    token: jwttoken,
  });
});
```

![[Pasted image 20231108142320.png]]

![[Pasted image 20231108142411.png]]


http://localhost:3000/trip
![[Pasted image 20231108144347.png]]

![[Pasted image 20231108144629.png]]