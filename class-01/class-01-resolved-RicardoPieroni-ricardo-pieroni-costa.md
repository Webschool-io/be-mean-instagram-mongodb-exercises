
C:\Program Files\MongoDB\Server\3.2\bin>mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.js
on
2016-03-22T17:24:38.273-0300    connected to: localhost
2016-03-22T17:24:38.277-0300    dropping: be-mean.restaurantes
2016-03-22T17:24:41.265-0300    [###############.........] be-mean.restaurantes 7.2 MB/11.4 MB (63.4%)
2016-03-22T17:24:42.739-0300    [########################] be-mean.restaurantes 11.4 MB/11.4 MB (100.0%)
2016-03-22T17:24:42.740-0300    imported 25359 documents

C:\Program Files\MongoDB\Server\3.2\bin>mongo
2016-03-22T17:25:06.860-0300 I CONTROL  [main] Hotfix KB2731284 or later update is not installed, will zero-out data fil
es
MongoDB shell version: 3.2.4
connecting to: test
Server has startup warnings:
2016-03-22T10:11:47.402-0300 I CONTROL  [initandlisten]
2016-03-22T10:11:47.408-0300 I CONTROL  [initandlisten] ** WARNING: This 32-bit MongoDB binary is deprecated
2016-03-22T10:11:47.414-0300 I CONTROL  [initandlisten]
2016-03-22T10:11:47.417-0300 I CONTROL  [initandlisten]
2016-03-22T10:11:47.423-0300 I CONTROL  [initandlisten] ** NOTE: This is a 32 bit MongoDB binary.
2016-03-22T10:11:47.428-0300 I CONTROL  [initandlisten] **       32 bit builds are limited to less than 2GB of data (or
less with --journal).
2016-03-22T10:11:47.437-0300 I CONTROL  [initandlisten] **       Note that journaling defaults to off for 32 bit and is
currently off.
2016-03-22T10:11:47.446-0300 I CONTROL  [initandlisten] **       See http://dochub.mongodb.org/core/32bit
2016-03-22T10:11:47.451-0300 I CONTROL  [initandlisten]
> use be-mean
switched to db be-mean
> db.restaurantes.find({}).count()
25359
> ^C
bye

C:\Program Files\MongoDB\Server\3.2\bin>