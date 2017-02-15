# MongoDB - Aula 01 - Exercício
autor: Talita Araujo

## Importando os restaurantes

C:\Program Files\MongoDB\Server\3.2\bin>mongoimport --db test --collection restaurantes --drop --file C:\Users\talita.a.de.araujo\Documents\MongoDB\restaurantes.json
2016-10-18T15:33:37.174-0300    connected to: localhost
2016-10-18T15:33:37.177-0300    dropping: test.restaurantes
2016-10-18T15:33:40.170-0300    [#################.......] test.restaurantes    8.20MB/11.3MB (72.3%)
2016-10-18T15:33:40.704-0300    [########################] test.restaurantes    11.3MB/11.3MB (100.0%)
2016-10-18T15:33:40.706-0300    imported 25359 documents

## Contando os restaurantes
C:\Program Files\MongoDB\Server\3.2\bin>mongo
MongoDB shell version: 3.2.10
connecting to: test
MongoDB Enterprise > db.restaurantes.find({}).count()
25359

##