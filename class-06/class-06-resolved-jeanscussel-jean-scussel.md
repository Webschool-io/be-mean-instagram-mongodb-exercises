# MongoDB - Aula 06 - Exercício
autor: Jean Scussel

**OBS:** Os resultados de busca mostram o tempo sempre abaixo de **0 milissegundos** pois a base de pokemons é pequena demais. Porém observa-se a diferença na quantidade de arquivos buscados quando usado o `totalDocsExamined.`

## 1. Na coleção de pokemons, criar um índice para o campo `name`, e outro para outros dois campos

### name
```
	be-mean> db.pokemons.createIndex({name: 1})
	{
 	 "createdCollectionAutomatically": false,
  	"numIndexesBefore": 1,
  	"numIndexesAfter": 2,
  	"ok": 1
	}
```
### attack e defense
```
	be-mean> db.pokemons.createIndex({attack: 1, defense: 1})
	{
  	"createdCollectionAutomatically": false,
  	"numIndexesBefore": 2,
  	"numIndexesAfter": 3,
  	"ok": 1
	}
```
### Índices criados
```
	be-mean> db.pokemons.getIndexes()
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
	      "attack": 1,
	      "defense": 1
	    },
	    "name": "attack_1_defense_1",
	    "ns": "be-mean.pokemons"
	  }
	]
```

## 2. Fazer uma query com índice e outra sem para `name`, e para os outros dois campos definidos

### name sem índice
```
	be-mean> db.pokemons.find({
    	name: "Charmander"}).explain('executionStats').executionStats.executionTimeMillis
	0
	be-mean> db.pokemons.find({
    	name: "Charmander"}).explain('executionStats').executionStats.totalDocsExamined
	610
```
#### name com índice
```
	be-mean> db.pokemons.find({
    	name: "Charmander"}).explain('executionStats').executionStats.totalDocsExamined
	1
	be-mean> db.pokemons.find({
    	name: "Charmander"}).explain('executionStats').executionStats.executionTimeMillis
	0
```

### attack e defense sem índice
```
	be-mean> db.pokemons.find({
    	attack: 52, defense: 43}).explain('executionStats').executionStats.totalDocsExamined
	610
	be-mean> db.pokemons.find({
    	attack: 52, defense: 43}).explain('executionStats').executionStats.executionTimeMillis
	0
```

### attack e defense com índice
```
	be-mean> db.pokemons.find({
    	attack: 52, defense: 43}).explain('executionStats').executionStats.totalDocsExamined
	2
	be-mean> db.pokemons.find({
    	attack: 52, defense: 43}).explain('executionStats').executionStats.executionTimeMillis
	0
```
