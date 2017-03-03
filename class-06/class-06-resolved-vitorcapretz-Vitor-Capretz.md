# MongoDB - Aula 05 - Exercício
*autor:* [Vítor Capretz](http://github.com/vitorcapretz)

## 1. Fazer uma query para o campo name utilizando `explain` para ver o resultado da busca
```
vitor-ThinkPad-T440(mongod-3.0.12) be-mean> var query = {name: "Delmonico Gourmet"}
vitor-ThinkPad-T440(mongod-3.0.12) be-mean> db.restaurantes.find(query).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.restaurantes",
    "indexFilterSet": false,
    "parsedQuery": {
      "name": {
        "$eq": "Delmonico Gourmet"
      }
    },
    "winningPlan": {
      "stage": "COLLSCAN",
      "filter": {
        "name": {
          "$eq": "Delmonico Gourmet"
        }
      },
      "direction": "forward"
    },
    "rejectedPlans": [ ]
  },
  "executionStats": {
    "executionSuccess": true,
    "nReturned": 2,
    "executionTimeMillis": 23,
    "totalKeysExamined": 0,
    "totalDocsExamined": 25359,
    "executionStages": {
      "stage": "COLLSCAN",
      "filter": {
        "name": {
          "$eq": "Delmonico Gourmet"
        }
      },
      "nReturned": 2,
      "executionTimeMillisEstimate": 30,
      "works": 25361,
      "advanced": 2,
      "needTime": 25358,
      "needFetch": 0,
      "saveState": 198,
      "restoreState": 198,
      "isEOF": 1,
      "invalidates": 0,
      "direction": "forward",
      "docsExamined": 25359
    }
  },
  "serverInfo": {
    "host": "vitor-ThinkPad-T440",
    "port": 27017,
    "version": "3.0.12",
    "gitVersion": "33934938e0e95d534cebbaff656cde916b9c3573"
  },
  "ok": 1
}
```

## 2. Criar um `index` um para o campo `name`
```
vitor-ThinkPad-T440(mongod-3.0.12) be-mean> db.restaurantes.createIndex({name: 1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}
```

## 3. Refazer a query para o campo `name` utilizando `explain` para ver o resultado da busca
```
vitor-ThinkPad-T440(mongod-3.0.12) be-mean> db.restaurantes.find(query).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.restaurantes",
    "indexFilterSet": false,
    "parsedQuery": {
      "name": {
        "$eq": "Delmonico Gourmet"
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
        "direction": "forward",
        "indexBounds": {
          "name": [
            "[\"Delmonico Gourmet\", \"Delmonico Gourmet\"]"
          ]
        }
      }
    },
    "rejectedPlans": [ ]
  },
  "executionStats": {
    "executionSuccess": true,
    "nReturned": 2,
    "executionTimeMillis": 0,
    "totalKeysExamined": 2,
    "totalDocsExamined": 2,
    "executionStages": {
      "stage": "FETCH",
      "nReturned": 2,
      "executionTimeMillisEstimate": 0,
      "works": 3,
      "advanced": 2,
      "needTime": 0,
      "needFetch": 0,
      "saveState": 0,
      "restoreState": 0,
      "isEOF": 1,
      "invalidates": 0,
      "docsExamined": 2,
      "alreadyHasObj": 0,
      "inputStage": {
        "stage": "IXSCAN",
        "nReturned": 2,
        "executionTimeMillisEstimate": 0,
        "works": 3,
        "advanced": 2,
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
            "[\"Delmonico Gourmet\", \"Delmonico Gourmet\"]"
          ]
        },
        "keysExamined": 2,
        "dupsTested": 0,
        "dupsDropped": 0,
        "seenInvalidated": 0,
        "matchTested": 0
      }
    }
  },
  "serverInfo": {
    "host": "vitor-ThinkPad-T440",
    "port": 27017,
    "version": "3.0.12",
    "gitVersion": "33934938e0e95d534cebbaff656cde916b9c3573"
  },
  "ok": 1
}
```

## 4. Fazer uma query para dois campos juntos utilizando `explain` para ver o resultado da busca
```
vitor-ThinkPad-T440(mongod-3.0.12) be-mean> var query = {"borough": "Manhattan",   "cuisine": "Delicatessen"}
vitor-ThinkPad-T440(mongod-3.0.12) be-mean> db.restaurantes.find(query).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.restaurantes",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "borough": {
            "$eq": "Manhattan"
          }
        },
        {
          "cuisine": {
            "$eq": "Delicatessen"
          }
        }
      ]
    },
    "winningPlan": {
      "stage": "COLLSCAN",
      "filter": {
        "$and": [
          {
            "borough": {
              "$eq": "Manhattan"
            }
          },
          {
            "cuisine": {
              "$eq": "Delicatessen"
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
    "nReturned": 133,
    "executionTimeMillis": 33,
    "totalKeysExamined": 0,
    "totalDocsExamined": 25359,
    "executionStages": {
      "stage": "COLLSCAN",
      "filter": {
        "$and": [
          {
            "borough": {
              "$eq": "Manhattan"
            }
          },
          {
            "cuisine": {
              "$eq": "Delicatessen"
            }
          }
        ]
      },
      "nReturned": 133,
      "executionTimeMillisEstimate": 30,
      "works": 25361,
      "advanced": 133,
      "needTime": 25227,
      "needFetch": 0,
      "saveState": 198,
      "restoreState": 198,
      "isEOF": 1,
      "invalidates": 0,
      "direction": "forward",
      "docsExamined": 25359
    }
  },
  "serverInfo": {
    "host": "vitor-ThinkPad-T440",
    "port": 27017,
    "version": "3.0.12",
    "gitVersion": "33934938e0e95d534cebbaff656cde916b9c3573"
  },
  "ok": 1
}
```

## 5. Criar um `index` para esses dois campos juntos
```
vitor-ThinkPad-T440(mongod-3.0.12) be-mean> db.restaurantes.createIndex({borough: 1, cuisine: 1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 2,
  "numIndexesAfter": 3,
  "ok": 1
}
```

## 6. Refazer a query para os dois campos juntos utilizando `explain` para ver o resultado da busca

```
vitor-ThinkPad-T440(mongod-3.0.12) be-mean> db.restaurantes.find(query).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.restaurantes",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "borough": {
            "$eq": "Manhattan"
          }
        },
        {
          "cuisine": {
            "$eq": "Delicatessen"
          }
        }
      ]
    },
    "winningPlan": {
      "stage": "FETCH",
      "inputStage": {
        "stage": "IXSCAN",
        "keyPattern": {
          "borough": 1,
          "cuisine": 1
        },
        "indexName": "borough_1_cuisine_1",
        "isMultiKey": false,
        "direction": "forward",
        "indexBounds": {
          "borough": [
            "[\"Manhattan\", \"Manhattan\"]"
          ],
          "cuisine": [
            "[\"Delicatessen\", \"Delicatessen\"]"
          ]
        }
      }
    },
    "rejectedPlans": [ ]
  },
  "executionStats": {
    "executionSuccess": true,
    "nReturned": 133,
    "executionTimeMillis": 0,
    "totalKeysExamined": 133,
    "totalDocsExamined": 133,
    "executionStages": {
      "stage": "FETCH",
      "nReturned": 133,
      "executionTimeMillisEstimate": 0,
      "works": 134,
      "advanced": 133,
      "needTime": 0,
      "needFetch": 0,
      "saveState": 1,
      "restoreState": 1,
      "isEOF": 1,
      "invalidates": 0,
      "docsExamined": 133,
      "alreadyHasObj": 0,
      "inputStage": {
        "stage": "IXSCAN",
        "nReturned": 133,
        "executionTimeMillisEstimate": 0,
        "works": 134,
        "advanced": 133,
        "needTime": 0,
        "needFetch": 0,
        "saveState": 1,
        "restoreState": 1,
        "isEOF": 1,
        "invalidates": 0,
        "keyPattern": {
          "borough": 1,
          "cuisine": 1
        },
        "indexName": "borough_1_cuisine_1",
        "isMultiKey": false,
        "direction": "forward",
        "indexBounds": {
          "borough": [
            "[\"Manhattan\", \"Manhattan\"]"
          ],
          "cuisine": [
            "[\"Delicatessen\", \"Delicatessen\"]"
          ]
        },
        "keysExamined": 133,
        "dupsTested": 0,
        "dupsDropped": 0,
        "seenInvalidated": 0,
        "matchTested": 0
      }
    }
  },
  "serverInfo": {
    "host": "vitor-ThinkPad-T440",
    "port": 27017,
    "version": "3.0.12",
    "gitVersion": "33934938e0e95d534cebbaff656cde916b9c3573"
  },
  "ok": 1
}
```
