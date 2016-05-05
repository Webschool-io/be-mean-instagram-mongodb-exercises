#MongoDB - Aula 06 - Exercícios
autor: Higor Diego

##1. Fazer uma query para o campo `name` utilizando `explain` para ver o resultado da busca
```js

nodejs(mongod-3.2.0) test> use be-mean-pokemons
switched to db be-mean-pokemons

nodejs(mongod-3.2.0) be-mean-pokemons> db.pokemons.find({"name": "Dodrio"}).explain('executionStats').executionStats.totalDocsExamined
610

```

##2. Criar um `index` um para o campo `name`
```js
nodejs(mongod-3.2.0) be-mean-pokemons> db.pokemons.createIndex({name: 1});
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}

```

##3. Refazer a query para o campo `name` utilizando `explain` para ver o resultado da busca
```js
nodejs(mongod-3.2.0) be-mean-pokemons> db.pokemons.find({"name": "Dodrio"}).explain('executionStats').executionStats.totalDocsExamined;
1

```

##4. Fazer uma query para dois campos juntos utilizando `explain` para ver o resultado da busca
```js
nodejs(mongod-3.2.0) be-mean-pokemons> db.pokemons.find({$and: [{ attack: {$gt: 20}}, { defense: { $gt:30} } ] } ).explain('executionStats').executionStats.totalDocsExamined;
610

```

##5. Criar um `index` para esses dois campos juntos
```js
nodejs(mongod-3.2.0) be-mean-pokemons> db.pokemons.createIndex({attack: 1, defense: 1});
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 2,
  "numIndexesAfter": 3,
  "ok": 1
}

```

##6. Refazer a query para os dois campos juntos utilizando `explain` para ver o resultado da busca
```js
nodejs(mongod-3.2.0) be-mean-pokemons> db.pokemons.find({$and: [{ attack: {$gt: 20}}, { defense: { $gt:30} } ] } ).explain('executionStats').executionStats.totalDocsExamined;
576
```
