# MongoDB - Aula 06 - Exercício
autor: Filipe Leuch Bonfim

## 1. Na coleção de pokemons, criar um **índice** para o campo ``name``, e outro para outros dois campos

### Campo ``name``
```javascript
db.pokemons.createIndex({ name: 1 })
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}
```

### Campos ``hp`` e ``speed``
```javascript
db.pokemons.createIndex({ hp: 1, speed: 1 })
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 2,
  "numIndexesAfter": 3,
  "ok": 1
}

```


## 2. Fazer uma query com índice e outra sem para ``name``, e para os outros dois campos definidos

### Campo ``name``
#### Sem índice
```javascript
db.pokemons.find({ "name": "Charmeleon" }).explain('executionStats').executionStats
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
        "$eq": "Charmeleon"
      }
    },
    "nReturned": 1,
    "executionTimeMillisEstimate": 0,
    "works": 612,
    "advanced": 1,
    "needTime": 610,
    "needFetch": 0,
    "saveState": 4,
    "restoreState": 4,
    "isEOF": 1,
    "invalidates": 0,
    "direction": "forward",
    "docsExamined": 610
  }
}
```
#### Com índice
```javascript
db.pokemons.find({ "name": "Charmeleon" }).explain('executionStats').executionStats
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

### Campos ``hp`` e ``speed``
#### Sem índice
```javascript
db.pokemons.find({ hp: {$gte: 50}, speed: {$lt: 70} }).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 253,
  "executionTimeMillis": 0,
  "totalKeysExamined": 0,
  "totalDocsExamined": 610,
  "executionStages": {
    "stage": "COLLSCAN",
    "filter": {
      "$and": [
        {
          "speed": {
            "$lt": 70
          }
        },
        {
          "hp": {
            "$gte": 50
          }
        }
      ]
    },
    "nReturned": 253,
    "executionTimeMillisEstimate": 0,
    "works": 612,
    "advanced": 253,
    "needTime": 358,
    "needFetch": 0,
    "saveState": 4,
    "restoreState": 4,
    "isEOF": 1,
    "invalidates": 0,
    "direction": "forward",
    "docsExamined": 610
  }
}

```

#### Com índice
```javascript
db.pokemons.find({ hp: {$gte: 50}, speed: {$lt: 70} }).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 253,
  "executionTimeMillis": 0,
  "totalKeysExamined": 291,
  "totalDocsExamined": 253,
  "executionStages": {
    "stage": "FETCH",
    "nReturned": 253,
    "executionTimeMillisEstimate": 0,
    "works": 292,
    "advanced": 253,
    "needTime": 38,
    "needFetch": 0,
    "saveState": 2,
    "restoreState": 2,
    "isEOF": 1,
    "invalidates": 0,
    "docsExamined": 253,
    "alreadyHasObj": 0,
    "inputStage": {
      "stage": "IXSCAN",
      "nReturned": 253,
      "executionTimeMillisEstimate": 0,
      "works": 291,
      "advanced": 253,
      "needTime": 38,
      "needFetch": 0,
      "saveState": 2,
      "restoreState": 2,
      "isEOF": 1,
      "invalidates": 0,
      "keyPattern": {
        "hp": 1,
        "speed": 1
      },
      "indexName": "hp_1_speed_1",
      "isMultiKey": false,
      "direction": "forward",
      "indexBounds": {
        "hp": [
          "[50.0, inf.0]"
        ],
        "speed": [
          "[-inf.0, 70.0)"
        ]
      },
      "keysExamined": 291,
      "dupsTested": 0,
      "dupsDropped": 0,
      "seenInvalidated": 0,
      "matchTested": 0
    }
  }
}
```
