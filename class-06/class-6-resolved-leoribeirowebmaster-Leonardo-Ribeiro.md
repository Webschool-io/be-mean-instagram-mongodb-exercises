# MongoDB - Aula 06 - Exercício
User: leoribeirowebmaster
Autor: Leonardo Ribeiro

# Fazer uma query para o campo name utilizando `explain` para ver o resultado da busca.
```
iMac-de-Leonardo(mongod-3.2.7) be-mean> db.pokemons.find({"name":"Charmander"}).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 1,
  "executionTimeMillis": 1,
  "totalKeysExamined": 0,
  "totalDocsExamined": 610,
  "executionStages": {
    "stage": "COLLSCAN",
    "filter": {
      "name": {
        "$eq": "Charmander"
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

# Criar um `index` um para o campo `name`.
```
iMac-de-Leonardo(mongod-3.2.7) be-mean> db.pokemons.createIndex({name: 1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}
```

# Refazer a query para o campo `name` utilizando `explain` para ver o resultado da busca.
```
iMac-de-Leonardo(mongod-3.2.7) be-mean> db.pokemons.find({"name":"Charmander"}).explain('executionStats').executionStats
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
          "[\"Charmander\", \"Charmander\"]"
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

# Fazer uma query para dois campos juntos utilizando `explain` para ver o resultado da busca.
```
iMac-de-Leonardo(mongod-3.2.7) be-mean> db.pokemons.find({attack: {$gt: 40}, type: "fire"}).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 0,
  "executionTimeMillis": 0,
  "totalKeysExamined": 0,
  "totalDocsExamined": 610,
  "executionStages": {
    "stage": "COLLSCAN",
    "filter": {
      "$and": [
        {
          "type": {
            "$eq": "fire"
          }
        },
        {
          "attack": {
            "$gt": 40
          }
        }
      ]
    },
    "nReturned": 0,
    "executionTimeMillisEstimate": 0,
    "works": 612,
    "advanced": 0,
    "needTime": 611,
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

# Criar um `index` para esses dois campos juntos.
```
iMac-de-Leonardo(mongod-3.2.7) be-mean> db.pokemons.createIndex({attack : 1, type: 1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 2,
  "numIndexesAfter": 3,
  "ok": 1
}
```

# Refazer a query para os dois campos juntos utilizando `explain` para ver o resultado da busca.
```
iMac-de-Leonardo(mongod-3.2.7) be-mean> db.pokemons.find({attack: {$gt: 40}, type: "fire"}).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 0,
  "executionTimeMillis": 0,
  "totalKeysExamined": 83,
  "totalDocsExamined": 0,
  "executionStages": {
    "stage": "FETCH",
    "nReturned": 0,
    "executionTimeMillisEstimate": 0,
    "works": 84,
    "advanced": 0,
    "needTime": 83,
    "needYield": 0,
    "saveState": 0,
    "restoreState": 0,
    "isEOF": 1,
    "invalidates": 0,
    "docsExamined": 0,
    "alreadyHasObj": 0,
    "inputStage": {
      "stage": "IXSCAN",
      "nReturned": 0,
      "executionTimeMillisEstimate": 0,
      "works": 84,
      "advanced": 0,
      "needTime": 83,
      "needYield": 0,
      "saveState": 0,
      "restoreState": 0,
      "isEOF": 1,
      "invalidates": 0,
      "keyPattern": {
        "attack": 1,
        "type": 1
      },
      "indexName": "attack_1_type_1",
      "isMultiKey": false,
      "isUnique": false,
      "isSparse": false,
      "isPartial": false,
      "indexVersion": 1,
      "direction": "forward",
      "indexBounds": {
        "attack": [
          "(40.0, inf.0]"
        ],
        "type": [
          "[\"fire\", \"fire\"]"
        ]
      },
      "keysExamined": 83,
      "dupsTested": 0,
      "dupsDropped": 0,
      "seenInvalidated": 0
    }
  }
}
```