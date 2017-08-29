---
layout: post #post
title: Get Start with Mongodb #post title
categories: Database MEAN #post category, seperated by space
tags: Database MEAN Mongodb #post tag, seperated by space
---


## Databases
1. database: can have relations between tables

2. relational db -- non-relational db, tables -- collections, object -- document


## Mongodb
1. Find how to download on mongodb website, install using homebrew is recommended.

2. `which mongo` check the installation directory of mongodb

3. Node.js: a platform

4. Packages in node: file, request handling, express


5. Run mongodb on mac: mongod

    - if it shutting down, maybe permission problem, using sudo su, then mongod

    - in a new terminal, mongo, it is running

6. Insert examples: db.collectionName.functionName

    ```
    //insert 1
    db.trainees.insert({
        "id":2,
        "name":"yy2",
        "place":"nj2",
        "phone":"1232"
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

7. Retrieve examples

    ```
    //retrieve and format
    db.trainees.find().pretty()
    ```

8. Find specific document

    ```
    db.trainees.find({"id":1,"place":"nj"}).pretty()
    //or
    db.trainees.find({
        $or:[
            {"id":11},
            {"place":"nj"}
        ]
        }).pretty()
    ```

9. Limit show what props of result, second param in find(), `"_id":0` hide the auto-id

    ```
    db.trainees.find({},{"id":1,"place":"nj","_id":0}).pretty()
    ```

10. More `$`

    ```
    db.trainees.find({ "id":{$gt:2}}).pretty()
    db.trainees.find({ "id":{$in:[1,11]}}).pretty()
    ```

11. Update: set

    ```
     db.trainees.update({"id":12},{
                $set:{
                    "name": "newname"
                }
            })
    db.trainees.update({"id":12},{
            $set:{
                "org": "xyorg"
            }
        })
     db.trainees.update({},{
            $set:{
                "org": "xyorg"
            }
        },{"multi":true})
    //unset
     db.trainees.update({},{
            $unset:{
                "org": ""
            }
        },{"multi":true})
    ```

12. remove

    ```
    db.trainees.remove({"id":12});
    ```