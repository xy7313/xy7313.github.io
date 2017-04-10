---
layout: post #post
title: Start from Java 4 #post title
categories: Java #post category, seperated by space
tags: Java #post tag, seperated by space
---


## Collections
1. from util package, an interface
2. including:
    - List
    - Set: doesn't in order, no duplicates
    - Map
    - Queue: FIFO
3. CRUD: create, retrieve, update, delete
4. Collection(class):
    - sort();
    - max();
    - min();
5. Iterator: thread safe vs. Enumeration: thread not sage

6. hashmap:
    1. sort key :`Map<Integer, String> map = new TreeMap<Integer, String>(hmap); ` whatever the key is, when you put them to treemap, your key is automatically sorted.
7. So if we want to use HashSet<self-defined object>, we need to override both hashcode() and equal(). These two method are both from java....object class

8. Date & Calendar
```
Calender cal = Calendar.getInstance();
cal.set(2017,0,1);
//month start from 0
```
9. StringTokenizer: like split
10. Random: class, function called next.int()
11. author reference to book
12. database driver
13. 

## JDBC