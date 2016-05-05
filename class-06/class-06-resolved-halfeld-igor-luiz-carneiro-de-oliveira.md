# MongoDB - Aula 06 - Exercício
Autor: Igor luíz


## Fazer uma query para o campo `name` utilizando `explain` para ver o resultado 

```sh
localhost(mongod-3.0.8) be-mean> db.pokemons.find({ name: /pikachu/i }).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "name": /pikachu/i
    },
    "winningPlan": {
      "stage": "COLLSCAN",
      "filter": {
        "name": /pikachu/i
      },
      "direction": "forward"
    },
    "rejectedPlans": [ ]
  },
  "executionStats": {
    "executionSuccess": true,
    "nReturned": 1,
    "executionTimeMillis": 0,
    "totalKeysExamined": 0,
    "totalDocsExamined": 620,
    "executionStages": {
      "stage": "COLLSCAN",
      "filter": {
        "name": /pikachu/i
      },
      "nReturned": 1,
      "executionTimeMillisEstimate": 0,
      "works": 622,
      "advanced": 1,
      "needTime": 620,
      "needFetch": 0,
      "saveState": 4,
      "restoreState": 4,
      "isEOF": 1,
      "invalidates": 0,
      "direction": "forward",
      "docsExamined": 620
    }
  },
  "serverInfo": {
    "host": "localhost.localdomain",
    "port": 27017,
    "version": "3.0.8",
    "gitVersion": "83d8cc25e00e42856924d84e220fbe4a839e605d"
  },
  "ok": 1
}
```


## Criar um `index` um para o campo `name`

```sh
localhost(mongod-3.0.8) be-mean> db.pokemons.createIndex({ name: 1 })
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}
```



## Refazer a query para o campo `name` utilizando `explain` para ver o resultado após ter o `index`

```sh
localhost(mongod-3.0.8) be-mean> db.pokemons.find({ name: /pikachu/i }).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "name": /pikachu/i
    },
    "winningPlan": {
      "stage": "FETCH",
      "inputStage": {
        "stage": "IXSCAN",
        "filter": {
          "name": /pikachu/i
        },
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
        }
      }
    },
    "rejectedPlans": [ ]
  },
  "executionStats": {
    "executionSuccess": true,
    "nReturned": 1,
    "executionTimeMillis": 32,
    "totalKeysExamined": 620,
    "totalDocsExamined": 1,
    "executionStages": {
      "stage": "FETCH",
      "nReturned": 1,
      "executionTimeMillisEstimate": 0,
      "works": 621,
      "advanced": 1,
      "needTime": 619,
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
        "works": 620,
        "advanced": 1,
        "needTime": 619,
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
        "keysExamined": 620,
        "dupsTested": 0,
        "dupsDropped": 0,
        "seenInvalidated": 0,
        "matchTested": 1
      }
    }
  },
  "serverInfo": {
    "host": "localhost.localdomain",
    "port": 27017,
    "version": "3.0.8",
    "gitVersion": "83d8cc25e00e42856924d84e220fbe4a839e605d"
  },
  "ok": 1
}
```


## Fazer uma query para dois campos juntos utilizando explain para ver o resultado

```sh
localhost(mongod-3.0.8) be-mean> db.pokemons.find({ name: 1, created: 1 }).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "created": {
            "$eq": 1
          }
        },
        {
          "name": {
            "$eq": 1
          }
        }
      ]
    },
    "winningPlan": {
      "stage": "COLLSCAN",
      "filter": {
        "$and": [
          {
            "created": {
              "$eq": 1
            }
          },
          {
            "name": {
              "$eq": 1
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
    "nReturned": 0,
    "executionTimeMillis": 0,
    "totalKeysExamined": 0,
    "totalDocsExamined": 620,
    "executionStages": {
      "stage": "COLLSCAN",
      "filter": {
        "$and": [
          {
            "created": {
              "$eq": 1
            }
          },
          {
            "name": {
              "$eq": 1
            }
          }
        ]
      },
      "nReturned": 0,
      "executionTimeMillisEstimate": 0,
      "works": 622,
      "advanced": 0,
      "needTime": 621,
      "needFetch": 0,
      "saveState": 4,
      "restoreState": 4,
      "isEOF": 1,
      "invalidates": 0,
      "direction": "forward",
      "docsExamined": 620
    }
  },
  "serverInfo": {
    "host": "localhost.localdomain",
    "port": 27017,
    "version": "3.0.8",
    "gitVersion": "83d8cc25e00e42856924d84e220fbe4a839e605d"
  },
  "ok": 1
}
```


## Criar um index `multiplo`

```sh
localhost(mongod-3.0.8) be-mean> db.pokemons.createIndex({ name: 1, created: 1 })
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}
```


## Refazer a query para os dois campos juntos utilizando explain para ver o resultado da busca

```sh
localhost(mongod-3.0.8) be-mean> db.pokemons.find({ name: 1, created: 1 }).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "created": {
            "$eq": 1
          }
        },
        {
          "name": {
            "$eq": 1
          }
        }
      ]
    },
    "winningPlan": {
      "stage": "FETCH",
      "inputStage": {
        "stage": "IXSCAN",
        "keyPattern": {
          "name": 1,
          "created": 1
        },
        "indexName": "name_1_created_1",
        "isMultiKey": false,
        "direction": "forward",
        "indexBounds": {
          "name": [
            "[1.0, 1.0]"
          ],
          "created": [
            "[1.0, 1.0]"
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
          "name": 1,
          "created": 1
        },
        "indexName": "name_1_created_1",
        "isMultiKey": false,
        "direction": "forward",
        "indexBounds": {
          "name": [
            "[1.0, 1.0]"
          ],
          "created": [
            "[1.0, 1.0]"
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
    "host": "localhost.localdomain",
    "port": 27017,
    "version": "3.0.8",
    "gitVersion": "83d8cc25e00e42856924d84e220fbe4a839e605d"
  },
  "ok": 1
}
```

