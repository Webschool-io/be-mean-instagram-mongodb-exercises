# MongoDB - Aula 06 - Exercício
Autor: Thais Zambe

## 1. Fazer uma query para o campo `name` utilizando `explain`.

```js
ythati-be-mean-instagram-2238559(mongod-3.0.9) be-mean> db.pokemons.find({name: "Pikachu"}).explain("executionStats").executionStats
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
        "$eq": "Pikachu"
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

## 2. Criar um índice para o campo `name`.

```js
ythati-be-mean-instagram-2238559(mongod-3.0.9) be-mean> db.pokemons.createIndex({name: 1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}
```

```js
ythati-be-mean-instagram-2238559(mongod-3.0.9) be-mean> db.pokemons.getIndexes()
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
```

## 3. Refazer a query para o campo `name` utilizando `explain`.

```js
ythati-be-mean-instagram-2238559(mongod-3.0.9) be-mean> db.pokemons.find({name: "Pikachu"}).explain("executionStats").executionStats
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
          "[\"Pikachu\", \"Pikachu\"]"
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

## 4. Fazer uma query para dois campos quaisquer utilizando `explain`.

```js
ythati-be-mean-instagram-2238559(mongod-3.0.9) be-mean> db.pokemons.find({$and: [{attack: {$lt: 40}}, {speed: {$gt: 100}}]}).explain("executionStats").executionStats
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
            "$lt": 40
          }
        },
        {
          "speed": {
            "$gt": 100
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

## 5. Criar um índice para os dois campos do exercício anterior juntos.

```js
ythati-be-mean-instagram-2238559(mongod-3.0.9) be-mean> db.pokemons.createIndex({attack: 1, speed: 1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}
```

```js
ythati-be-mean-instagram-2238559(mongod-3.0.9) be-mean> db.pokemons.getIndexes()
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
      "attack": 1,
      "speed": 1
    },
    "name": "attack_1_speed_1",
    "ns": "be-mean.pokemons"
  }
]
```

## 6. Refazer a query para os mesmos dois campos utilizando `explain`.

```js
ythati-be-mean-instagram-2238559(mongod-3.0.9) be-mean> db.pokemons.find({$and: [{attack: {$lt: 40}}, {speed: {$gt: 100}}]}).explain("executionStats").executionStats
{
  "executionSuccess": true,
  "nReturned": 1,
  "executionTimeMillis": 0,
  "totalKeysExamined": 15,
  "totalDocsExamined": 1,
  "executionStages": {
    "stage": "FETCH",
    "nReturned": 1,
    "executionTimeMillisEstimate": 0,
    "works": 16,
    "advanced": 1,
    "needTime": 14,
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
      "works": 16,
      "advanced": 1,
      "needTime": 14,
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
          "[-inf.0, 40.0)"
        ],
        "speed": [
          "(100.0, inf.0]"
        ]
      },
      "keysExamined": 15,
      "dupsTested": 0,
      "dupsDropped": 0,
      "seenInvalidated": 0,
      "matchTested": 0
    }
  }
}
```