# MongoDB - Aula 06 - Exercício
User: [netoabel](http://www.github.com/netoabel)

Autor: Abel Neto

## Fazer uma query para o campo name utilizando `explain` para ver o resultado da busca

```
be-mean> db.restaurantes.find({ "name": "Morris Park Bake Shop" }).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 1,
  "executionTimeMillis": 111,
  "totalKeysExamined": 0,
  "totalDocsExamined": 25359,
  "executionStages": {
    "stage": "COLLSCAN",
    "filter": {
      "name": {
        "$eq": "Morris Park Bake Shop"
      }
    },
    "nReturned": 1,
    "executionTimeMillisEstimate": 70,
    "works": 25390,
    "advanced": 1,
    "needTime": 25359,
    "needYield": 29,
    "saveState": 214,
    "restoreState": 214,
    "isEOF": 1,
    "invalidates": 0,
    "direction": "forward",
    "docsExamined": 25359
  }
}
```
 
## Criar um `index` um para o campo `name`

``` 
be-mean> db.restaurantes.createIndex( { name: 1 } )
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}
``` 

## Refazer a query para o campo `name` utilizando `explain` para ver o resultado da busca

```
be-mean> db.restaurantes.find({ "name": "Morris Park Bake Shop" }).explain('executionStats').executionStats
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
          "[\"Morris Park Bake Shop\", \"Morris Park Bake Shop\"]"
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

## Fazer uma query para dois campos juntos utilizando `explain` para ver o resultado da busca

```
be-mean> db.restaurantes.find({ borough: "Bronx", cuisine: "Bakery" }).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 71,
  "executionTimeMillis": 61,
  "totalKeysExamined": 0,
  "totalDocsExamined": 25359,
  "executionStages": {
    "stage": "COLLSCAN",
    "filter": {
      "$and": [
        {
          "borough": {
            "$eq": "Bronx"
          }
        },
        {
          "cuisine": {
            "$eq": "Bakery"
          }
        }
      ]
    },
    "nReturned": 71,
    "executionTimeMillisEstimate": 20,
    "works": 25361,
    "advanced": 71,
    "needTime": 25289,
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
be-mean> db.restaurantes.createIndex({ borough: 1, cuisine: 1 })
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 2,
  "numIndexesAfter": 3,
  "ok": 1
}
```

## Refazer a query para os dois campos juntos utilizando `explain` para ver o resultado da busca

```
be-mean> db.restaurantes.find({ borough: "Bronx", cuisine: "Bakery" }).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 71,
  "executionTimeMillis": 0,
  "totalKeysExamined": 71,
  "totalDocsExamined": 71,
  "executionStages": {
    "stage": "FETCH",
    "nReturned": 71,
    "executionTimeMillisEstimate": 0,
    "works": 72,
    "advanced": 71,
    "needTime": 0,
    "needYield": 0,
    "saveState": 0,
    "restoreState": 0,
    "isEOF": 1,
    "invalidates": 0,
    "docsExamined": 71,
    "alreadyHasObj": 0,
    "inputStage": {
      "stage": "IXSCAN",
      "nReturned": 71,
      "executionTimeMillisEstimate": 0,
      "works": 72,
      "advanced": 71,
      "needTime": 0,
      "needYield": 0,
      "saveState": 0,
      "restoreState": 0,
      "isEOF": 1,
      "invalidates": 0,
      "keyPattern": {
        "borough": 1,
        "cuisine": 1
      },
      "indexName": "borough_1_cuisine_1",
      "isMultiKey": false,
      "isUnique": false,
      "isSparse": false,
      "isPartial": false,
      "indexVersion": 1,
      "direction": "forward",
      "indexBounds": {
        "borough": [
          "[\"Bronx\", \"Bronx\"]"
        ],
        "cuisine": [
          "[\"Bakery\", \"Bakery\"]"
        ]
      },
      "keysExamined": 71,
      "dupsTested": 0,
      "dupsDropped": 0,
      "seenInvalidated": 0
    }
  }
}
```