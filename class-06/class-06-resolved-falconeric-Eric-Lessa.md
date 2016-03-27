# MongoDB - Aula 06 - Exercício
User: [falconeric](https://github.com/falconeric)
Autor: Eric Lessa

# Fazer uma query para o campo name utilizando `explain` para ver o resultado da busca.
```
elcarvalho(mongod-3.2.4) be-mean-instagram> db.restaurantes.find({"name": "Riviera Caterer"}).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean-instagram.restaurantes",
    "indexFilterSet": false,
    "parsedQuery": {
      "name": {
        "$eq": "Riviera Caterer"
      }
    },
    "winningPlan": {
      "stage": "COLLSCAN",
      "filter": {
        "name": {
          "$eq": "Riviera Caterer"
        }
      },
      "direction": "forward"
    },
    "rejectedPlans": [ ]
  },
  "executionStats": {
    "executionSuccess": true,
    "nReturned": 1,
    "executionTimeMillis": 20,
    "totalKeysExamined": 0,
    "totalDocsExamined": 25359,
    "executionStages": {
      "stage": "COLLSCAN",
      "filter": {
        "name": {
          "$eq": "Riviera Caterer"
        }
      },
      "nReturned": 1,
      "executionTimeMillisEstimate": 20,
      "works": 25361,
      "advanced": 1,
      "needTime": 25359,
      "needYield": 0,
      "saveState": 198,
      "restoreState": 198,
      "isEOF": 1,
      "invalidates": 0,
      "direction": "forward",
      "docsExamined": 25359
    }
  },
  "serverInfo": {
    "host": "elcarvalho.local",
    "port": 27017,
    "version": "3.2.4",
    "gitVersion": "e2ee9ffcf9f5a94fad76802e28cc978718bb7a30"
  },
  "ok": 1
}
```

# Criar um `index` um para o campo `name`.
```
elcarvalho(mongod-3.2.4) be-mean-instagram> db.restaurantes.createIndex({ name : 1 })
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}
```

# Refazer a query para o campo `name` utilizando `explain` para ver o resultado da busca.
```
elcarvalho(mongod-3.2.4) be-mean-instagram> db.restaurantes.find({"name": "Riviera Caterer"}).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean-instagram.restaurantes",
    "indexFilterSet": false,
    "parsedQuery": {
      "name": {
        "$eq": "Riviera Caterer"
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
            "[\"Riviera Caterer\", \"Riviera Caterer\"]"
          ]
        }
      }
    },
    "rejectedPlans": [ ]
  },
  "executionStats": {
    "executionSuccess": true,
    "nReturned": 1,
    "executionTimeMillis": 3,
    "totalKeysExamined": 1,
    "totalDocsExamined": 1,
    "executionStages": {
      "stage": "FETCH",
      "nReturned": 1,
      "executionTimeMillisEstimate": 10,
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
        "executionTimeMillisEstimate": 10,
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
            "[\"Riviera Caterer\", \"Riviera Caterer\"]"
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
    "host": "elcarvalho.local",
    "port": 27017,
    "version": "3.2.4",
    "gitVersion": "e2ee9ffcf9f5a94fad76802e28cc978718bb7a30"
  },
  "ok": 1
}
```

# Fazer uma query para dois campos juntos utilizando `explain` para ver o resultado da busca.
```
elcarvalho(mongod-3.2.4) be-mean-instagram> db.restaurantes.find({"name": "Riviera Caterer", "borough": "Brooklyn"}).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean-instagram.restaurantes",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "borough": {
            "$eq": "Brooklyn"
          }
        },
        {
          "name": {
            "$eq": "Riviera Caterer"
          }
        }
      ]
    },
    "winningPlan": {
      "stage": "FETCH",
      "filter": {
        "borough": {
          "$eq": "Brooklyn"
        }
      },
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
            "[\"Riviera Caterer\", \"Riviera Caterer\"]"
          ]
        }
      }
    },
    "rejectedPlans": [ ]
  },
  "executionStats": {
    "executionSuccess": true,
    "nReturned": 1,
    "executionTimeMillis": 3,
    "totalKeysExamined": 1,
    "totalDocsExamined": 1,
    "executionStages": {
      "stage": "FETCH",
      "filter": {
        "borough": {
          "$eq": "Brooklyn"
        }
      },
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
            "[\"Riviera Caterer\", \"Riviera Caterer\"]"
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
    "host": "elcarvalho.local",
    "port": 27017,
    "version": "3.2.4",
    "gitVersion": "e2ee9ffcf9f5a94fad76802e28cc978718bb7a30"
  },
  "ok": 1
}
```

# Criar um `index` para esses dois campos juntos.
```
elcarvalho(mongod-3.2.4) be-mean-instagram> db.restaurantes.createIndex({ name : 1, borough: 1 })
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 2,
  "numIndexesAfter": 3,
  "ok": 1
}
```

# Refazer a query para os dois campos juntos utilizando `explain` para ver o resultado da busca.
```
elcarvalho(mongod-3.2.4) be-mean-instagram> db.restaurantes.find({"name": "Riviera Caterer", "borough": "Brooklyn"}).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean-instagram.restaurantes",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "borough": {
            "$eq": "Brooklyn"
          }
        },
        {
          "name": {
            "$eq": "Riviera Caterer"
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
          "borough": 1
        },
        "indexName": "name_1_borough_1",
        "isMultiKey": false,
        "isUnique": false,
        "isSparse": false,
        "isPartial": false,
        "indexVersion": 1,
        "direction": "forward",
        "indexBounds": {
          "name": [
            "[\"Riviera Caterer\", \"Riviera Caterer\"]"
          ],
          "borough": [
            "[\"Brooklyn\", \"Brooklyn\"]"
          ]
        }
      }
    },
    "rejectedPlans": [
      {
        "stage": "FETCH",
        "filter": {
          "borough": {
            "$eq": "Brooklyn"
          }
        },
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
              "[\"Riviera Caterer\", \"Riviera Caterer\"]"
            ]
          }
        }
      }
    ]
  },
  "executionStats": {
    "executionSuccess": true,
    "nReturned": 1,
    "executionTimeMillis": 104,
    "totalKeysExamined": 1,
    "totalDocsExamined": 1,
    "executionStages": {
      "stage": "FETCH",
      "nReturned": 1,
      "executionTimeMillisEstimate": 0,
      "works": 3,
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
          "name": 1,
          "borough": 1
        },
        "indexName": "name_1_borough_1",
        "isMultiKey": false,
        "isUnique": false,
        "isSparse": false,
        "isPartial": false,
        "indexVersion": 1,
        "direction": "forward",
        "indexBounds": {
          "name": [
            "[\"Riviera Caterer\", \"Riviera Caterer\"]"
          ],
          "borough": [
            "[\"Brooklyn\", \"Brooklyn\"]"
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
    "host": "elcarvalho.local",
    "port": 27017,
    "version": "3.2.4",
    "gitVersion": "e2ee9ffcf9f5a94fad76802e28cc978718bb7a30"
  },
  "ok": 1
}
```
