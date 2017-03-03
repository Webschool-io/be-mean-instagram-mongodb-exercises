## Buscando pokemon pelo nome sem Index.
```
Leonardo-Larocca(mongod-3.4.0) be-mean> db.pokemons.find({"name":"Pikachu"}).explain('executionStats').executionStats.totalDocsExamined
610

Leonardo-Larocca(mongod-3.4.0) be-mean> db.pokemons.find({"name":"Pikachu"}).explain('executionStats').executionStats.executionTimeMillis
1

```

## Buscando pokemon pelo nome e ataque maior que 100 sem Index
```
Leonardo-Larocca(mongod-3.4.0) be-mean> db.pokemons.find({$or:[{name: 'Pikachu'},{attack:{gte: 100}}]}).explain('executionStats').executionStats.totalDocsExamined
610

Leonardo-Larocca(mongod-3.4.0) be-mean> db.pokemons.find({$or:[{name: 'Pikachu'},{attack:{gte: 100}}]}).explain('executionStats').executionStats.executionTimeMillis
1
```

## Buscando pokemon pelo nome com Index
```
Leonardo-Larocca(mongod-3.4.0) be-mean> db.pokemons.createIndex({name: 1})

{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}
Leonardo-Larocca(mongod-3.4.0) be-mean> db.pokemons.getIndexes()
[
  {
    "v": 2,
    "key": {
      "_id": 1
    },
    "name": "_id_",
    "ns": "be-mean.pokemons"
  },
  {
    "v": 2,
    "key": {
      "name": 1
    },
    "name": "name_1",
    "ns": "be-mean.pokemons"
  }
]
Leonardo-Larocca(mongod-3.4.0) be-mean> db.pokemons.find({"name":"Pikachu"}).explain('executionStats').executionStats.totalDocsExamined
1
Leonardo-Larocca(mongod-3.4.0) be-mean> db.pokemons.find({"name":"Pikachu"}).explain('executionStats').executionStats.executionTimeMillis
0
Leonardo-Larocca(mongod-3.4.0) be-mean>
```

##Buscando pokemon pelo nome e ataque com Index
```
Leonardo-Larocca(mongod-3.4.0) be-mean> db.pokemons.dropIndex({name: 1})
{
  "nIndexesWas": 2,
  "ok": 1
}
Leonardo-Larocca(mongod-3.4.0) be-mean> db.pokemons.createIndex({name: 1, attack: 1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}
Leonardo-Larocca(mongod-3.4.0) be-mean> db.pokemons.getIndexes()
[
  {
    "v": 2,
    "key": {
      "_id": 1
    },
    "name": "_id_",
    "ns": "be-mean.pokemons"
  },
  {
    "v": 2,
    "key": {
      "name": 1,
      "attack": 1
    },
    "name": "name_1_attack_1",
    "ns": "be-mean.pokemons"
  }
]

Leonardo-Larocca(mongod-3.4.0) be-mean> db.pokemons.find({$or:[{name: 'Pikachu'},{attack:{gte: 100}}]}).explain('executionStats').executionStats.totalDocsExamined
610

Leonardo-Larocca(mongod-3.4.0) be-mean> db.pokemons.find({$or:[{name: 'Pikachu'},{attack:{gte: 100}}]}).explain('executionStats').executionStats.executionTimeMillis
1
```


db.my.poke.createIndex({name: 1})
db.my.poke.createIndex({name: 1, attack: 1})
