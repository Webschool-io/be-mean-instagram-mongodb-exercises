# MongoDB - Aula 06 - Exercício
autor: Lucas de Oliveira

**1** - Query para o campo `name` **sem** índice utilizando `explain` para ver o resultado da busca

```js
> db.pokemons.find({ name: /pikachu/i }).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 1,
  "executionTimeMillis": 62,
  "totalKeysExamined": 0,
  "totalDocsExamined": 610,
  "executionStages": {
    "stage": "COLLSCAN",
    "filter": {
      "name": /pikachu/i
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

**2** - Criar um `índice` um para o campo `name`

```js
> db.pokemons.createIndex({ name: 1 })
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 2,
  "numIndexesAfter": 3,
  "ok": 1
}
```

**3** - Query para o campo `name` com `índice` utilizando `explain`

```js
> db.pokemons.find({ name: /pikachu/i }).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 1,
  "executionTimeMillis": 0,
  "totalKeysExamined": 610,
  "totalDocsExamined": 1,
  "executionStages": {
    "stage": "FETCH",
    "nReturned": 1,
    "executionTimeMillisEstimate": 0,
    "works": 611,
    "advanced": 1,
    "needTime": 609,
    "needFetch": 0,
    "saveState": 4,
    "restoreState": 4,
    "isEOF": 1,
    "invalidates": 0,
    "docsExamined": 1,
    "alreadyHasObj": 0,
    "inputStage": {
      "stage": "IXSCAN",
      "filter": {
        "name": /pikachu/i
      },
      "nReturned": 1,
      "executionTimeMillisEstimate": 0,
      "works": 610,
      "advanced": 1,
      "needTime": 609,
      "needFetch": 0,
      "saveState": 4,
      "restoreState": 4,
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
          "[/pikachu/i, /pikachu/i]"
        ]
      },
      "keysExamined": 610,
      "dupsTested": 0,
      "dupsDropped": 0,
      "seenInvalidated": 0,
      "matchTested": 1
    }
  }
}
```

**4** - Query para dois campos **sem** `índice`

```js
> db.pokemons.find({$and: [{attack: 60}, {defense: 30}]}).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 3,
  "executionTimeMillis": 0,
  "totalKeysExamined": 0,
  "totalDocsExamined": 610,
  "executionStages": {
    "stage": "COLLSCAN",
    "filter": {
      "$and": [
        {
          "attack": {
            "$eq": 60
          }
        },
        {
          "defense": {
            "$eq": 30
          }
        }
      ]
    },
    "nReturned": 3,
    "executionTimeMillisEstimate": 0,
    "works": 612,
    "advanced": 3,
    "needTime": 608,
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

**5** - Criar índice para `dois campos` juntos

```js
> db.pokemons.createIndex({attack: 1, defense: 1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}
```

**6** - Query para os `dois campos` **com** índice

```js
> db.pokemons.find({$and: [{attack: 30}, {defense: 60}]}).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean-pokemons.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "attack": {
            "$eq": 30
          }
        },
        {
          "defense": {
            "$eq": 60
          }
        }
      ]
    },
    "winningPlan": {
      "stage": "FETCH",
      "inputStage": {
        "stage": "IXSCAN",
        "keyPattern": {
          "attack": 1,
          "defense": 1
        },
        "indexName": "attack_1_defense_1",
        "isMultiKey": false,
        "direction": "forward",
        "indexBounds": {
          "attack": [
            "[30.0, 30.0]"
          ],
          "defense": [
            "[60.0, 60.0]"
          ]
        }
      }
    },
    "rejectedPlans": [ ]
  },
  "executionStats": {
    "executionSuccess": true,
    "nReturned": 0,
    "executionTimeMillis": 0,
    "totalKeysExamined": 0,
    "totalDocsExamined": 0,
    "executionStages": {
      "stage": "FETCH",
      "nReturned": 0,
      "executionTimeMillisEstimate": 0,
      "works": 1,
      "advanced": 0,
      "needTime": 0,
      "needFetch": 0,
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
            "[30.0, 30.0]"
          ],
          "defense": [
            "[60.0, 60.0]"
          ]
        },
        "keysExamined": 0,
        "dupsTested": 0,
        "dupsDropped": 0,
        "seenInvalidated": 0,
        "matchTested": 0
      }
    }
  },
  "serverInfo": {
    "host": "lucas-Vostro-14-5480",
    "port": 27017,
    "version": "3.0.7",
    "gitVersion": "6ce7cbe8c6b899552dadd907604559806aa2e9bd"
  },
  "ok": 1
}
```
