# MongoDB - Aula 06 - Exercício
autor: Thiago Rodrigues Magalhães


## Query para o campo `name` **sem** indice ##
```
thiago(mongod-3.0.7) be-mean> db.restaurantes.find({ name: "Morris Park Bake Shop" }).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 1,
  "executionTimeMillis": 175,
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
    "executionTimeMillisEstimate": 150,
    "works": 25394,
    "advanced": 1,
    "needTime": 25359,
    "needFetch": 33,
    "saveState": 219,
    "restoreState": 219,
    "isEOF": 1,
    "invalidates": 0,
    "direction": "forward",
    "docsExamined": 25359
  }
}

```


## Criar indice pra o campo `name` ##
```
thiago(mongod-3.0.7) be-mean> db.restaurantes.createIndex({ name: 1 })
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}
```


## Query para o campo `name` **com** indice ##
```
thiago(mongod-3.0.7) be-mean> db.restaurantes.find({ name: "Morris Park Bake Shop" }).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 1,
  "executionTimeMillis": 23,
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


## Query para os dois campos **sem** indice ##
```
marcelo-js(mongod-3.0.7) be-mean> db.pokemons.find({$and: [{attack: 25}, {defense: 50}]}).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 1,
  "executionTimeMillis": 0,
  "totalKeysExamined": 0,
  "totalDocsExamined": 610,
  "executionStages": {
    "stage": "COLLSCAN",
    "filter": {
      "$and": [
        {
          "attack": {
            "$eq": 25
          }
        },
        {
          "defense": {
            "$eq": 50
          }
        }
      ]
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


## Criar indice para `dois campos` juntos ##
```
thiago(mongod-3.0.7) be-mean> db.restaurantes.createIndex({ borough: 1, cuisine: 1 })
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 2,
  "numIndexesAfter": 3,
  "ok": 1
}

```


## Query para os dois campos **com** indice ##
```
thiago(mongod-3.0.7) be-mean> db.restaurantes.find({ $and: [{borough: "Bronx"}, {cuisine: "Bakery"}] }).explain('executionStats').executionStats
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