# MongoDB - Aula 06 - Exercício
**autor:** Eric Cristhiano Marcelino da Silva

## 1. Fazer uma query para o campo `name` utilizando `explain` para ver o resultado da busca
```js
db.pokemons.find({ name: /scizor/i }).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 1,
  "executionTimeMillis": 0,
  "totalKeysExamined": 0,
  "totalDocsExamined": 7,
  "executionStages": {
    "stage": "COLLSCAN",
    "filter": {
      "name": /scizor/i
    },
    "nReturned": 1,
    "executionTimeMillisEstimate": 0,
    "works": 9,
    "advanced": 1,
    "needTime": 7,
    "needFetch": 0,
    "saveState": 0,
    "restoreState": 0,
    "isEOF": 1,
    "invalidates": 0,
    "direction": "forward",
    "docsExamined": 7
  }
}
```
## 2. Criar um `index` um para o campo `name`
```js
db.pokemons.createIndex({name: 1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}
```
## 3. Refazer a query para o campo `name` utilizando `explain` para ver o resultado da busca
```js
 db.pokemons.find({ name: /scizor/i }).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 1,
  "executionTimeMillis": 11,
  "totalKeysExamined": 7,
  "totalDocsExamined": 1,
  "executionStages": {
    "stage": "FETCH",
    "nReturned": 1,
    "executionTimeMillisEstimate": 0,
    "works": 8,
    "advanced": 1,
    "needTime": 6,
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
        "name": /scizor/i
      },
      "nReturned": 1,
      "executionTimeMillisEstimate": 0,
      "works": 7,
      "advanced": 1,
      "needTime": 6,
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
          "[/scizor/i, /scizor/i]"
        ]
      },
      "keysExamined": 7,
      "dupsTested": 0,
      "dupsDropped": 0,
      "seenInvalidated": 0,
      "matchTested": 1
    }
  }
}
```
## 4. Fazer uma query para dois campos juntos utilizando `explain` para ver o resultado da busca
```js
db.pokemons.find({ $and: [{height: {$gte: 1}}, {attack: {$gte: 60}}] }).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 4,
  "executionTimeMillis": 0,
  "totalKeysExamined": 0,
  "totalDocsExamined": 7,
  "executionStages": {
    "stage": "COLLSCAN",
    "filter": {
      "$and": [
        {
          "attack": {
            "$gte": 60
          }
        },
        {
          "height": {
            "$gte": 1
          }
        }
      ]
    },
    "nReturned": 4,
    "executionTimeMillisEstimate": 0,
    "works": 9,
    "advanced": 4,
    "needTime": 4,
    "needFetch": 0,
    "saveState": 0,
    "restoreState": 0,
    "isEOF": 1,
    "invalidates": 0,
    "direction": "forward",
    "docsExamined": 7
  }
}

```
## 5. Criar um `index` para esses dois campos juntos
```js
db.pokemons.createIndex({height: 1, attack: 1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 2,
  "numIndexesAfter": 3,
  "ok": 1
}

```
## 6. Refazer a query para os dois campos juntos utilizando `explain` para ver o resultado da busca
```js
db.pokemons.find({ $and: [{height: {$gte: 1}}, {attack: {$gte: 60}}] }).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 4,
  "executionTimeMillis": 0,
  "totalKeysExamined": 5,
  "totalDocsExamined": 4,
  "executionStages": {
    "stage": "FETCH",
    "nReturned": 4,
    "executionTimeMillisEstimate": 0,
    "works": 6,
    "advanced": 4,
    "needTime": 1,
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
      "needTime": 1,
      "needFetch": 0,
      "saveState": 0,
      "restoreState": 0,
      "isEOF": 1,
      "invalidates": 0,
      "keyPattern": {
        "height": 1,
        "attack": 1
      },
      "indexName": "height_1_attack_1",
      "isMultiKey": false,
      "direction": "forward",
      "indexBounds": {
        "height": [
          "[1.0, inf.0]"
        ],
        "attack": [
          "[60.0, inf.0]"
        ]
      },
      "keysExamined": 5,
      "dupsTested": 0,
      "dupsDropped": 0,
      "seenInvalidated": 0,
      "matchTested": 0
    }
  }
}

```