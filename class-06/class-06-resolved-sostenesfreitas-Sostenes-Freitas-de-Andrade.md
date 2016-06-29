##MongoDb - Aula 06 -Exercício

Autor: sostenesfreitas

##1 - Fazer uma query para o campo name utilizando explain para ver o resultado da busca:

``` 
corsair(mongod-3.2.7) be-mean> var query = {"name":"Articuno"}
corsair(mongod-3.2.7) be-mean> db.pokemons.find(query).explain('executionStats').executionStats

{
  "executionSuccess": true,
  "nReturned": 1,
  "executionTimeMillis": 0,
  "totalKeysExamined": 0,
  "totalDocsExamined": 610,
  "executionStages": {
    "stage": "COLLSCAN",
	"filter": {
		"name": {
        "$eq": "Articuno"
      
		}
    
	},
    "nReturned": 1,
    "executionTimeMillisEstimate": 0,
    "works": 612,
    "advanced": 1,
    "needTime": 610,
    "needYield": 0,
    "saveState": 4,
    "restoreState": 4,
    "isEOF": 1,
    "invalidates": 0,
    "direction": "forward",
    "docsExamined": 610
  
  }

}
```
##2 - Criar um index um para o campo name

```
corsair(mongod-3.2.7) be-mean> var index = {name: 1}
corsair(mongod-3.2.7) be-mean> db.pokemons.createIndex(index)
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}

```
##3 - Refazer a query para o campo name utilizando explain para ver o resultado da busca

```
corsair(mongod-3.2.7) be-mean> var query = {"name":"Articuno"}
corsair(mongod-3.2.7) be-mean> db.pokemons.find(query).explain('executionStats').executionStats


{
  "executionSuccess": true,
  "nReturned": 1,
  "executionTimeMillis": 13,
  "totalKeysExamined": 1,
  "totalDocsExamined": 1,
  "executionStages": {
    "stage": "FETCH",
    "nReturned": 1,
    "executionTimeMillisEstimate": 0,
    "works": 2,
    "advanced": 1,
    "needTime": 0,
    "needYield": 0,
    "saveState": 0,
    "restoreState": 0,
    "isEOF": 1,
    "invalidates": 0,
    "docsExamined": 1,
    "alreadyHasObj": 0,
	"inputStage": {
      "stage": "IXSCAN",
      "nReturned": 1,
      "executionTimeMillisEstimate": 0,
      "works": 2,
      "advanced": 1,
      "needTime": 0,
      "needYield": 0,
      "saveState": 0,
      "restoreState": 0,
      "isEOF": 1,
      "invalidates": 0,
	  "keyPattern": {
        "name": 1
      
	  },
      "indexName": "name_1",
      "isMultiKey": false,
      "isUnique": false,
      "isSparse": false,
      "isPartial": false,
      "indexVersion": 1,
      "direction": "forward",
	  "indexBounds": {
		  "name": [
          "[\"Articuno\", \"Articuno\"]"
        
		  ]
      
	  },
      "keysExamined": 1,
      "dupsTested": 0,
      "dupsDropped": 0,
      "seenInvalidated": 0
    
	}
  
  }

}


```

## 4 - Fazer uma query para dois campos juntos utilizando explain para ver o resultado da busca

```
corsair(mongod-3.2.7) be-mean> var query = {"name":"Articuno","hp":90}
corsair(mongod-3.2.7) be-mean> db.pokemons.find(query).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 1,
  "executionTimeMillis": 0,
  "totalKeysExamined": 0,
  "totalDocsExamined": 610,
  "executionStages": {
    "stage": "COLLSCAN",
	"filter": {
		"$and": [
		{
			"hp": {
            "$eq": 90
          
			}
        
		},
		{
			"name": {
            "$eq": "Articuno"
          
			}
        
		}
      
		]
    
	},
    "nReturned": 1,
    "executionTimeMillisEstimate": 0,
    "works": 612,
    "advanced": 1,
    "needTime": 610,
    "needYield": 0,
    "saveState": 4,
    "restoreState": 4,
    "isEOF": 1,
    "invalidates": 0,
    "direction": "forward",
    "docsExamined": 610
  
  }

}

```

## 5 - Criar um index para esses dois campos juntos

```
corsair(mongod-3.2.7) be-mean> var index = {name: 1, hp: 1}
corsair(mongod-3.2.7) be-mean> db.pokemons.createIndex(index)
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 2,
  "numIndexesAfter": 3,
  "ok": 1
}

```
## 6 - Refazer a query para os dois campos juntos utilizando explain para ver o resultado da busca

```
corsair(mongod-3.2.7) be-mean> var query = {"name":"Articuno","hp":90}
corsair(mongod-3.2.7) be-mean> db.pokemons.find(query).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 1,
  "executionTimeMillis": 0,
  "totalKeysExamined": 1,
  "totalDocsExamined": 1,
  "executionStages": {
    "stage": "FETCH",
    "nReturned": 1,
    "executionTimeMillisEstimate": 0,
    "works": 2,
    "advanced": 1,
    "needTime": 0,
    "needYield": 0,
    "saveState": 0,
    "restoreState": 0,
    "isEOF": 1,
    "invalidates": 0,
    "docsExamined": 1,
    "alreadyHasObj": 0,
	"inputStage": {
      "stage": "IXSCAN",
      "nReturned": 1,
      "executionTimeMillisEstimate": 0,
      "works": 2,
      "advanced": 1,
      "needTime": 0,
      "needYield": 0,
      "saveState": 0,
      "restoreState": 0,
      "isEOF": 1,
      "invalidates": 0,
	  "keyPattern": {
        "name": 1,
        "hp": 1
      
	  },
      "indexName": "name_1_hp_1",
      "isMultiKey": false,
      "isUnique": false,
      "isSparse": false,
      "isPartial": false,
      "indexVersion": 1,
      "direction": "forward",
	  "indexBounds": {
		  "name": [
          "[\"Articuno\", \"Articuno\"]"
        
		  ],
		  "hp": [
          "[90.0, 90.0]"
        
		  ]
      
	  },
      "keysExamined": 1,
      "dupsTested": 0,
      "dupsDropped": 0,
      "seenInvalidated": 0
    
	}
  
  }

}

```






 
