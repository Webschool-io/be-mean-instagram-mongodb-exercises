# MongoDB - Aula 06 - Exercício
autor: Wladek Zacharski

## 1. Realizando a query pelo name sem indexe 

```
> db.pokemons.getIndexes()
[
  {
    "v" : 1,
    "key" : {
      "_id" : 1
    },
    "name" : "_id_",
    "ns" : "be-mean-pokemons.pokemons"
  }
]
> db.pokemons.find({name: /cartepy/i}).explain('executionStats').executionStats.executionTimeMillis
1

```

## 2. Realizando a query pelo name com index criado

```
> db.pokemons.getIndexes()
[
  {
    "v" : 1,
    "key" : {
      "_id" : 1
    },
    "name" : "_id_",
    "ns" : "be-mean-pokemons.pokemons"
  },
  {
    "v" : 1,
    "key" : {
      "name" : 1
    },
    "name" : "name_1",
    "ns" : "be-mean-pokemons.pokemons"
  }
]
> db.pokemons.find({name: /cartepy/i}).explain('executionStats').executionStats.executionTimeMillis
0

```


## 3. Realizando a query com dois campos juntos sem o index criado

```
> db.pokemons.getIndexes()
[
  {
    "v" : 1,
    "key" : {
      "_id" : 1
    },
    "name" : "_id_",
    "ns" : "be-mean-pokemons.pokemons"
  }
]
> db.pokemons.find({$and:[{defense: {$gte: 90}},{attack: {$gte: 90}}]}).explain('executionStats').executionStats.executionTimeMillis
0

```

## 4. Realizando a query com dois campos juntos e com os dois indexes

```
> db.pokemons.getIndexes()
[
  {
    "v" : 1,
    "key" : {
      "_id" : 1
    },
    "name" : "_id_",
    "ns" : "be-mean-pokemons.pokemons"
  },
  {
    "v" : 1,
    "key" : {
      "attack" : 1
    },
    "name" : "attack_1",
    "ns" : "be-mean-pokemons.pokemons",
    "defense" : 1
  },
  {
    "v" : 1,
    "key" : {
      "defense" : 1
    },
    "name" : "defense_1",
    "ns" : "be-mean-pokemons.pokemons"
  }
]
> db.pokemons.find({$and:[{defense: {$gte: 90}},{attack: {$gte: 90}}]}).explain('executionStats').executionStats.executionTimeMillis
0

```