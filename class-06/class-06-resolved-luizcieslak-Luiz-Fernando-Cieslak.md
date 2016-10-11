# MongoDB - Aula 06 - Exercício
autor: Luiz Fernando Cieslak

## 1. Fazer uma query para o campo name utilizando explain para ver o resultado da busca
```
db.pokemons.find({name: /starmie/i}).explain('executionStats').executionStats.totalDocsExamined
610
db.pokemons.find({name: /starmie/i}).explain('executionStats').executionStats.executionTimeMillis
1
```
## 2. Criar um index um para o campo name
```
db.pokemons.createIndex({name:1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}
```
## 3. Refazer a query para o campo name utilizando explain para ver o resultado da busca
```
db.pokemons.find({name: /starmie/i}).explain('executionStats').executionStats.totalDocsExamined
1
db.pokemons.find({name: /starmie/i}).explain('executionStats').executionStats.executionTimeMillis
0
```
## 4. Fazer uma query para dois campos juntos utilizando explain para ver o resultado da busca
```
db.pokemons.find({ $and:[ { types: 'psychic'},{ attack:{$gt: 100}}]})
...
Fetched 6 record(s) in 1ms

db.pokemons.find({ $and:[ { types: 'psychic'},{ attack:{$gt: 100}}]}).explain('executionStats').executionStats.totalDocsExamined
610
db.pokemons.find({ $and:[ { types: 'psychic'},{ attack:{$gt: 100}}]}).explain('executionStats').executionStats.executionTimeMillis
1
```
## 5. Criar um index para esses dois campos juntos
```
db.pokemons.createIndex({types:1, attack: 1})
```
## 6. Refazer a query para os dois campos juntos utilizando explain para ver o resultado da busca
```
db.pokemons.find({ $and:[ { types: 'psychic'},{ attack:{$gt: 100}}]}).explain('executionStats').executionStats.totalDocsExamined
6
db.pokemons.find({ $and:[ { types: 'psychic'},{ attack:{$gt: 100}}]}).explain('executionStats').executionStats.executionTimeMillis
0
```
