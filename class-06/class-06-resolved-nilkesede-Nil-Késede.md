# MongoDB - Aula 06 - Exercício
> Autor: Nil Késede

## Fazer uma query para o campo `name` com ultilizar o `explain` para ver a performance da busca
```js
> db.pokemons.find({ name: /pikachu/i }).explain('executionStats').executionStats.totalDocsExamined
610

> db.pokemons.find({ name: /pikachu/i }).explain('executionStats').executionStats.executionTimeMillis
3
```

## Criar um `index` para o campo `name`
```js
> db.pokemons.createIndex({ name: 1 })
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}

> db.pokemons.getIndexes()
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
```

## Refazer a query para o campo `name` utilizando `explain` para ver a performance da busca

```js
db.pokemons.find({ name: /pikachu/i }).explain('executionStats').executionStats.totalDocsExamined
1

db.pokemons.find({ name: /pikachu/i }).explain('executionStats').executionStats.executionTimeMillis
2
```

##4. Fazer uma query para dois campos juntos utilizando `explain` para ver a performance da busca

```js
> db.pokemons.find({ $and:[ { defense: { $gt: 60 } }, { speed: { $gt: 50 } } ] }).explain('executionStats').executionStats.totalDocsExamined
610

> db.pokemons.find({ $and:[ { defense: { $gt: 60 } }, { speed: { $gt: 50 } } ] }).explain('executionStats').executionStats.executionTimeMillis
2
```

## Criar um `index` para esses dois campos juntos
```js
> db.pokemons.createIndex({ defense: 1, speed: 1 })
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 2,
  "numIndexesAfter": 3,
  "ok": 1
}

> db.pokemons.getIndexes()
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
  },
  {
    "v": 1,
    "key": {
      "defense": 1,
      "speed": 1
    },
    "name": "defense_1_speed_1",
    "ns": "be-mean.pokemons"
  }
]

```

## Refazer a query para os dois campos juntos utilizando `explain` para ver a performance da busca
```js
> db.pokemons.find({ $and:[ { defense: { $gt: 60 } }, { speed: { $gt: 50 } } ] }).explain('executionStats').executionStats.totalDocsExamined
236

> db.pokemons.find({ $and:[ { defense: { $gt: 60 } }, { speed: { $gt: 50 } } ] }).explain('executionStats').executionStats.executionTimeMillis
1
```
