# MongoDB - Aula 06 - Exercício
autor: Samuel Desconsi - Underzzoo

## 1. Fazer uma query para o campo `name` utilizando `explain` para ver o resultado da busca

```
db.pokemons.find({ name: /pikachu/i }).explain('executionStats').executionStats.totalDocsExamined
610

db.pokemons.find({ name: /pikachu/i }).explain('executionStats').executionStats.executionTimeMillis
1

```
## 2. Criar um `index` um para o campo `name`

```
db.pokemons.createIndex({ name: 1 })
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}

> db.pokemons.createIndex({ name: 1 })
{ "numIndexesBefore" : 2, "note" : "all indexes already exist", "ok" : 1 }
>

```

## 3. Refazer a query para o campo `name` utilizando `explain` para ver o resultado da busca

```
db.pokemons.find({ name: /Pika/i }).explain('executionStats').executionStats.totalDocsExamined
1

db.pokemons.find({ name: /Pika/i }).explain('executionStats').executionStats.executionTimeMillis
0
```

## 4. Fazer uma query para dois campos juntos utilizando `explain` para ver o resultado da busca

```
db.pokemons.find({$and:[{attack: {$gt: 50}}, {defense: {$gt: 30}}]}).explain('executionStats').executionStats.totalDocsExamined
610

db.pokemons.find({$and:[{attack: {$gt: 50}}, {defense: {$gt: 30}}]}).explain('executionStats').executionStats.executionTimeMillis
1

```

## 5. Criar um `index` para esses dois campos juntos

```
> db.pokemons.createIndex({ attack: 1, defense: 1 })
{
	"createdCollectionAutomatically" : false,
	"numIndexesBefore" : 2,
	"numIndexesAfter" : 3,
	"ok" : 1
}

```

## 6. Refazer a query para os dois campos juntos utilizando `explain` para ver o resultado da busca

```
db.pokemons.find({$and:[{attack: {$gt: 50}}, {defense: {$gt: 30}}]}).explain('executionStats').executionStats.totalDocsExamined
454

db.pokemons.find({$and:[{attack: {$gt: 50}}, {defense: {$gt: 30}}]}).explain('executionStats').executionStats.executionTimeMillis
0

```
