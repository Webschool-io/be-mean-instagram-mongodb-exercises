# MongoDB - Aula 06 - Exercício
autor: Vander Amorin

## 1. Query pelo campo 'name' sem índice
```
var query = { name: /charmander/i }

 be-mean-instagram> db.pokemons.find(query).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 1,
  "executionTimeMillis": 0,
  "totalKeysExamined": 0,
  "totalDocsExamined": 13,
  "executionStages": {
    "stage": "COLLSCAN",
    "filter": {
      "name": /charmander/i
    },
    "nReturned": 1,
    "executionTimeMillisEstimate": 0,
    "works": 15,
    "advanced": 1,
    "needTime": 13,
    "needFetch": 0,
    "saveState": 0,
    "restoreState": 0,
    "isEOF": 1,
    "invalidates": 0,
    "direction": "forward",
    "docsExamined": 13
  }
}
```


## 2. Criar índice para o campo 'name'
```
db.pokemons.createIndex({ name: 1 })
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}
```

## 3. Query pelo campo 'name' com índice
```
be-mean-instagram> db.pokemons.find(query).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 1,
  "executionTimeMillis": 0,
  "totalKeysExamined": 13,
  "totalDocsExamined": 1,
  "executionStages": {
    "stage": "FETCH",
    "nReturned": 1,
    "executionTimeMillisEstimate": 0,
    "works": 14,
    "advanced": 1,
    "needTime": 12,
    "needFetch": 0,
    "saveState": 0,
    "restoreState": 0,
    "isEOF": 1,
    "invalidates": 0,
    "docsExamined": 1,
    "alreadyHasObj": 0,
    "inputStage": {
      "stage": "IXSCAN",
      "filter": {
        "name": /charmander/i
      },
      "nReturned": 1,
      "executionTimeMillisEstimate": 0,
      "works": 13,
      "advanced": 1,
      "needTime": 12,
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
          "[\"\", {})",
          "[/charmander/i, /charmander/i]"
        ]
      },
      "keysExamined": 13,
      "dupsTested": 0,
      "dupsDropped": 0,
      "seenInvalidated": 0,
      "matchTested": 1
    }
  }
}

```

## 4. Query por 2 campos não indexados
```
var query = {

  $and:[

    { attack: 40 },
    { height: 1.6 }

  ]
}

be-mean-instagram> db.pokemons.find(query).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 1,
  "executionTimeMillis": 0,
  "totalKeysExamined": 0,
  "totalDocsExamined": 13,
  "executionStages": {
    "stage": "COLLSCAN",
    "filter": {
      "$and": [
        {
          "attack": {
            "$eq": 40
          }
        },
        {
          "height": {
            "$eq": 1.6
          }
        }
      ]
    },
    "nReturned": 1,
    "executionTimeMillisEstimate": 0,
    "works": 15,
    "advanced": 1,
    "needTime": 13,
    "needFetch": 0,
    "saveState": 0,
    "restoreState": 0,
    "isEOF": 1,
    "invalidates": 0,
    "direction": "forward",
    "docsExamined": 13
  }
}


```

## 5. Criar index composto para dois campos
```
be-mean-instagram> db.pokemons.createIndex({ attack: 1, height: 1  })
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}

```

## 6. Query pelos dois campos agora indexados
```
var query = {

  $and:[

    { attack: 40 },
    { height: 1.6 }

  ]
}

be-mean-instagram> db.pokemons.find(query).explain('executionStats').executionStats
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
        "attack": 1,
        "height": 1
      },
      "indexName": "attack_1_height_1",
      "isMultiKey": false,
      "direction": "forward",
      "indexBounds": {
        "attack": [
          "[40.0, 40.0]"
        ],
        "height": [
          "[1.6, 1.6]"
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

