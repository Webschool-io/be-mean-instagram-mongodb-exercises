# MongoDB - Aula 06 - Exercício
autor: Anderson da Silva Souza 

## 1. Realizando a query pelo name sem indexe 

,,

db.pokemons.find({ "name": "Zubat"}).explain('executionStats').executionStats
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
        "$eq": "Zubat"
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

## 2. Realizando a query pelo name com index criado

db.pokemons.createIndex({name:1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}

db.pokemons.getIndexes()
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

db.pokemons.find({ "name": "Zubat"}).explain('executionStats').executionStats
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
      "works": 1,
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
          "[\"Zubat\", \"Zubat\"]"
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


## 3. Realizando a query com dois campos juntos sem o index criado

var query = {$and: [{hp:40 }, {speed:55}]}
 db.pokemons.find(query).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 4,
  "executionTimeMillis": 0,
  "totalKeysExamined": 0,
  "totalDocsExamined": 610,
  "executionStages": {
    "stage": "COLLSCAN",
    "filter": {
      "$and": [
        {
          "hp": {
            "$eq": 40
          }
        },
        {
          "speed": {
            "$eq": 55
          }
        }
      ]
    },
    "nReturned": 4,
    "executionTimeMillisEstimate": 0,
    "works": 612,
    "advanced": 4,
    "needTime": 607,
    "needFetch": 0,
    "saveState": 4,
    "restoreState": 4,
    "isEOF": 1,
    "invalidates": 0,
    "direction": "forward",
    "docsExamined": 610
  }
}

## 4. Realizando a query com dois campos juntos e com os dois indexes

db.pokemons.createIndex({hp:1,speed:1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}

db.pokemons.getIndexes()
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
      "hp": 1,
      "speed": 1
    },
    "name": "hp_1_speed_1",
    "ns": "be-mean.pokemons"
  }
]

db.pokemons.find(query).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 4,
  "executionTimeMillis": 17,
  "totalKeysExamined": 4,
  "totalDocsExamined": 4,
  "executionStages": {
    "stage": "FETCH",
    "nReturned": 4,
    "executionTimeMillisEstimate": 0,
    "works": 5,
    "advanced": 4,
    "needTime": 0,
    "needFetch": 0,
    "saveState": 0,
    "restoreState": 0,
    "isEOF": 1,
    "invalidates": 0,
    "docsExamined": 4,
    "alreadyHasObj": 0,
    "inputStage": {
      "stage": "IXSCAN",
      "nReturned": 4,
      "executionTimeMillisEstimate": 0,
      "works": 5,
      "advanced": 4,
      "needTime": 0,
      "needFetch": 0,
      "saveState": 0,
      "restoreState": 0,
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
          "[40.0, 40.0]"
        ],
        "speed": [
          "[55.0, 55.0]"
        ]
      },
      "keysExamined": 4,
      "dupsTested": 0,
      "dupsDropped": 0,
      "seenInvalidated": 0,
      "matchTested": 0
    }
  }
}
