Based on my old playlist on youtube
https://www.youtube.com/watch?v=AB7X6SdGZFg&list=PLd8BRUO4k5RlKRhcXDy9CBM2tzow6MasG

# Why TypeScript ?

https://dev.to/cristain/how-to-set-up-typescript-with-nodejs-and-express-2023-gf

# Create NodeJS Project

``` shell
mkdir node-expres-mysql
cd node-expres-mysql
npm init --yes
```

### Install TypeScript 
``` shell
npm install -D typescript ts-node-dev
npx tsc --init
code .
```

**tsconfig.json**
![[Pasted image 20231107214443.png]]

```shell
npm install express @types/express
```


#### Create Server file

![[Pasted image 20231107214834.png]]

**server.ts**
```ts
import http from "http";

const port = process.env.port || 3000;
const server = http.createServer();

server.listen(port, () => {
  console.log("Server is started");
});
 ```

```shell
npx ts-node server.ts 
```

**Server started but nothing show**
![[Pasted image 20231107230321.png]]

#### Create Express Application

![[Pasted image 20231107230416.png]]

**app.ts**
```ts
import express from "express";

export const app = express();
app.use("/", (req, res) => {
  res.send("Hello World!!!");
});
```

**server.ts**
```ts
import http from "http";
import { app } from "./app";

const port = process.env.port || 3000;
const server = http.createServer(app);

server.listen(port, () => {
  console.log("Server is started");
});
```

![[Pasted image 20231107230709.png]]

![[Pasted image 20231107230738.png]]

![[Pasted image 20231107230828.png]]

