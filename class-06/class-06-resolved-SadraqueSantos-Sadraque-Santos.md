#MongoDB - Aula 06 - Exercício
Autor: Sadraque Santos

## 1. Fazer uma query para o campo name utilizando explain para ver o resultado da busca

```js
db.pokemons.find({"name": "Pikachu"}).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 1,
  "executionTimeMillis": 0,
  "totalKeysExamined": 0,
  "totalDocsExamined": 620,
  "executionStages": {
    "stage": "COLLSCAN",
    "filter": {
      "name": {
        "$eq": "Pikachu"
      }
    },
    "nReturned": 1,
    "executionTimeMillisEstimate": 0,
    "works": 622,
    "advanced": 1,
    "needTime": 620,
    "needYield": 0,
    "saveState": 4,
    "restoreState": 4,
    "isEOF": 1,
    "invalidates": 0,
    "direction": "forward",
    "docsExamined": 620
  }
}
```

## 2. Criar um index um para o campo name
```js
db.pokemons.createIndex({ name: 1 })
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}
```

## 3. Refazer a query para o campo name utilizando explain para ver o resultado da busca
```js
db.restaurantes.find({"name": "Pikachu"}).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 0,
  "executionTimeMillis": 0,
  "totalKeysExamined": 0,
  "totalDocsExamined": 0,
  "executionStages": {
    "stage": "FETCH",
    "nReturned": 0,
    "executionTimeMillisEstimate": 0,
    "works": 2,
    "advanced": 0,
    "needTime": 0,
    "needYield": 0,
    "saveState": 0,
    "restoreState": 0,
    "isEOF": 1,
    "invalidates": 0,
    "docsExamined": 0,
    "alreadyHasObj": 0,
    "inputStage": {
      "stage": "IXSCAN",
      "nReturned": 0,
      "executionTimeMillisEstimate": 0,
      "works": 1,
      "advanced": 0,
      "needTime": 0,
      "needYield": 0,
      "saveState": 0,
      "restoreState": 0,
      "isEOF": 1,
      "invalidates": 0,
      "keyPattern": {
        "name": 1
      },
      "indexName": "name_1",
      "isMultiKey": false,
      "isUnique": false,
      "isSparse": false,
      "isPartial": false,
      "indexVersion": 1,
      "direction": "forward",
      "indexBounds": {
        "name": [
          "[\"Pikachu\", \"Pikachu\"]"
        ]
      },
      "keysExamined": 0,
      "dupsTested": 0,
      "dupsDropped": 0,
      "seenInvalidated": 0
    }
  }
}
```

## 4. Fazer uma query para dois campos juntos utilizando explain para ver o resultado da busca
```js
var query = {attack: {$gt: 80}, defense: {$gt: 80}}
db.pokemons.find(query).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 114,
  "executionTimeMillis": 0,
  "totalKeysExamined": 0,
  "totalDocsExamined": 620,
  "executionStages": {
    "stage": "COLLSCAN",
    "filter": {
      "$and": [
        {
          "attack": {
            "$gt": 80
          }
        },
        {
          "defense": {
            "$gt": 80
          }
        }
      ]
    },
    "nReturned": 114,
    "executionTimeMillisEstimate": 0,
    "works": 622,
    "advanced": 114,
    "needTime": 507,
    "needYield": 0,
    "saveState": 4,
    "restoreState": 4,
    "isEOF": 1,
    "invalidates": 0,
    "direction": "forward",
    "docsExamined": 620
  }
}
```

## 5. Criar um index para esses dois campos juntos
```js
db.pokemons.createIndex({ attack: 1, defense: 1 })
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 2,
  "numIndexesAfter": 3,
  "ok": 1
}
```

## 6. Refazer a query para os dois campos juntos utilizando explain para ver o resultado da busca
```js
var query = {attack: {$gt: 80}, defense: {$gt: 80}}
db.pokemons.find(query).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 114,
  "executionTimeMillis": 0,
  "totalKeysExamined": 144,
  "totalDocsExamined": 114,
  "executionStages": {
    "stage": "FETCH",
    "nReturned": 114,
    "executionTimeMillisEstimate": 0,
    "works": 145,
    "advanced": 114,
    "needTime": 30,
    "needYield": 0,
    "saveState": 1,
    "restoreState": 1,
    "isEOF": 1,
    "invalidates": 0,
    "docsExamined": 114,
    "alreadyHasObj": 0,
    "inputStage": {
      "stage": "IXSCAN",
      "nReturned": 114,
      "executionTimeMillisEstimate": 0,
      "works": 145,
      "advanced": 114,
      "needTime": 30,
      "needYield": 0,
      "saveState": 1,
      "restoreState": 1,
      "isEOF": 1,
      "invalidates": 0,
      "keyPattern": {
        "attack": 1,
        "defense": 1
      },
      "indexName": "attack_1_defense_1",
      "isMultiKey": false,
      "isUnique": false,
      "isSparse": false,
      "isPartial": false,
      "indexVersion": 1,
      "direction": "forward",
      "indexBounds": {
        "attack": [
          "(80.0, inf.0]"
        ],
        "defense": [
          "(80.0, inf.0]"
        ]
      },
      "keysExamined": 144,
      "dupsTested": 0,
      "dupsDropped": 0,
      "seenInvalidated": 0
    }
  }
}
```
