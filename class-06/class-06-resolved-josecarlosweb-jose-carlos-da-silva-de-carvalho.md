# MongoDB - Aula 06 - Exercício
autor: José Carlos da Silva de Carvalho 

## 1. Realizando a query pelo name sem indice

```js
carlos-pc(mongod-3.0.7) be-mean> db.pokemons.find({"name": "Charmander"}).explain('executionStats').executionStats
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


## 2. Realizando a query pelo name com index criado
```js
carlos-pc(mongod-3.0.7) be-mean> db.pokemons.createIndex({name: 1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}
carlos-pc(mongod-3.0.7) be-mean> db.pokemons.find({"name": "Charmander"}).explain('executionStats').executionStats
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


## 3. Realizando a query com dois campos juntos sem o index criado
```js
carlos-pc(mongod-3.0.7) be-mean> var query = {$and: [{"attack": {$lt: 41}}, {"defense": {$gte: 50}}]}
carlos-pc(mongod-3.0.7) be-mean> db.pokemons.find(query).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 36,
  "executionTimeMillis": 0,
  "totalKeysExamined": 0,
  "totalDocsExamined": 610,
  "executionStages": {
    "stage": "COLLSCAN",
    "filter": {
      "$and": [
        {
          "attack": {
            "$lt": 41
          }
        },
        {
          "defense": {
            "$gte": 50
          }
        }
      ]
    },
    "nReturned": 36,
    "executionTimeMillisEstimate": 0,
    "works": 612,
    "advanced": 36,
    "needTime": 575,
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


## 4. Realizando a query com dois campos juntos e com os dois indexes
```js
carlos-pc(mongod-3.0.7) be-mean> db.pokemons.createIndex({attack: 1, defense: 1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 2,
  "numIndexesAfter": 3,
  "ok": 1
}
carlos-pc(mongod-3.0.7) be-mean> db.pokemons.find(query).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 36,
  "executionTimeMillis": 0,
  "totalKeysExamined": 47,
  "totalDocsExamined": 36,
  "executionStages": {
    "stage": "FETCH",
    "nReturned": 36,
    "executionTimeMillisEstimate": 0,
    "works": 48,
    "advanced": 36,
    "needTime": 11,
    "needFetch": 0,
    "saveState": 0,
    "restoreState": 0,
    "isEOF": 1,
    "invalidates": 0,
    "docsExamined": 36,
    "alreadyHasObj": 0,
    "inputStage": {
      "stage": "IXSCAN",
      "nReturned": 36,
      "executionTimeMillisEstimate": 0,
      "works": 48,
      "advanced": 36,
      "needTime": 11,
      "needFetch": 0,
      "saveState": 0,
      "restoreState": 0,
      "isEOF": 1,
      "invalidates": 0,
      "keyPattern": {
        "attack": 1,
        "defense": 1
      },
      "indexName": "attack_1_defense_1",
      "isMultiKey": false,
      "direction": "forward",
      "indexBounds": {
        "attack": [
          "[-inf.0, 41.0)"
        ],
        "defense": [
          "[50.0, inf.0]"
        ]
      },
      "keysExamined": 47,
      "dupsTested": 0,
      "dupsDropped": 0,
      "seenInvalidated": 0,
      "matchTested": 0
    }
  }
}
```

