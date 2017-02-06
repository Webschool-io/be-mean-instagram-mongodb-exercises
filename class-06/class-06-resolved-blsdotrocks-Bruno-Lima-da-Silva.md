# MongoDB - Aula 06 - Exercício

autor: Bruno Lima da Silva

## 1. Fazer uma query para o campo name utilizando explain para ver o resultado da busca.
```js
blsrocks(mongod-3.2.9) be-mean> db.pokemons.find({"name": "Caterpie"}).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "name": {
        "$eq": "Caterpie"
      }
    },
    "winningPlan": {
      "stage": "COLLSCAN",
      "filter": {
        "name": {
          "$eq": "Caterpie"
        }
      },
      "direction": "forward"
    },
    "rejectedPlans": [ ]
  },
  "executionStats": {
    "executionSuccess": true,
    "nReturned": 1,
    "executionTimeMillis": 1,
    "totalKeysExamined": 0,
    "totalDocsExamined": 610,
    "executionStages": {
      "stage": "COLLSCAN",
      "filter": {
        "name": {
          "$eq": "Caterpie"
        }
      },
      "nReturned": 1,
      "executionTimeMillisEstimate": 0,
      "works": 612,
      "advanced": 1,
      "needTime": 610,
      "needYield": 0,
      "saveState": 4,
      "restoreState": 4,
      "isEOF": 1,
      "invalidates": 0,
      "direction": "forward",
      "docsExamined": 610
    }
  },
  "serverInfo": {
    "host": "blsrocks",
    "port": 27017,
    "version": "3.2.9",
    "gitVersion": "22ec9e93b40c85fc7cae7d56e7d6a02fd811088c"
  },
  "ok": 1
}

```

## 2. Criar um index um para o campo name.
```js
blsrocks(mongod-3.2.9) be-mean> db.pokemons.createIndex({ name: 1 })
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}
```

## 3. Refazer a query para o campo name utilizando explain para ver o resultado da busca.
```js
blsrocks(mongod-3.2.9) be-mean> db.pokemons.find({"name": "Caterpie"}).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "name": {
        "$eq": "Caterpie"
      }
    },
    "winningPlan": {
      "stage": "FETCH",
      "inputStage": {
        "stage": "IXSCAN",
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
            "[\"Caterpie\", \"Caterpie\"]"
          ]
        }
      }
    },
    "rejectedPlans": [ ]
  },
  "executionStats": {
    "executionSuccess": true,
    "nReturned": 1,
    "executionTimeMillis": 1,
    "totalKeysExamined": 1,
    "totalDocsExamined": 1,
    "executionStages": {
      "stage": "FETCH",
      "nReturned": 1,
      "executionTimeMillisEstimate": 0,
      "works": 2,
      "advanced": 1,
      "needTime": 0,
      "needYield": 0,
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
            "[\"Caterpie\", \"Caterpie\"]"
          ]
        },
        "keysExamined": 1,
        "dupsTested": 0,
        "dupsDropped": 0,
        "seenInvalidated": 0
      }
    }
  },
  "serverInfo": {
    "host": "blsrocks",
    "port": 27017,
    "version": "3.2.9",
    "gitVersion": "22ec9e93b40c85fc7cae7d56e7d6a02fd811088c"
  },
  "ok": 1
}
```

## 4. Fazer uma query para dois campos juntos utilizando explain para ver o resultado da busca.
```js
blsrocks(mongod-3.2.9) be-mean> var query = {defense: 40, height: 6}
blsrocks(mongod-3.2.9) be-mean> query
{
  "defense": 40,
  "height": 6
}
blsrocks(mongod-3.2.9) be-mean> db.pokemons.find(query).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "defense": {
            "$eq": 40
          }
        },
        {
          "height": {
            "$eq": "6"
          }
        }
      ]
    },
    "winningPlan": {
      "stage": "COLLSCAN",
      "filter": {
        "$and": [
          {
            "defense": {
              "$eq": 40
            }
          },
          {
            "height": {
              "$eq": "6"
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
    "nReturned": 5,
    "executionTimeMillis": 1,
    "totalKeysExamined": 0,
    "totalDocsExamined": 610,
    "executionStages": {
      "stage": "COLLSCAN",
      "filter": {
        "$and": [
          {
            "defense": {
              "$eq": 40
            }
          },
          {
            "height": {
              "$eq": "6"
            }
          }
        ]
      },
      "nReturned": 5,
      "executionTimeMillisEstimate": 10,
      "works": 612,
      "advanced": 5,
      "needTime": 606,
      "needYield": 0,
      "saveState": 4,
      "restoreState": 4,
      "isEOF": 1,
      "invalidates": 0,
      "direction": "forward",
      "docsExamined": 610
    }
  },
  "serverInfo": {
    "host": "blsrocks",
    "port": 27017,
    "version": "3.2.9",
    "gitVersion": "22ec9e93b40c85fc7cae7d56e7d6a02fd811088c"
  },
  "ok": 1
}
```

## 5. Criar um index para esses dois campos juntos.
```js
blsrocks(mongod-3.2.9) be-mean> db.pokemons.createIndex({ defense: 48, height: 6 })
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}

```
\"6\"

## 6. Refazer a query para os dois campos juntos utilizando explain para ver o resultado da busca.
```js
blsrocks(mongod-3.2.9) be-mean> var query = {defense: 40, height: 6}
blsrocks(mongod-3.2.9) be-mean> query
{
  "defense": 40,
  "height": 6
}
blsrocks(mongod-3.2.9) be-mean> db.pokemons.find(query).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "defense": {
            "$eq": 40
          }
        },
        {
          "height": {
            "$eq": 6
          }
        }
      ]
    },
    "winningPlan": {
      "stage": "FETCH",
      "inputStage": {
        "stage": "IXSCAN",
        "keyPattern": {
          "defense": 48,
          "height": 6
        },
        "indexName": "defense_48_height_6",
        "isMultiKey": false,
        "isUnique": false,
        "isSparse": false,
        "isPartial": false,
        "indexVersion": 1,
        "direction": "forward",
        "indexBounds": {
          "defense": [
            "[40.0, 40.0]"
          ],
          "height": [
            "[6.0, 6.0]"
          ]
        }
      }
    },
    "rejectedPlans": [ ]
  },
  "executionStats": {
    "executionSuccess": true,
    "nReturned": 0,
    "executionTimeMillis": 1,
    "totalKeysExamined": 0,
    "totalDocsExamined": 0,
    "executionStages": {
      "stage": "FETCH",
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
          "defense": 48,
          "height": 6
        },
        "indexName": "defense_48_height_6",
        "isMultiKey": false,
        "isUnique": false,
        "isSparse": false,
        "isPartial": false,
        "indexVersion": 1,
        "direction": "forward",
        "indexBounds": {
          "defense": [
            "[40.0, 40.0]"
          ],
          "height": [
            "[6.0, 6.0]"
          ]
        },
        "keysExamined": 0,
        "dupsTested": 0,
        "dupsDropped": 0,
        "seenInvalidated": 0
      }
    }
  },
  "serverInfo": {
    "host": "blsrocks",
    "port": 27017,
    "version": "3.2.9",
    "gitVersion": "22ec9e93b40c85fc7cae7d56e7d6a02fd811088c"
  },
  "ok": 1
}
```