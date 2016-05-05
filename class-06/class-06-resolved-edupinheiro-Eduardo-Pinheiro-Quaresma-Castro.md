# MongoDB - Aula 06 - Exercício
autor: Eduardo Pinheiro Quaresma Castro

## 01 - Pesquisa sem index para o campo 'name'
```js
Cybertron(mongod-3.0.9) be-mean> db.pokemons.getIndexes()
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

Cybertron(mongod-3.0.9) be-mean> db.pokemons.find({"name": "Rattata"}).explain('executionStats').executionStats.totalDocsExamined
610
Cybertron(mongod-3.0.9) be-mean> db.pokemons.find({"name": "Rattata"}).explain('executionStats').executionStats.executionTimeMillis
0
```
## 02 - Pesquisa com index para o campo 'name'
```js
Cybertron(mongod-3.0.9) be-mean> db.pokemons.createIndex({name: 1})
Cybertron(mongod-3.0.9) be-mean> db.pokemons.getIndexes()
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

Cybertron(mongod-3.0.9) be-mean> db.pokemons.find({"name": "Rattata"}).explain('executionStats').executionStats.totalDocsExamined
1
Cybertron(mongod-3.0.9) be-mean> db.pokemons.find({"name": "Rattata"}).explain('executionStats').executionStats.executionTimeMillis
0
```

## 03 - Pesquisa sem index para dois campos: 'name' e 'types: 'normal'
```js
Cybertron(mongod-3.0.9) be-mean> db.pokemons.getIndexes()
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

Cybertron(mongod-3.0.9) be-mean> db.pokemons.find({"name": "Rattata", types: 'normal'}).explain('executionStats').executionStats.totalDocsExamined
610
Cybertron(mongod-3.0.9) be-mean> db.pokemons.find({"name": "Rattata", types: 'normal'}).explain('executionStats').executionStats.executionTimeMillis
0
```

## 04 - Pesquisa com index para dois campos: 'name' e 'types: 'normal'
```js
Cybertron(mongod-3.0.9) be-mean> db.pokemons.getIndexes()
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
      "name": 1,
      "types": 1
    },
    "name": "name_1_types_1",
    "ns": "be-mean.pokemons"
  }
]

Cybertron(mongod-3.0.9) be-mean> db.pokemons.find({"name": "Rattata", types: 'normal'}).explain('executionStats').executionStats.totalDocsExamined
1
Cybertron(mongod-3.0.9) be-mean> db.pokemons.find({"name": "Rattata", types: 'normal'}).explain('executionStats').executionStats.executionTimeMillis
0
```