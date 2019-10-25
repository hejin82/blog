---
layout: post
title:  "install MongoDB on Mac"
date:   2019-10-25 01:46:40 +0900
categories: jekyll update
---
+ Comparing MongoDB versus SQL syntax

| SQL      | MongoDB |
| ----------- | ----------- |
| select * from books      | db.books.find()       |
| select * from books where id = 3   | db.books.find({id : 3})        |
| select * from books where name like 'Oliver%'      | db.books.find({ name: /^Oliver/})       |
| select * from books where name like '%Oliver%'   | b.books.find({ name: /Oliver/})        |
| select * from books where published_date > '2011-8-01'      | db.books.find({published_date: {$gt: ISODate("2011-8-01")}})       |
| select name from books order by published_data   | db.books.find( {}, name: 1}).sort({published_date: 1})        |
| select name from books order by published_date desc      | db.books.find( {}, name: 1}).sort({published_date: -1})       |
| select votes.name from books join votes where votes.book_id = books.id   | db.books.find( {votes: {$exists: 1}}, {votes.name: 1})        |


