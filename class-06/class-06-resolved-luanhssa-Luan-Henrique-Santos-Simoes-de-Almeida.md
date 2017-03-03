# MongoDB - Aula 06 - Exercício
User: [luanhssa](http://www.github.com/luanhssa)
Autor: Luan Henrique Santos Simões de Almeida

## Fazer uma query para o campo name utilizando `explain` para ver o resultado da busca
```
inspiron(mongod-3.2.6) bemean> db.restaurantes.find({"name": "Wendy'S"}).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 41,
  "executionTimeMillis": 25,
  "totalKeysExamined": 0,
  "totalDocsExamined": 25359,
  "executionStages": {
    "stage": "COLLSCAN",
    "filter": {
      "name": {
        "$eq": "Wendy'S"
      }
    },
    "nReturned": 41,
    "executionTimeMillisEstimate": 30,
    "works": 25361,
    "advanced": 41,
    "needTime": 25319,
    "needYield": 0,
    "saveState": 198,
    "restoreState": 198,
    "isEOF": 1,
    "invalidates": 0,
    "direction": "forward",
    "docsExamined": 25359
  }
}
```

## Criar um `index` para o campo `name`
```
inspiron(mongod-3.2.6) bemean> db.restaurantes.createIndex({name:1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}
```

## Refazer a query para o campo `name` utilizando `explain` para ver o resultado da busca
```
inspiron(mongod-3.2.6) bemean> db.restaurantes.find({"name": "Wendy'S"}).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 41,
  "executionTimeMillis": 12,
  "totalKeysExamined": 41,
  "totalDocsExamined": 41,
  "executionStages": {
    "stage": "FETCH",
    "nReturned": 41,
    "executionTimeMillisEstimate": 10,
    "works": 42,
    "advanced": 41,
    "needTime": 0,
    "needYield": 0,
    "saveState": 0,
    "restoreState": 0,
    "isEOF": 1,
    "invalidates": 0,
    "docsExamined": 41,
    "alreadyHasObj": 0,
    "inputStage": {
      "stage": "IXSCAN",
      "nReturned": 41,
      "executionTimeMillisEstimate": 10,
      "works": 42,
      "advanced": 41,
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
          "[\"Wendy'S\", \"Wendy'S\"]"
        ]
      },
      "keysExamined": 41,
      "dupsTested": 0,
      "dupsDropped": 0,
      "seenInvalidated": 0
    }
  }
}
```

## Fazer uma query para dois campos juntos utilizando `explain` para ver o resultado da busca
```
inspiron(mongod-3.2.6) bemean> db.restaurantes.find({"restaurant_id": "30112340", "borough": "Brooklyn"}).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 1,
  "executionTimeMillis": 41,
  "totalKeysExamined": 0,
  "totalDocsExamined": 25359,
  "executionStages": {
    "stage": "COLLSCAN",
    "filter": {
      "$and": [
        {
          "borough": {
            "$eq": "Brooklyn"
          }
        },
        {
          "restaurant_id": {
            "$eq": "30112340"
          }
        }
      ]
    },
    "nReturned": 1,
    "executionTimeMillisEstimate": 30,
    "works": 25361,
    "advanced": 1,
    "needTime": 25359,
    "needYield": 0,
    "saveState": 198,
    "restoreState": 198,
    "isEOF": 1,
    "invalidates": 0,
    "direction": "forward",
    "docsExamined": 25359
  }
}
```

## Criar um `index` para esses dois campos juntos
```
inspiron(mongod-3.2.6) bemean> db.restaurantes.createIndex({restaurant_id:1, borough:1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 2,
  "numIndexesAfter": 3,
  "ok": 1
}
```

## Refazer a query para os dois campos juntos utilizando `explain` para ver o resultado da busca
```
inspiron(mongod-3.2.6) bemean> db.restaurantes.find({"restaurant_id": "30112340", "borough": "Brooklyn"}).explain('executionStats').executionStats
{
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
        "restaurant_id": 1,
        "borough": 1
      },
      "indexName": "restaurant_id_1_borough_1",
      "isMultiKey": false,
      "isUnique": false,
      "isSparse": false,
      "isPartial": false,
      "indexVersion": 1,
      "direction": "forward",
      "indexBounds": {
        "restaurant_id": [
          "[\"30112340\", \"30112340\"]"
        ],
        "borough": [
          "[\"Brooklyn\", \"Brooklyn\"]"
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
