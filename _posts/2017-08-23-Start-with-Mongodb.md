---
layout: post #post
title: Get Start with Mongodb #post title
categories: Mongodb MEAN #post category, seperated by space
tags: Database MEAN #post tag, seperated by space
---

1. Find how to download on mongodb website, install using homebrew is recommended.

2. `which mongo` check the installation directory of mongodb

3. Node.js: a platform

4. packages in node

file, request handling, express

//database: can have relations between tables
//relational db -- non-relational db, tables -- collections, object -- document

5. run mongodb on mac: mongod

    - if it shutting down, maybe permission problem, using sudo su, then mongod

    - in a new terminal, mongo, it is running

6. insert examples

```
//insert 1
db.trainees.insert({
    "id":1,
    "name":"yy",
    "place":"nj",
    "phone":"123"
})

//insert many
db.trainees.insertMany([
    {
        "id":12,
        "name":"yy12",
        "place":"nj12",
        "phone":"12312"
    },
    {
        "id":11,
        "name":"yy11",
        "place":"nj11",
        "phone":"12311"
    }
])
```

7. retrieve examples

```
//retrieve and format
db.trainees.find().pretty()
```