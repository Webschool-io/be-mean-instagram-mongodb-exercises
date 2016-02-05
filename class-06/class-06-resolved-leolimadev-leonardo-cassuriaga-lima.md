#MongoDB - Aula 06 - Exercícios
autor: Leonardo Cassuriga Lima

##1. Fazer uma query para o campo `name` utilizando `explain` para ver o resultado da busca

> db.pokemons.find({name : /Bulbassauro/i}).explain('executionStats').executionStats.totalDocsExamined  
11

##2. Criar um `index` um para o campo `name`

db.pokemons.createIndex({ name: 1})  
{  
  "createdCollectionAutomatically": false,  
  "numIndexesBefore": 1,  
  "numIndexesAfter": 2,  
  "ok": 1  
}  

##3. Refazer a query para o campo `name` utilizando `explain` para ver o resultado da busca

db.pokemons.find({name : /Bulbassauro/i}).explain('executionStats').executionStats.totalDocsExamined  
1

##4. Fazer uma query para dois campos juntos utilizando `explain` para ver o resultado da busca

db.pokemons.find({name : /Bulbassauro/i, type: 'grama' }).explain('executionStats').executionStats.totalDocsExamined

1

##5. Criar um `index` para esses dois campos juntos

db.pokemons.createIndex({ name: 1, type: 1})  
{  
  "createdCollectionAutomatically": false,  
  "numIndexesBefore": 2,  
  "numIndexesAfter": 3,  
  "ok": 1  
}  

##6. Refazer a query para os dois campos juntos utilizando `explain` para ver o resultado da busca

db.pokemons.find({name : /Bulbassauro/i, type: 'grama' }).explain('executionStats').executionStats.totalDocsExamined  
1
