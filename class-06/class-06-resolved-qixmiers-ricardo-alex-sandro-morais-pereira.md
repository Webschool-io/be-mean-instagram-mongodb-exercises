# MongoDB - Aula 06 - Exercício
autor: Ricardo Pereira

## 1. Query para o campo name utilizando explain ##

```
MacBook-Pro-de-Ricardo(mongod-3.0.3) be-mean> db.pokemons.find({name: "Charizard"}).explain("executionStats").executionStats
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
        "$eq": "Charizard"
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

## 2. Index para o campo name ##

```
MacBook-Pro-de-Ricardo(mongod-3.0.3) be-mean> db.pokemons.createIndex({name: 1})

{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}
```

## 3. Query com index para ver a diferenca de resultado ##
```
MacBook-Pro-de-Ricardo(mongod-3.0.3) be-mean> db.pokemons.find({name: "Charizard"}).explain("executionStats").executionStats
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
          "[\"Charizard\", \"Charizard\"]"
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

## 4. Buscando dois campos sem index ##

```
MacBook-Pro-de-Ricardo(mongod-3.0.3) be-mean> db.pokemons.find({defense: {$gt: 70}, attack: {$gt: 100}}).explain("executionStats").executionStats
{
  "executionSuccess": true,
  "nReturned": 72,
  "executionTimeMillis": 66,
  "totalKeysExamined": 0,
  "totalDocsExamined": 610,
  "executionStages": {
    "stage": "COLLSCAN",
    "filter": {
      "$and": [
        {
          "attack": {
            "$gt": 100
          }
        },
        {
          "defense": {
            "$gt": 70
          }
        }
      ]
    },
    "nReturned": 72,
    "executionTimeMillisEstimate": 0,
    "works": 612,
    "advanced": 72,
    "needTime": 539,
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

## 5. Criando index para os dois campos ##

```
MacBook-Pro-de-Ricardo(mongod-3.0.3) be-mean> db.pokemons.createIndex({defense: 1, attack: 1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 2,
  "numIndexesAfter": 3,
  "ok": 1
}
```

## 6. Buscando dois campos com index ##

```
MacBook-Pro-de-Ricardo(mongod-3.0.3) be-mean> db.pokemons.find({defense: {$gt: 70}, attack: {$gt: 100}}).explain("executionStats").executionStats
{
  "executionSuccess": true,
  "nReturned": 72,
  "executionTimeMillis": 101,
  "totalKeysExamined": 118,
  "totalDocsExamined": 72,
  "executionStages": {
    "stage": "FETCH",
    "nReturned": 72,
    "executionTimeMillisEstimate": 0,
    "works": 118,
    "advanced": 72,
    "needTime": 45,
    "needFetch": 0,
    "saveState": 0,
    "restoreState": 0,
    "isEOF": 1,
    "invalidates": 0,
    "docsExamined": 72,
    "alreadyHasObj": 0,
    "inputStage": {
      "stage": "IXSCAN",
      "nReturned": 72,
      "executionTimeMillisEstimate": 0,
      "works": 118,
      "advanced": 72,
      "needTime": 45,
      "needFetch": 0,
      "saveState": 0,
      "restoreState": 0,
      "isEOF": 1,
      "invalidates": 0,
      "keyPattern": {
        "defense": 1,
        "attack": 1
      },
      "indexName": "defense_1_attack_1",
      "isMultiKey": false,
      "direction": "forward",
      "indexBounds": {
        "defense": [
          "(70.0, inf.0]"
        ],
        "attack": [
          "(100.0, inf.0]"
        ]
      },
      "keysExamined": 118,
      "dupsTested": 0,
      "dupsDropped": 0,
      "seenInvalidated": 0,
      "matchTested": 0
    }
  }
}
```
