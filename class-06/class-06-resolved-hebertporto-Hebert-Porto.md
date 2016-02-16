# MongoDb - Aula 06 - Exercício Resolvido - Hebert Porto
Autor: Hebert Porto

## 1. Fazer uma query para o campo `name` utilizando `explain` para ver o resultado da busca
```js
vagrant-ubuntu-trusty-64(mongod-3.0.9) be-mean> db.pokemons.find({ name: /pikachu/i }).explain('executionStats').executionStats.totalDocsExamined
610

```

## 2. Criar um `index` um para o campo `name`
```js
vagrant-ubuntu-trusty-64(mongod-3.0.9) be-mean> db.pokemons.createIndex({name: 1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}
```

## 3. Refazer a query para o campo `name` utilizando `explain` para ver o resultado da busca
```js
vagrant-ubuntu-trusty-64(mongod-3.0.9) be-mean> db.pokemons.find({ name: /pikachu/i }).explain('executionStats').executionStats.executionTimeMillis
0
```

## 4. Fazer uma query para dois campos juntos utilizando `explain` para ver o resultado da busca
```js
vagrant-ubuntu-trusty-64(mongod-3.0.9) be-mean> db.pokemons.find({$and : [{speed: 50}, {hp: { $gte: 50}}]}).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "speed": {
            "$eq": 50
          }
        },
        {
          "hp": {
            "$gte": 50
          }
        }
      ]
    },
    "winningPlan": {
      "stage": "COLLSCAN",
      "filter": {
        "$and": [
          {
            "speed": {
              "$eq": 50
            }
          },
          {
            "hp": {
              "$gte": 50
            }
          }
        ]
      },
      "direction": "forward"
    },
    "rejectedPlans": [ ]
  },
  "executionStats": {
    "executionSuccess": true,
    "nReturned": 26,
    "executionTimeMillis": 1,
    "totalKeysExamined": 0,
    "totalDocsExamined": 610,
    "executionStages": {
      "stage": "COLLSCAN",
      "filter": {
        "$and": [
          {
            "speed": {
              "$eq": 50
            }
          },
          {
            "hp": {
              "$gte": 50
            }
          }
        ]
      },
      "nReturned": 26,
      "executionTimeMillisEstimate": 0,
      "works": 612,
      "advanced": 26,
      "needTime": 585,
      "needFetch": 0,
      "saveState": 4,
      "restoreState": 4,
      "isEOF": 1,
      "invalidates": 0,
      "direction": "forward",
      "docsExamined": 610
    }
  },
  "serverInfo": {
    "host": "vagrant-ubuntu-trusty-64",
    "port": 27017,
    "version": "3.0.9",
    "gitVersion": "20d60d3491908f1ae252fe452300de3978a040c7"
  },
  "ok": 1
}
```

## 5. Criar um `index` para esses dois campos juntos
```js
vagrant-ubuntu-trusty-64(mongod-3.0.9) be-mean> db.pokemons.createIndex({speed: 1, hp: 1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 2,
  "numIndexesAfter": 3,
  "ok": 1
}
```

## 6. Refazer a query para os dois campos juntos utilizando `explain` para ver o resultado da busca
```js
vagrant-ubuntu-trusty-64(mongod-3.0.9) be-mean> db.pokemons.find({$and : [{speed: 50}, {hp: { $gte: 50}}]}).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "speed": {
            "$eq": 50
          }
        },
        {
          "hp": {
            "$gte": 50
          }
        }
      ]
    },
    "winningPlan": {
      "stage": "FETCH",
      "inputStage": {
        "stage": "IXSCAN",
        "keyPattern": {
          "speed": 1,
          "hp": 1
        },
        "indexName": "speed_1_hp_1",
        "isMultiKey": false,
        "direction": "forward",
        "indexBounds": {
          "speed": [
            "[50.0, 50.0]"
          ],
          "hp": [
            "[50.0, inf.0]"
          ]
        }
      }
    },
    "rejectedPlans": [ ]
  },
  "executionStats": {
    "executionSuccess": true,
    "nReturned": 26,
    "executionTimeMillis": 1,
    "totalKeysExamined": 26,
    "totalDocsExamined": 26,
    "executionStages": {
      "stage": "FETCH",
      "nReturned": 26,
      "executionTimeMillisEstimate": 0,
      "works": 27,
      "advanced": 26,
      "needTime": 0,
      "needFetch": 0,
      "saveState": 0,
      "restoreState": 0,
      "isEOF": 1,
      "invalidates": 0,
      "docsExamined": 26,
      "alreadyHasObj": 0,
      "inputStage": {
        "stage": "IXSCAN",
        "nReturned": 26,
        "executionTimeMillisEstimate": 0,
        "works": 27,
        "advanced": 26,
        "needTime": 0,
        "needFetch": 0,
        "saveState": 0,
        "restoreState": 0,
        "isEOF": 1,
        "invalidates": 0,
        "keyPattern": {
          "speed": 1,
          "hp": 1
        },
        "indexName": "speed_1_hp_1",
        "isMultiKey": false,
        "direction": "forward",
        "indexBounds": {
          "speed": [
            "[50.0, 50.0]"
          ],
          "hp": [
            "[50.0, inf.0]"
          ]
        },
        "keysExamined": 26,
        "dupsTested": 0,
        "dupsDropped": 0,
        "seenInvalidated": 0,
        "matchTested": 0
      }
    }
  },
  "serverInfo": {
    "host": "vagrant-ubuntu-trusty-64",
    "port": 27017,
    "version": "3.0.9",
    "gitVersion": "20d60d3491908f1ae252fe452300de3978a040c7"
  },
  "ok": 1
}
```