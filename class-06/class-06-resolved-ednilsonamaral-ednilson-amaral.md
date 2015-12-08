# MongoDB - Aula 06 - Exercício  
Autor: Ednilson Amaral


## Criar 2 indíces


### Indice para campo `name`

```  
be-mean> db.pokemons.createIndex({name: 1})  
{  
  "createdCollectionAutomatically": false,  
  "numIndexesBefore": 1,  
  "numIndexesAfter": 2,  
  "ok": 1  
}  

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
  }  
]  
```


Agora, utilizando o `explain()` após a criação desse indice:  

```  
be-mean> db.pokemons.find({"name": "Pikachu"}).explain('executionStats')  
{  
  "queryPlanner": {  
    "plannerVersion": 1,  
    "namespace": "be-mean.pokemons",  
    "indexFilterSet": false,  
    "parsedQuery": {  
      "name": {  
        "$eq": "Pikachu"  
      }  
    },  
    "winningPlan": {  
      "stage": "FETCH",  
      "inputStage": {  
        "stage": "IXSCAN",  
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
            "[\"Pikachu\", \"Pikachu\"]"  
          ]  
        }  
      }  
    },  
    "rejectedPlans": [ ]  
  },  
  "executionStats": {  
    "executionSuccess": true,  
    "nReturned": 1,  
    "executionTimeMillis": 1,  
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
            "[\"Pikachu\", \"Pikachu\"]"  
          ]  
        },  
        "keysExamined": 1,  
        "dupsTested": 0,  
        "dupsDropped": 0,  
        "seenInvalidated": 0  
      }  
    }  
  },  
  "serverInfo": {  
    "host": "EDNILSON-NB",  
    "port": 27017,  
    "version": "3.2.0-rc2-211-gbd58ea2",  
    "gitVersion": "bd58ea2ba5d17b960981990bb97cab133d7e90ed"  
  },  
  "ok": 1  
}  
```


### Indice para outros dois campos juntos  

```  
be-mean> db.pokemons.createIndex({attack: 1, defense: 1})  
{  
  "createdCollectionAutomatically": false,  
  "numIndexesBefore": 2,  
  "numIndexesAfter": 3,  
  "ok": 1  
}  

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


Agora, utilizando o `explain()` após a criação desse indice:  

```  
be-mean> db.pokemons.find({"attack": {$lte: 100}, "defense": {$gte: 30}}).explain('executionStats')  
{  
  "queryPlanner": {  
    "plannerVersion": 1,  
    "namespace": "be-mean.pokemons",  
    "indexFilterSet": false,  
    "parsedQuery": {  
      "$and": [  
        {  
          "attack": {  
            "$lte": 100  
          }  
        },  
        {  
          "defense": {  
            "$gte": 30  
          }  
        }  
      ]  
    },  
    "winningPlan": {  
      "stage": "FETCH",  
      "inputStage": {  
        "stage": "IXSCAN",  
        "keyPattern": {  
          "attack": 1,  
          "defense": 1  
        },  
        "indexName": "attack_1_defense_1",  
        "isMultiKey": false,  
        "isUnique": false,  
        "isSparse": false,  
        "isPartial": false,  
        "indexVersion": 1,  
        "direction": "forward",  
        "indexBounds": {  
          "attack": [  
            "[-inf.0, 100.0]"  
          ],  
          "defense": [  
            "[30.0, inf.0]"  
          ]  
        }  
      }  
    },  
    "rejectedPlans": [ ]  
  },  
  "executionStats": {  
    "executionSuccess": true,  
    "nReturned": 497,  
    "executionTimeMillis": 4,  
    "totalKeysExamined": 509,  
    "totalDocsExamined": 497,  
    "executionStages": {  
      "stage": "FETCH",  
      "nReturned": 497,  
      "executionTimeMillisEstimate": 0,  
      "works": 509,  
      "advanced": 497,  
      "needTime": 11,  
      "needYield": 0,  
      "saveState": 3,  
      "restoreState": 3,  
      "isEOF": 1,  
      "invalidates": 0,  
      "docsExamined": 497,  
      "alreadyHasObj": 0,  
      "inputStage": {  
        "stage": "IXSCAN",  
        "nReturned": 497,  
        "executionTimeMillisEstimate": 0,  
        "works": 509,  
        "advanced": 497,  
        "needTime": 11,  
        "needYield": 0,  
        "saveState": 3,  
        "restoreState": 3,  
        "isEOF": 1,  
        "invalidates": 0,  
        "keyPattern": {  
          "attack": 1,  
          "defense": 1  
        },  
        "indexName": "attack_1_defense_1",  
        "isMultiKey": false,  
        "isUnique": false,  
        "isSparse": false,  
        "isPartial": false,  
        "indexVersion": 1,  
        "direction": "forward",  
        "indexBounds": {  
          "attack": [  
            "[-inf.0, 100.0]"  
          ],  
          "defense": [  
            "[30.0, inf.0]"  
          ]  
        },  
        "keysExamined": 509,  
        "dupsTested": 0,  
        "dupsDropped": 0,  
        "seenInvalidated": 0  
      }  
    }  
  },  
  "serverInfo": {  
    "host": "EDNILSON-NB",  
    "port": 27017,  
    "version": "3.2.0-rc2-211-gbd58ea2",  
    "gitVersion": "bd58ea2ba5d17b960981990bb97cab133d7e90ed"  
  },  
  "ok": 1  
}  
```