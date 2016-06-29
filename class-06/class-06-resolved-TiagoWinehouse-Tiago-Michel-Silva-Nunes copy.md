# MongoDB - Aula 06 - Exercício
autor: Tiago Michel Silva Nunes

## 1.  Indice para campo  `name`

```javascript
SkyWine(mongod-3.0.7) be-mean-pokemons> db.pokemons.find({ name: 'Charmeleon' }).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 1,
  "executionTimeMillis": 0,
  "totalKeysExamined": 0,
  "totalDocsExamined": 611,
  "executionStages": {
    "stage": "COLLSCAN",
    "filter": {
      "name": {
        "$eq": "Charmeleon"
      }
    },
    "nReturned": 1,
    "executionTimeMillisEstimate": 0,
    "works": 613,
    "advanced": 1,
    "needTime": 611,
    "needFetch": 0,
    "saveState": 4,
    "restoreState": 4,
    "isEOF": 1,
    "invalidates": 0,
    "direction": "forward",
    "docsExamined": 611
  }
}
```

# 2. Criar um index um para o campo name

```javascript
SkyWine(mongod-3.0.7) be-mean-pokemons> db.pokemons.createIndex({name:1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}
```

# 3. Refazer a query para o campo name utilizando explain para ver o resultado da busca


```javascript
SkyWine(mongod-3.0.7) be-mean-pokemons> db.pokemons.find({ name: 'Charmeleon' }).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 1,
  "executionTimeMillis": 26,
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
          "[\"Charmeleon\", \"Charmeleon\"]"
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
SkyWine(mongod-3.0.7) be-mean-pokemons> db.pokemons.find({$and: [{atack: 55}, {defese:{$gt:22}}]}).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 0,
  "executionTimeMillis": 0,
  "totalKeysExamined": 0,
  "totalDocsExamined": 611,
  "executionStages": {
    "stage": "COLLSCAN",
    "filter": {
      "$and": [
        {
          "atack": {
            "$eq": 55
          }
        },
        {
          "defese": {
            "$gt": 22
          }
        }
      ]
    },
    "nReturned": 0,
    "executionTimeMillisEstimate": 0,
    "works": 613,
    "advanced": 0,
    "needTime": 612,
    "needFetch": 0,
    "saveState": 4,
    "restoreState": 4,
    "isEOF": 1,
    "invalidates": 0,
    "direction": "forward",
    "docsExamined": 611
  }
}

```


# 5. Criar um index para esses dois campos juntos

```javascript
SkyWine(mongod-3.0.7) be-mean-pokemons> db.pokemons.createIndex({ speed: 1, types: 1 })
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 2,
  "numIndexesAfter": 3,
  "ok": 1
}

```
# 6. Refazer a query para os dois campos juntos utilizando explain para ver o resultado da busca

```javascript
SkyWine(mongod-3.0.7) be-mean-pokemons> db.pokemons.find( { types: 'normal', speed: 56 } ).explain('executionStats').executionStats
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
        "speed": 1,
        "types": 1
      },
      "indexName": "speed_1_types_1",
      "isMultiKey": true,
      "direction": "forward",
      "indexBounds": {
        "speed": [
          "[56.0, 56.0]"
        ],
        "types": [
          "[\"normal\", \"normal\"]"
        ]
      },
      "keysExamined": 1,
      "dupsTested": 1,
      "dupsDropped": 0,
      "seenInvalidated": 0,
      "matchTested": 0
    }
  }
}

```

