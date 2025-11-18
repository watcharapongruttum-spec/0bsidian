
# Using of multer

``` shell
npm install multer @types/multer
```

Create upload folder
![[Pasted image 20231108112223.png]]

**app.ts**
```ts
app.use("/upload", upload);
app.use("/uploads", express.static("uploads"));
```

**upload.ts**
```ts
import express from "express";
import path from "path";
import multer from "multer";

export const router = express.Router();

class FileMiddleware {
  filename = "";
  public readonly diskLoader = multer({
    storage: multer.diskStorage({
      destination: (_req, _file, cb) => {
        cb(null, path.join(__dirname, "../uploads"));
      },
      filename: (req, file, cb) => {
        const uniqueSuffix =
          Date.now() + "-" + Math.round(Math.random() * 10000);
        this.filename = uniqueSuffix + "." + file.originalname.split(".").pop();
        cb(null, this.filename);
      },
    }),
    limits: {
      fileSize: 67108864, // 64 MByte
    },
  });
}

const fileUpload = new FileMiddleware();
router.post("/", fileUpload.diskLoader.single("file"), (req, res) => {
  res.json({ filename: "/uploads/" + fileUpload.filename });
});
```


![[Pasted image 20231108112730.png]]

http://localhost:3000/uploads/1689007304324.png
