# MongoDB - Aula 06 - Exercício
autor: Matheus Torres Pereira

## 1. Fazer uma query para o campo name utilizando explain para ver o resultado da busca.

```
ubuntu(mongod-3.2.12) be-mean> db.restaurantes.find({name: 'Riviera Caterer'}).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.restaurantes",
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
    "executionTimeMillis": 24,
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
      "executionTimeMillisEstimate": 30,
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
    "host": "ubuntu",
    "port": 27017,
    "version": "3.2.12",
    "gitVersion": "ef3e1bc78e997f0d9f22f45aeb1d8e3b6ac14a14"
  },
  "ok": 1
}
```

## 2. Criar um index um para o campo name.

```
ubuntu(mongod-3.2.12) be-mean> db.restaurantes.createIndex({name:1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}
```

## 3. Refazer a query para o campo name utilizando explain para ver o resultado da busca.

```
ubuntu(mongod-3.2.12) be-mean> db.restaurantes.find({name: 'Riviera Caterer'}).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.restaurantes",
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
    "executionTimeMillis": 6,
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
    "host": "ubuntu",
    "port": 27017,
    "version": "3.2.12",
    "gitVersion": "ef3e1bc78e997f0d9f22f45aeb1d8e3b6ac14a14"
  },
  "ok": 1
}
```

## 4. Fazer uma query para dois campos juntos utilizando explain para ver o resultado da busca.

```
ubuntu(mongod-3.2.12) be-mean> db.restaurantes.find({cuisine: 'Portuguese', borough: 'Manhattan'}).explain()
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
            "$eq": "Portuguese"
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
              "$eq": "Portuguese"
            }
          }
        ]
      },
      "direction": "forward"
    },
    "rejectedPlans": [ ]
  },
  "serverInfo": {
    "host": "ubuntu",
    "port": 27017,
    "version": "3.2.12",
    "gitVersion": "ef3e1bc78e997f0d9f22f45aeb1d8e3b6ac14a14"
  },
  "ok": 1
}
```

## 5. Criar um index para esses dois campos juntos.

```
ubuntu(mongod-3.2.12) be-mean> db.restaurantes.createIndex({cuisine:1, borough:1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 2,
  "numIndexesAfter": 3,
  "ok": 1
}
```

## 6. Refazer a query para os dois campos juntos utilizando explain para ver o resultado da busca.

```
ubuntu(mongod-3.2.12) be-mean> db.restaurantes.find({cuisine: 'Portuguese', borough: 'Manhattan'}).explain()
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
            "$eq": "Portuguese"
          }
        }
      ]
    },
    "winningPlan": {
      "stage": "FETCH",
      "inputStage": {
        "stage": "IXSCAN",
        "keyPattern": {
          "cuisine": 1,
          "borough": 1
        },
        "indexName": "cuisine_1_borough_1",
        "isMultiKey": false,
        "isUnique": false,
        "isSparse": false,
        "isPartial": false,
        "indexVersion": 1,
        "direction": "forward",
        "indexBounds": {
          "cuisine": [
            "[\"Portuguese\", \"Portuguese\"]"
          ],
          "borough": [
            "[\"Manhattan\", \"Manhattan\"]"
          ]
        }
      }
    },
    "rejectedPlans": [ ]
  },
  "serverInfo": {
    "host": "ubuntu",
    "port": 27017,
    "version": "3.2.12",
    "gitVersion": "ef3e1bc78e997f0d9f22f45aeb1d8e3b6ac14a14"
  },
  "ok": 1
}
```

