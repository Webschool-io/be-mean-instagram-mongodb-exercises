# MongoDB - Aula 06 - Exercício
autor: **Sergio Diniz Correia**

# 1- Fazer uma query para o campo name utilizando explain para ver o resultado da busca
```javascript
 db.pokemons.find({nome : /Charmander/i}).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 0,
  "executionTimeMillis": 1,
  "totalKeysExamined": 0,
  "totalDocsExamined": 610,
  "executionStages": {
    "stage": "COLLSCAN",
    "filter": {
      "nome": /Charmander/i
    },
    "nReturned": 0,
    "executionTimeMillisEstimate": 0,
    "works": 612,
    "advanced": 0,
    "needTime": 611,
    "needFetch": 0,
    "saveState": 4,
    "restoreState": 4,
    "isEOF": 1,
    "invalidates": 0,
    "direction": "forward",
    "docsExamined": 610
  }
}
Sergios-MacBook-Pro(mongod-3.0.7) be-mean> 


```

# 2- Criar um index um para o campo name
```javascript
db.pokemons.createIndex({name : 1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}



```

# 3- Refazer a query para o campo name utilizando explain para ver o resultado da busca
```javascript
 db.pokemons.find({ name: /charmander/i }).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 1,
  "executionTimeMillis": 2,
  "totalKeysExamined": 610,
  "totalDocsExamined": 1,
  "executionStages": {
    "stage": "FETCH",
    "nReturned": 1,
    "executionTimeMillisEstimate": 0,
    "works": 611,
    "advanced": 1,
    "needTime": 609,
    "needFetch": 0,
    "saveState": 4,
    "restoreState": 4,
    "isEOF": 1,
    "invalidates": 0,
    "docsExamined": 1,
    "alreadyHasObj": 0,
    "inputStage": {
      "stage": "IXSCAN",
      "filter": {
        "name": /charmander/i
      },
      "nReturned": 1,
      "executionTimeMillisEstimate": 0,
      "works": 610,
      "advanced": 1,
      "needTime": 609,
      "needFetch": 0,
      "saveState": 4,
      "restoreState": 4,
      "isEOF": 1,
      "invalidates": 0,
      "keyPattern": {
        "name": 1
      },
      "indexName": "name_1",
      "isMultiKey": false,
      "direction": "forward",
      "indexBounds": {
        "name": [
          "[\"\", {})",
          "[/charmander/i, /charmander/i]"
        ]
      },
      "keysExamined": 610,
      "dupsTested": 0,
      "dupsDropped": 0,
      "seenInvalidated": 0,
      "matchTested": 1
    }
  }
}
Sergios-MacBook-Pro(mongod-3.0.7) be-mean> 




```

# 4- Fazer uma query para dois campos juntos utilizando explain para ver o resultado da busca
```javascript
db.pokemons.find({ $and:[ { hp :{$gt:50} }, { defense : {$gt: 40} } ]  }).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 411,
  "executionTimeMillis": 0,
  "totalKeysExamined": 0,
  "totalDocsExamined": 610,
  "executionStages": {
    "stage": "COLLSCAN",
    "filter": {
      "$and": [
        {
          "defense": {
            "$gt": 40
          }
        },
        {
          "hp": {
            "$gt": 50
          }
        }
      ]
    },
    "nReturned": 411,
    "executionTimeMillisEstimate": 0,
    "works": 612,
    "advanced": 411,
    "needTime": 200,
    "needFetch": 0,
    "saveState": 4,
    "restoreState": 4,
    "isEOF": 1,
    "invalidates": 0,
    "direction": "forward",
    "docsExamined": 610
  }
}
Sergios-MacBook-Pro(mongod-3.0.7) be-mean> 


```

# 5- Criar um index para esses dois campos juntos
```javascript
db.pokemons.createIndex({speed: 1, defense: 1 })
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 2,
  "numIndexesAfter": 3,
  "ok": 1
}
Sergios-MacBook-Pro(mongod-3.0.7) be-mean> 


```

# 6- Refazer a query para os dois campos juntos utilizando explain para ver o resultado da busca
```javascript
db.pokemons.find({ $and:[ { speed :{$gt:50} }, { defense : {$gt: 40} } ]  }).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 342,
  "executionTimeMillis": 1,
  "totalKeysExamined": 359,
  "totalDocsExamined": 342,
  "executionStages": {
    "stage": "FETCH",
    "nReturned": 342,
    "executionTimeMillisEstimate": 0,
    "works": 360,
    "advanced": 342,
    "needTime": 17,
    "needFetch": 0,
    "saveState": 2,
    "restoreState": 2,
    "isEOF": 1,
    "invalidates": 0,
    "docsExamined": 342,
    "alreadyHasObj": 0,
    "inputStage": {
      "stage": "IXSCAN",
      "nReturned": 342,
      "executionTimeMillisEstimate": 0,
      "works": 359,
      "advanced": 342,
      "needTime": 17,
      "needFetch": 0,
      "saveState": 2,
      "restoreState": 2,
      "isEOF": 1,
      "invalidates": 0,
      "keyPattern": {
        "speed": 1,
        "defense": 1
      },
      "indexName": "speed_1_defense_1",
      "isMultiKey": false,
      "direction": "forward",
      "indexBounds": {
        "speed": [
          "(50.0, inf.0]"
        ],
        "defense": [
          "(40.0, inf.0]"
        ]
      },
      "keysExamined": 359,
      "dupsTested": 0,
      "dupsDropped": 0,
      "seenInvalidated": 0,
      "matchTested": 0
    }
  }
}
Sergios-MacBook-Pro(mongod-3.0.7) be-mean> 


```
