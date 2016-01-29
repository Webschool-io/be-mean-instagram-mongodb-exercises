# MongoDB - Aula 06 - Exercício
autor: Airton Vancin Junior

## Fazer a query sem indíce para o campo 'name' ##
```
linux(mongod-3.0.7) be-mean> db.pokemons.getIndexes()
[
  {
    "v": 1,
    "key": {
      "_id": 1
    },
    "name": "_id_",
    "ns": "be-mean.pokemons"
  }
]
linux(mongod-3.0.7) be-mean> db.pokemons.find({"name": "Rattata"}).explain('executionStats').executionStats.totalDocsExamined
610

linux(mongod-3.0.7) be-mean> db.pokemons.find({"name": "Rattata"}).explain('executionStats').executionStats.executionTimeMillis
1
```

## Fazer a query com indíce para o campo 'name' ##

```
linux(mongod-3.0.7) be-mean> db.pokemons.createIndex({ name: 1 })
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}
linux(mongod-3.0.7) be-mean> db.pokemons.getIndexes()
[
  {
    "v": 1,
    "key": {
      "_id": 1
    },
    "name": "_id_",
    "ns": "be-mean.pokemons"
  },
  {
    "v": 1,
    "key": {
      "name": 1
    },
    "name": "name_1",
    "ns": "be-mean.pokemons"
  }
]
linux(mongod-3.0.7) be-mean> db.pokemons.find({"name": "Rattata"}).explain('executionStats').executionStats.totalDocsExamined
1
linux(mongod-3.0.7) be-mean> db.pokemons.find({"name": "Rattata"}).explain('executionStats').executionStats.executionTimeMillis
0

```

## Fazer a query sem indíce para dois campos juntos ('speed' e 'type: ['normal']') ##

```
linux(mongod-3.0.7) be-mean> db.pokemons.getIndexes()
[
  {
    "v": 1,
    "key": {
      "_id": 1
    },
    "name": "_id_",
    "ns": "be-mean.pokemons"
  }
]

linux(mongod-3.0.7) be-mean> db.pokemons.find({"speed": {$gte: 120}, "types": "normal"}).explain('executionStats').executionStats.totalDocsExamined
610
linux(mongod-3.0.7) be-mean> db.pokemons.find({"speed": {$gte: 120}, "types": "normal"}).explain('executionStats').executionStats.executionTimeMillis
1
```

## ## Fazer a query com indíce para dois campos juntos ('speed' e 'type: ['normal']') ## ##

```
linux(mongod-3.0.7) be-mean> db.pokemons.getIndexes()
[
  {
    "v": 1,
    "key": {
      "_id": 1
    },
    "name": "_id_",
    "ns": "be-mean.pokemons"
  },
  {
    "v": 1,
    "key": {
      "speed": 1,
      "types": 1
    },
    "name": "speed_1_types_1",
    "ns": "be-mean.pokemons"
  }
]
linux(mongod-3.0.7) be-mean> db.pokemons.find({"speed": {$gte: 120}, "types": "normal"}).explain('executionStats').executionStats.totalDocsExamined
2
linux(mongod-3.0.7) be-mean> db.pokemons.find({"speed": {$gte: 120}, "types": "normal"}).explain('executionStats').executionStats.executionTimeMillis
0

```


