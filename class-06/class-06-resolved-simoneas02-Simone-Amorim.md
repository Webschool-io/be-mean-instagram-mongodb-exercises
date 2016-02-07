# MongoDB - Aula 06 - Exercício
Autor: Simone Amorim

##1. Fazer uma query para o campo `name` utilizando `explain` para ver o resultado da busca.
```javascript
db.pokemons.find({"name" : "Charmander"}).explain('executionStats').executionStats.totalDocsExamined
610
db.pokemons.find({"name" : "Charmander"}).explain('executionStats').executionStats.executionTimeMillis
0

```
<br/>
##2. Criar um `index` um para o campo `name`.
```javascript
db.pokemons.createIndex({name: 1})
{
        "createdCollectionAutomatically" : false,
        "numIndexesBefore" : 1,
        "numIndexesAfter" : 2,
        "ok" : 1
}
```
<br/>
##3. Refazer a query para o campo `name` utilizando `explain` para ver o resultado da busca.
```javascript
db.pokemons.find({"name" : "Charmander"}).explain('executionStats').executionStats.totalDocsExamined
1
db.pokemons.find({"name" : "Charmander"}).explain('executionStats').executionStats.executionTimeMillis
0
```
<br/>
##4. Fazer uma query para dois campos juntos utilizando `explain` para ver o resultado da busca.
```javascript
db.pokemons.find({"name" : "Charmander", attack: {$gte: 50}}).explain('executionStats').executionStats.totalDocsExamined
610
db.pokemons.find({"name" : "Charmander", attack: {$gte: 50}}).explain('executionStats').executionStats.executionTimeMillis
0
```
<br/>
##5. Criar um `index` para esses dois campos juntos.
```javascript
db.pokemons.createIndex({name: 1, attack: 1})
{
        "createdCollectionAutomatically" : false,
        "numIndexesBefore" : 2,
        "numIndexesAfter" : 3,
        "ok" : 1
}
```
<br/>
##6. Refazer a query para os dois campos juntos utilizando `explain` para ver o resultado da busca.
```javascript
 db.pokemons.find({"name" : "Charmander", attack: {$gte: 50}}).explain('executionStats').executionStats.totalDocsExamined
1
db.pokemons.find({"name" : "Charmander", attack: {$gte: 50}}).explain('executionStats').executionStats.executionTimeMillis
0
```