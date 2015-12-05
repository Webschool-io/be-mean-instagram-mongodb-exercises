# MongoDB - Aula 06 - Exercício
autor: Michel Mattos

# 1. Fazer uma query para o campo name utilizando explain para ver o resultado da busca

```javascript
> db.restaurantes.find({ name: "Morris Park Bake Shop" }).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 1,
  "executionTimeMillis": 75,
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
    "executionTimeMillisEstimate": 60,
    "works": 26545,
    "advanced": 1,
    "needTime": 25359,
    "needFetch": 1184,
    "saveState": 1199,
    "restoreState": 1199,
    "isEOF": 1,
    "invalidates": 0,
    "direction": "forward",
    "docsExamined": 25359
  }
}
```

# 2. Criar um index um para o campo name

```javascript
> db.restaurantes.createIndex({ name: 1 })
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}
```

# 3. Refazer a query para o campo name utilizando explain para ver o resultado da busca

```javascript
> db.restaurantes.find({ name: "Morris Park Bake Shop" }).explain('executionStats').executionStats
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
    "needFetch": 0,
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
      "needFetch": 0,
      "saveState": 0,
      "restoreState": 0,
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
          "[\"Morris Park Bake Shop\", \"Morris Park Bake Shop\"]"
        ]
      },
      "keysExamined": 1,
      "dupsTested": 0,
      "dupsDropped": 0,
      "seenInvalidated": 0,
      "matchTested": 0
    }
  }
}
```

# 4. Fazer uma query para dois campos juntos utilizando explain para ver o resultado da busca

```javascript
> db.restaurantes.find({ borough: "Bronx", cuisine: "Bakery" }).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 71,
  "executionTimeMillis": 11,
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
    "executionTimeMillisEstimate": 10,
    "works": 25361,
    "advanced": 71,
    "needTime": 25289,
    "needFetch": 0,
    "saveState": 198,
    "restoreState": 198,
    "isEOF": 1,
    "invalidates": 0,
    "direction": "forward",
    "docsExamined": 25359
  }
}
```

# 5. Criar um index para esses dois campos juntos

```javascript
> db.restaurantes.createIndex({ borough: 1, cuisine: 1 })
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 2,
  "numIndexesAfter": 3,
  "ok": 1
}
```

# 6. Refazer a query para os dois campos juntos utilizando explain para ver o resultado da busca

```javascript
> db.restaurantes.find({ borough: "Bronx", cuisine: "Bakery" }).explain('executionStats').executionStats
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
    "needFetch": 0,
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
      "needFetch": 0,
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
      "seenInvalidated": 0,
      "matchTested": 0
    }
  }
}
```