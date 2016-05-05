# MongoDB - Aula 06 - Exercícios
## autor: Rafael Crispim Ignácio
1. Fazer uma query para o campo `name` utilizando `explain` para ver o resultado da busca

```js
be-mean> db.pokemons.find({ name: "Meowth" }).explain('executionStats').executionStats.totalDocsExamined
610
be-mean> db.pokemons.find({ name: "Meowth" }).explain('executionStats').executionStats.executionTimeMillis
1
```

1. Criar um `index` um para o campo `name`

```js
be-mean> db.pokemons.createIndex({ name: 1 })
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}
```

1. Refazer a query para o campo `name` utilizando `explain` para ver o resultado da busca

```js
be-mean> db.pokemons.find({ name: "Meowth" }).explain('executionStats').executionStats.totalDocsExamined
1
be-mean> db.pokemons.find({ name: "Meowth" }).explain('executionStats').executionStats.executionTimeMillis
0
```

1. Fazer uma query para dois campos juntos utilizando `explain` para ver o resultado da busca

```js
be-mean> db.pokemons.find({ hp: { $gt: 40 }, defense: { $gt: 60 } }).explain('executionStats').executionStats.totalDocsExamined
610
be-mean> db.pokemons.find({ hp: { $gt: 40 }, defense: { $gt: 60 } }).explain('executionStats').executionStats.executionTimeMillis
1
```

1. Criar um `index` para esses dois campos juntos

```js
be-mean> db.pokemons.createIndex({ hp: 1, defense: 1 })
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 2,
  "numIndexesAfter": 3,
  "ok": 1
}
```

1. Refazer a query para os dois campos juntos utilizando `explain` para ver o resultado da busca

```js
be-mean> db.pokemons.find({ hp: { $gt: 40 }, defense: { $gt: 60 } }).explain('executionStats').executionStats.totalDocsExamined
333
be-mean> db.pokemons.find({ hp: { $gt: 40 }, defense: { $gt: 60 } }).explain('executionStats').executionStats.executionTimeMillis
4
```
