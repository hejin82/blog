---
layout: post
title:  "install MongoDB on Mac"
date:   2019-10-26 00:46:40 +0900
categories: jekyll update
---
+ User brew:

```bash
$ brew tap mongodb/brew
$ brew install mongodb-community
==> Installing mongodb-community from mongodb/brew
==> Downloading https://fastdl.mongodb.org/osx/mongodb-macos-x86_64-4.2.1.tgz
######################################################################## 100.0%
==> Caveats
To have launchd start mongodb/brew/mongodb-community now and restart at login:
  brew services start mongodb/brew/mongodb-community
Or, if you don't want/need a background service you can just run:
  mongod --config /usr/local/etc/mongod.conf
==> Summary
🍺  /usr/local/Cellar/mongodb-community/4.2.1: 21 files, 273.5MB, built in 12 minutes 30 seconds

```

+ The default mongod.conf:

`/usr/local/etc/mongod.conf`

```
systemLog:
  destination: file
  path: /usr/local/var/log/mongodb/mongo.log
  logAppend: true
storage:
  dbPath: /usr/local/var/mongodb
net:
  bindIp: 127.0.0.1
```

+ To run MongoDB in the foreground

```
$ mongod --config /usr/local/etc/mongod.conf
```

+ To run in the background instead, include --fork

```
$ mongod --config /usr/local/etc/mongod.conf --fork
```

+ Connect to MongoDB

```
mongo
```

+ To display the database you are using

```
db
```

+ To switch databases

```
use <db>
```

+ Insert and Query

```
$ mongo
MongoDB shell version v4.2.1
connecting to: mongodb://127.0.0.1:27017/?compressors=disabled&gssapiServiceName=mongodb
Implicit session: session { "id" : UUID("c899fc3c-4ca8-4634-85af-0b0618ed4a53") }
MongoDB server version: 4.2.1
Server has startup warnings: 
2019-10-25T22:39:30.439+0900 I  CONTROL  [initandlisten] 
2019-10-25T22:39:30.439+0900 I  CONTROL  [initandlisten] ** WARNING: Access control is not enabled for the database.
2019-10-25T22:39:30.439+0900 I  CONTROL  [initandlisten] **          Read and write access to data and configuration is unrestricted.
2019-10-25T22:39:30.439+0900 I  CONTROL  [initandlisten] ** WARNING: You are running this process as the root user, which is not recommended.
2019-10-25T22:39:30.439+0900 I  CONTROL  [initandlisten] 
2019-10-25T22:39:30.439+0900 I  CONTROL  [initandlisten] 
2019-10-25T22:39:30.439+0900 I  CONTROL  [initandlisten] ** WARNING: soft rlimits too low. Number of files is 256, should be at least 1000
---
Free Monitoring URL:
https://cloud.mongodb.com/freemonitoring/cluster/WMRH4FGOITYQUMXFGUUM5QCV3BNCQQA5
---
> use book
switched to db book
> db.shelf.save({name: 'mongodb'})
WriteResult({ "nInserted" : 1 })
> db.shelf.find()
{ "_id" : ObjectId("5db2fe3ba7fc93125fdeb970"), "name" : "mongodb" }
> db.shelf.find({name: 'mongodb'})
{ "_id" : ObjectId("5db2fe3ba7fc93125fdeb970"), "name" : "mongodb" }
> 
```
