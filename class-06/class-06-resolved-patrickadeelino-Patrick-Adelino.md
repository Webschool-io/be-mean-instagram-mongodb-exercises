## MongoDb Aula - 06

Autor: Patrick Adelino

## 1. Fazer uma query por nome sem "indexização" utilizando o explain
```
db.restaurantes.find({"name" : "Indian Oven",}).explain("executionStats")
pontocom-Aspire-4252(mongod-3.2.7) be-mean> db.restaurantes.find({"name" : "Indian Oven",}).explain("executionStats")
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.restaurantes",
    "indexFilterSet": false,
    "parsedQuery": {
      "name": {
        "$eq": "Indian Oven"
      }
    },
    "winningPlan": {
      "stage": "COLLSCAN",
      "filter": {
        "name": {
          "$eq": "Indian Oven"
        }
      },
      "direction": "forward"
    },
    "rejectedPlans": [ ]
  },
  "executionStats": {
    "executionSuccess": true,
    "nReturned": 1,
    "executionTimeMillis": 74,
    "totalKeysExamined": 0,
    "totalDocsExamined": 25359,
    "executionStages": {
      "stage": "COLLSCAN",
      "filter": {
        "name": {
          "$eq": "Indian Oven"
        }
      },
      "nReturned": 1,
      "executionTimeMillisEstimate": 40,
      "works": 25361,
      "advanced": 1,
      "needTime": 25359,
      "needYield": 0,
      "saveState": 199,
      "restoreState": 199,
      "isEOF": 1,
      "invalidates": 0,
      "direction": "forward",
      "docsExamined": 25359
    }
  },
  "serverInfo": {
    "host": "pontocom-Aspire-4252",
    "port": 27017,
    "version": "3.2.7",
    "gitVersion": "4249c1d2b5999ebbf1fdf3bc0e0e3b3ff5c0aaf2"
  },
  "ok": 1
}
```
## 2. Criar um Index pelo nome
```
 db.restaurantes.createIndex({name:1})
{
    "createdCollectionAutomatically" : false,
    "numIndexesBefore" : 1,
    "numIndexesAfter" : 2,
    "ok" : 1
}
```

## 3.Refazer a query para o campo name utilizando explain para ver o resultado da busca
pontocom-Aspire-4252(mongod-3.2.7) be-mean> db.restaurantes.find({"name" : "Indian Oven",}).explain("executionStats")
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.restaurantes",
    "indexFilterSet": false,
    "parsedQuery": {
      "name": {
        "$eq": "Indian Oven"
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
            "[\"Indian Oven\", \"Indian Oven\"]"
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
            "[\"Indian Oven\", \"Indian Oven\"]"
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
    "host": "pontocom-Aspire-4252",
    "port": 27017,
    "version": "3.2.7",
    "gitVersion": "4249c1d2b5999ebbf1fdf3bc0e0e3b3ff5c0aaf2"
  },
  "ok": 1
}
```
## 4. Fazer uma query de dois campos juntos sem "indexização" utilizando o explain
```
pontocom-Aspire-4252(mongod-3.2.7) be-mean> db.restaurantes.find({"borough" : "Bronx",cuisine:"Bakery"}).explain("executionStats")
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.restaurantes",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "borough": {
            "$eq": "Bronx"
          }
        },
        {
          "cuisine": {
            "$eq": "Bakery"
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
              "$eq": "Bronx"
            }
          },
          {
            "cuisine": {
              "$eq": "Bakery"
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
    "nReturned": 71,
    "executionTimeMillis": 56,
    "totalKeysExamined": 0,
    "totalDocsExamined": 25359,
    "executionStages": {
      "stage": "COLLSCAN",
      "filter": {
        "$and": [
          {
            "borough": {
              "$eq": "Bronx"
            }
          },
          {
            "cuisine": {
              "$eq": "Bakery"
            }
          }
        ]
      },
      "nReturned": 71,
      "executionTimeMillisEstimate": 50,
      "works": 25361,
      "advanced": 71,
      "needTime": 25289,
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
    "host": "pontocom-Aspire-4252",
    "port": 27017,
    "version": "3.2.7",
    "gitVersion": "4249c1d2b5999ebbf1fdf3bc0e0e3b3ff5c0aaf2"
  },
  "ok": 1
}
```
## 5. Criar um index para esses dois campos juntos

```
db.restaurantes.createIndex({borough:1,cuisine:1})
{
        "createdCollectionAutomatically" : false,
        "numIndexesBefore" : 2,
        "numIndexesAfter" : 3,
        "ok" : 1
}
```

## 6. Refazer a query para os dois campos juntos utilizando explain para ver o resultado da busca

```
pontocom-Aspire-4252(mongod-3.2.7) be-mean> db.restaurantes.find({"borough" : "Bronx",cuisine:"Bakery"}).explain("executionStats")
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.restaurantes",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "borough": {
            "$eq": "Bronx"
          }
        },
        {
          "cuisine": {
            "$eq": "Bakery"
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
        "isUnique": false,
        "isSparse": false,
        "isPartial": false,
        "indexVersion": 1,
        "direction": "forward",
        "indexBounds": {
          "borough": [
            "[\"Bronx\", \"Bronx\"]"
          ],
          "cuisine": [
            "[\"Bakery\", \"Bakery\"]"
          ]
        }
      }
    },
    "rejectedPlans": [ ]
  },
  "executionStats": {
    "executionSuccess": true,
    "nReturned": 71,
    "executionTimeMillis": 2,
    "totalKeysExamined": 71,
    "totalDocsExamined": 71,
    "executionStages": {
      "stage": "FETCH",
      "nReturned": 71,
      "executionTimeMillisEstimate": 0,
      "works": 72,
      "advanced": 71,
      "needTime": 0,
      "needYield": 0,
      "saveState": 0,
      "restoreState": 0,
      "isEOF": 1,
      "invalidates": 0,
      "docsExamined": 71,
      "alreadyHasObj": 0,
      "inputStage": {
        "stage": "IXSCAN",
        "nReturned": 71,
        "executionTimeMillisEstimate": 0,
        "works": 72,
        "advanced": 71,
        "needTime": 0,
        "needYield": 0,
        "saveState": 0,
        "restoreState": 0,
        "isEOF": 1,
        "invalidates": 0,
        "keyPattern": {
          "borough": 1,
          "cuisine": 1
        },
        "indexName": "borough_1_cuisine_1",
        "isMultiKey": false,
        "isUnique": false,
        "isSparse": false,
        "isPartial": false,
        "indexVersion": 1,
        "direction": "forward",
        "indexBounds": {
          "borough": [
            "[\"Bronx\", \"Bronx\"]"
          ],
          "cuisine": [
            "[\"Bakery\", \"Bakery\"]"
          ]
        },
        "keysExamined": 71,
        "dupsTested": 0,
        "dupsDropped": 0,
        "seenInvalidated": 0
      }
    }
  },
  "serverInfo": {
    "host": "pontocom-Aspire-4252",
    "port": 27017,
    "version": "3.2.7",
    "gitVersion": "4249c1d2b5999ebbf1fdf3bc0e0e3b3ff5c0aaf2"
  },
  "ok": 1
}

```
