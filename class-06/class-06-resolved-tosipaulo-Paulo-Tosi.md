# MongoDB - Aula 06 - Exercício
autor: Paulo Tosi

## 1. Fazer uma query para o campo `name` utilizando explain para ver o resultado da busca ##

```javascript

db.pokemons.find({"name": /Charmander/i}).explain('executionStats').executionStats.totalDocsExamined
610

be-mean> db.pokemons.find({"name": /Charmander/i}).explain('executionStats').executionStats.executionTimeMillis
1

```


## Criar um index um para o campo `name` ##

```javascript

db.pokemons.createIndex({name:1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}


```


## Refazer a query para o campo `name` utilizando explain para ver o resultado da busca ##

```javascript

db.pokemons.find({"name": /Charmander/i}).explain('executionStats').executionStats.totalDocsExamined
1

be-mean> db.pokemons.find({"name": /Charmander/i}).explain('executionStats').executionStats.executionTimeMillis
2


```

## Fazer uma query para dois campos juntos utilizando `explain` para ver o resultado da busca ##

```javascript

db.pokemons.find({ $and:[ { attack: { $gt: 50 } }, { hp: { $gt: '10' } } ] }).explain('executionStats').executionStats.totalDocsExamined
610

db.pokemons.find({ $and:[ { attack: { $gt: 50 } }, { height: { $gt: '10' } } ] }).explain('executionStats').executionStats.executionTimeMillis
1

```

## Criar um `index` para esses dois campos juntos ##

```javascript

db.pokemons.createIndex({attack:1, height:1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 2,
  "numIndexesAfter": 3,
  "ok": 1
}


```

## Refazer a query para os dois campos juntos utilizando explain para ver o resultado da busca ##

```javascript

db.pokemons.find({ $and:[ { attack: { $gt: 50 } }, { hp: { $gt: '10' } } ] }).explain('executionStats').executionStats.totalDocsExamined
462

db.pokemons.find({ $and:[ { attack: { $gt: 50 } }, { height: { $gt: '10' } } ] }).explain('executionStats').executionStats.executionTimeMillis
1

```


