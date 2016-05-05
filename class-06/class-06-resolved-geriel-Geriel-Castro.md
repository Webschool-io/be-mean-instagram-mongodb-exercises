# MongoDB - Aula 06 - Exercício
autor: Geriel Castro

## Query para o campo `name` **SEM** indice
```
db.pokemons.find({ "name": "Charmander"}).explain('executionStats').executionStats

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

## Criar indice pra o campo `name`
```
db.pokemons.createIndex({name: 1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}

```

## Query para o campo `name` **COM** indice ##
```
db.pokemons.find({name: "Charmander"}).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 1,
  "executionTimeMillis": 10,
  "totalKeysExamined": 1,
  "totalDocsExamined": 1,
  "executionStages": {
    "stage": "FETCH",
    "nReturned": 1,
    "executionTimeMillisEstimate": 0,
    "works": 3,
    "advanced": 1,
    "needTime": 0,
    "needFetch": 1,
    "saveState": 1,
    "restoreState": 1,
    "isEOF": 1,
    "invalidates": 0,
    "docsExamined": 1,
    "alreadyHasObj": 0,
    "inputStage": {
      "stage": "IXSCAN",
      "nReturned": 1,
      "executionTimeMillisEstimate": 0,
      "works": 1,
      "advanced": 1,
      "needTime": 0,
      "needFetch": 0,
      "saveState": 1,
      "restoreState": 1,
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
          "[\"Charmander\", \"Charmander\"]"
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

## Query para os dois campos **SEM** indice
```
db.pokemons.find({$and :[{"attack": 52}, {"speed": 65}]}).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 2,
  "executionTimeMillis": 0,
  "totalKeysExamined": 0,
  "totalDocsExamined": 610,
  "executionStages": {
    "stage": "COLLSCAN",
    "filter": {
      "$and": [
        {
          "attack": {
            "$eq": 52
          }
        },
        {
          "speed": {
            "$eq": 65
          }
        }
      ]
    },
    "nReturned": 2,
    "executionTimeMillisEstimate": 0,
    "works": 612,
    "advanced": 2,
    "needTime": 609,
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
## Criar indice para `dois campos` juntos
```
db.pokemons.createIndex({attack: 1, speed: 1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 2,
  "numIndexesAfter": 3,
  "ok": 1
}


```
## Query para os dois campos **com** indice ##
```
db.pokemons.find({$and :[{"attack": 52}, {"speed": 65}]}).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 2,
  "executionTimeMillis": 1,
  "totalKeysExamined": 2,
  "totalDocsExamined": 2,
  "executionStages": {
    "stage": "FETCH",
    "nReturned": 2,
    "executionTimeMillisEstimate": 0,
    "works": 3,
    "advanced": 2,
    "needTime": 0,
    "needFetch": 0,
    "saveState": 0,
    "restoreState": 0,
    "isEOF": 1,
    "invalidates": 0,
    "docsExamined": 2,
    "alreadyHasObj": 0,
    "inputStage": {
      "stage": "IXSCAN",
      "nReturned": 2,
      "executionTimeMillisEstimate": 0,
      "works": 3,
      "advanced": 2,
      "needTime": 0,
      "needFetch": 0,
      "saveState": 0,
      "restoreState": 0,
      "isEOF": 1,
      "invalidates": 0,
      "keyPattern": {
        "attack": 1,
        "speed": 1
      },
      "indexName": "attack_1_speed_1",
      "isMultiKey": false,
      "direction": "forward",
      "indexBounds": {
        "attack": [
          "[52.0, 52.0]"
        ],
        "speed": [
          "[65.0, 65.0]"
        ]
      },
      "keysExamined": 2,
      "dupsTested": 0,
      "dupsDropped": 0,
      "seenInvalidated": 0,
      "matchTested": 0
    }
  }
}

```
