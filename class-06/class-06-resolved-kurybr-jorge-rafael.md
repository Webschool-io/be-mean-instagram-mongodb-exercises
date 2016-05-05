# MongoDB - Aula 06 - Exercício
Autor: Jorge Rafael

## Fazer a query sem indíce para o campo 'name' ##
```javascript
db.pokemons.getIndexes()
db.pokemons.find({"name": /snorlax/i }).explain('executionStats').executionStats.totalDocsExamined
db.pokemons.find({"name": /snorlax/i }).explain('executionStats').executionStats.executionTimeMillis

> db.pokemons.getIndexes()
[
        {
                "v" : 1,
                "key" : {
                        "_id" : 1
                },
                "name" : "_id_",
                "ns" : "be-mean.pokemons"
        }
]
> db.pokemons.find({"name": /snorlax/i }).explain('executionStats').executionStats.totalDocsExamined
610
> db.pokemons.find({"name": /snorlax/i }).explain('executionStats').executionStats.executionTimeMillis
0

```
## Fazer a query com indíce para o campo 'name' ##
```javascript

db.pokemons.createIndex({ name: 1 })
db.pokemons.getIndexes()
db.pokemons.find({"name": /snorlax/i }).explain('executionStats').executionStats.totalDocsExamined
db.pokemons.find({"name": /snorlax/i }).explain('executionStats').executionStats.executionTimeMillis

> db.pokemons.getIndexes()
[
        {
                "v" : 1,
                "key" : {
                        "_id" : 1
                },
                "name" : "_id_",
                "ns" : "be-mean.pokemons"
        },
        {
                "v" : 1,
                "key" : {
                        "name" : 1
                },
                "name" : "name_1",
                "ns" : "be-mean.pokemons"
        }
]
> db.pokemons.find({"name": /snorlax/i }).explain('executionStats').executionStats.totalDocsExamined
1
> db.pokemons.find({"name": /snorlax/i }).explain('executionStats').executionStats.executionTimeMillis
1
>

```

## Fazer a query sem indíce para dois campos juntos ('speed' e 'type: ['normal']') ##

```javascript
db.pokemons.getIndexes()
db.pokemons.find({"speed": {$gte: 120}, "types": "normal"}).explain('executionStats').executionStats.totalDocsExamined
db.pokemons.find({"speed": {$gte: 120}, "types": "normal"}).explain('executionStats').executionStats.executionTimeMillis
> db.pokemons.getIndexes()
[
        {
                "v" : 1,
                "key" : {
                        "_id" : 1
                },
                "name" : "_id_",
                "ns" : "be-mean.pokemons"
        },
        {
                "v" : 1,
                "key" : {
                        "name" : 1
                },
                "name" : "name_1",
                "ns" : "be-mean.pokemons"
        }
]
> db.pokemons.find({"speed": {$gte: 120}, "types": "normal"}).explain('executionStats').executionStats.totalDocsExamined
610
> db.pokemons.find({"speed": {$gte: 120}, "types": "normal"}).explain('executionStats').executionStats.executionTimeMillis
0
>
```

## ## Fazer a query com indíce para dois campos juntos ('speed' e 'type: ['normal']') ## ##

```javascript
db.pokemons.createIndex({ "speed"  : 1, types: 1 })
db.pokemons.find({"speed": {$gte: 120}, "types": "normal"}).explain('executionStats').executionStats.totalDocsExamined
db.pokemons.find({"speed": {$gte: 120}, "types": "normal"}).explain('executionStats').executionStats.executionTimeMillis

> db.pokemons.createIndex({ "speed"  : 1, types: 1 })
{
        "createdCollectionAutomatically" : false,
        "numIndexesBefore" : 2,
        "numIndexesAfter" : 3,
        "ok" : 1
}
> db.pokemons.find({"speed": {$gte: 120}, "types": "normal"}).explain('executionStats').executionStats.totalDocsExamined
2
> db.pokemons.find({"speed": {$gte: 120}, "types": "normal"}).explain('executionStats').executionStats.executionTimeMillis
0
>
```
