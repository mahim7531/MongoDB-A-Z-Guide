# 🟢 MongoDB A–Z Guide

A complete beginner-to-advanced guide for working with MongoDB in modern full-stack applications (MERN, Next.js, APIs).

---

# 📌 What is MongoDB?

MongoDB is a **NoSQL, document-based database** that stores data in **JSON-like format (BSON)**.

✔ Flexible schema
✔ High performance
✔ Scalable (horizontal scaling)
✔ Perfect for MERN stack

---

# 🧱 Core Concepts

## 1. Database

A container for collections.

## 2. Collection

Equivalent to a table (but schema-less).

## 3. Document

A single record (JSON object).

```json
{
  "name": "John",
  "age": 25,
  "skills": ["Node", "React"]
}
```

---

# 🔤 A–Z MongoDB Concepts

## 🅰️ Aggregation

Used for advanced data processing.

```js
db.users.aggregate([
  { $match: { age: { $gt: 18 } } },
  { $group: { _id: "$age", count: { $sum: 1 } } }
])
```

---

## 🅱️ BSON

Binary JSON format MongoDB uses internally.

---

## 🅲 Collection

Group of documents.

```js
db.createCollection("users")
```

---

## 🅳 Document

A JSON-like data structure.

---

## 🅴 Embedded Documents

Nested objects inside documents.

```json
{
  "name": "John",
  "address": {
    "city": "Dhaka"
  }
}
```

---

## 🅵 Find (Read Data)

```js
db.users.find()
db.users.find({ age: { $gt: 20 } })
```

---

## 🅶 GridFS

Used to store large files (images/videos).

---

## 🅷 Indexes

Improve query performance.

```js
db.users.createIndex({ email: 1 })
```

---

## 🅸 Insert

```js
db.users.insertOne({ name: "Mahim", age: 22 })
db.users.insertMany([{ name: "A" }, { name: "B" }])
```

---

## 🅹 JSON

MongoDB works with JSON-like structure.

---

## 🅺 Key-Value

MongoDB stores data as key-value pairs.

---

## 🅻 Lookup (Join)

```js
db.orders.aggregate([
  {
    $lookup: {
      from: "users",
      localField: "userId",
      foreignField: "_id",
      as: "user"
    }
  }
])
```

---

## 🅼 Mongoose (Node.js ODM)

```js
import mongoose from "mongoose";

mongoose.connect("mongodb://localhost:27017/mydb");

const UserSchema = new mongoose.Schema({
  name: String,
  age: Number
});

export default mongoose.model("User", UserSchema);
```

---

## 🅽 NoSQL

Schema-less, flexible database.

---

## 🅾️ Operators

```js
$gt  // greater than
$lt  // less than
$in  // matches values in array
$or  // logical OR
```

---

## 🅿️ Projection

```js
db.users.find({}, { name: 1, _id: 0 })
```

---

## 🆀 Query

```js
db.users.find({ name: "Mahim" })
```

---

## 🆁 Replication

Copies data across servers for reliability.

---

## 🆂 Schema Design

Flexible, but should be structured.

✔ Embed vs Reference
✔ Avoid deep nesting

---

## 🆃 Transactions

```js
session.startTransaction()
```

---

## 🆄 Update

```js
db.users.updateOne(
  { name: "Mahim" },
  { $set: { age: 23 } }
)
```

---

## 🆅 Validation

```js
db.createCollection("users", {
  validator: {
    $jsonSchema: {
      bsonType: "object",
      required: ["name"]
    }
  }
})
```

---

## 🆆 Write Concern

Controls write acknowledgment.

---

## 🆇 $expr

```js
db.users.find({
  $expr: { $gt: ["$age", 18] }
})
```

---

## 🆈 Yield

MongoDB can pause operations to allow others.

---

## 🆉 Zone Sharding

Distributes data across clusters.

---

# 🔥 CRUD Operations (Important)

## Create

```js
db.users.insertOne({ name: "Mahim" })
```

## Read

```js
db.users.find()
```

## Update

```js
db.users.updateOne({}, { $set: { age: 25 } })
```

## Delete

```js
db.users.deleteOne({ name: "Mahim" })
```

---

# ⚡ MongoDB with Node.js (Express)

```js
import express from "express";
import mongoose from "mongoose";

const app = express();
app.use(express.json());

mongoose.connect("mongodb://localhost:27017/test");

const User = mongoose.model("User", {
  name: String,
});

app.post("/user", async (req, res) => {
  const user = await User.create(req.body);
  res.json(user);
});

app.get("/user", async (req, res) => {
  const users = await User.find();
  res.json(users);
});

app.listen(4000);
```

---

# 🚀 Best Practices

✔ Use indexes for performance
✔ Keep documents small
✔ Use aggregation instead of loops
✔ Validate data
✔ Use Mongoose in Node.js projects

---

# ❌ Common Mistakes

❌ Over-nesting documents
❌ Not indexing frequently queried fields
❌ Storing unnecessary data
❌ Ignoring schema design

---

# 📚 Useful Commands

```bash
mongosh
show dbs
use mydb
show collections
```

---

# 🎯 Conclusion

MongoDB is a powerful, flexible database perfect for modern applications.
Master CRUD, Aggregation, and Schema Design to become production-ready.

---

---
