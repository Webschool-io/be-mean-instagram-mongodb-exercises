#MongoDB - Aula 06 - Exercícios
autor: Dariano Soares

##1. Fazer uma query para o campo `name` utilizando `explain` para ver o resultado da busca
```js
db.pokemons.find({name : /magneton/i}).explain('executionStats').executionStats.totalDocsExamined

610
```

##2. Criar um `index` um para o campo `name`
```js
db.pokemons.createIndex({ name: 1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}

```

##3. Refazer a query para o campo `name` utilizando `explain` para ver o resultado da busca
```js
db.pokemons.find({name : /magneton/i}).explain('executionStats').executionStats.totalDocsExamined

1
```

##4. Fazer uma query para dois campos juntos utilizando `explain` para ver o resultado da busca
```js
db.pokemons.find({name : /magneton/i, attack: 60 }).explain('executionStats').executionStats.totalDocsExamined

610
```

##5. Criar um `index` para esses dois campos juntos
```js
db.pokemons.createIndex({ name: 1, attack: 1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}

```

##6. Refazer a query para os dois campos juntos utilizando `explain` para ver o resultado da busca
```js
db.pokemons.find({name : /magneton/i, attack: 60 }).explain('executionStats').executionStats.totalDocsExamined

1
```