# MongoDB - Aula 06 - Exercício
Autor: Juliano Padilha

## Fazer uma query para o campo 'name' utilizando 'explain' para ver o resultado da busca
```
be-mean> db.restaurantes.find({name: "La Fogata"}).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.restaurantes",
    "indexFilterSet": false,
    "parsedQuery": {
      "name": {
        "$eq": "La Fogata"
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
            "[\"La Fogata\", \"La Fogata\"]"
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
      "needYield": 0,
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
            "[\"La Fogata\", \"La Fogata\"]"
          ]
        },
        "keysExamined": 2,
        "dupsTested": 0,
        "dupsDropped": 0,
        "seenInvalidated": 0
      }
    }
  },
  "serverInfo": {
    "host": "Julianos-MacBook-Pro.local",
    "port": 27017,
    "version": "3.2.7",
    "gitVersion": "4249c1d2b5999ebbf1fdf3bc0e0e3b3ff5c0aaf2"
  },
  "ok": 1
}
```

## Criar um index um para o campo name
```
be-mean> db.restaurantes.createIndex({name: 1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}

be-mean> db.restaurantes.getIndexes()
[
  {
    "v": 1,
    "key": {
      "_id": 1
    },
    "name": "_id_",
    "ns": "be-mean.restaurantes"
  },
  {
    "v": 1,
    "key": {
      "name": 1
    },
    "name": "name_1",
    "ns": "be-mean.restaurantes"
  }
]
```

## Refazer a query para o campo 'name' utilizando explain para ver o resultado da busca
```
be-mean> db.restaurantes.find({name: "La Fogata"}).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.restaurantes",
    "indexFilterSet": false,
    "parsedQuery": {
      "name": {
        "$eq": "La Fogata"
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
            "[\"La Fogata\", \"La Fogata\"]"
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
      "needYield": 0,
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
            "[\"La Fogata\", \"La Fogata\"]"
          ]
        },
        "keysExamined": 2,
        "dupsTested": 0,
        "dupsDropped": 0,
        "seenInvalidated": 0
      }
    }
  },
  "serverInfo": {
    "host": "Julianos-MacBook-Pro.local",
    "port": 27017,
    "version": "3.2.7",
    "gitVersion": "4249c1d2b5999ebbf1fdf3bc0e0e3b3ff5c0aaf2"
  },
  "ok": 1
}
```

## Fazer uma query para dois campos juntos utilizando explain para ver o resultado da busca
```
db.restaurantes.find({$and:[{cuisine: "Spanish"}, {borough: "Brooklyn"}]}).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.restaurantes",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "borough": {
            "$eq": "Brooklyn"
          }
        },
        {
          "cuisine": {
            "$eq": "Spanish"
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
              "$eq": "Brooklyn"
            }
          },
          {
            "cuisine": {
              "$eq": "Spanish"
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
    "nReturned": 138,
    "executionTimeMillis": 18,
    "totalKeysExamined": 0,
    "totalDocsExamined": 25359,
    "executionStages": {
      "stage": "COLLSCAN",
      "filter": {
        "$and": [
          {
            "borough": {
              "$eq": "Brooklyn"
            }
          },
          {
            "cuisine": {
              "$eq": "Spanish"
            }
          }
        ]
      },
      "nReturned": 138,
      "executionTimeMillisEstimate": 10,
      "works": 25361,
      "advanced": 138,
      "needTime": 25222,
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
    "host": "Julianos-MacBook-Pro.local",
    "port": 27017,
    "version": "3.2.7",
    "gitVersion": "4249c1d2b5999ebbf1fdf3bc0e0e3b3ff5c0aaf2"
  },
  "ok": 1
}
```

## Criar um index para esses dois campos juntos
```
be-mean> db.restaurantes.createIndex({cuisine: 1}, {borough: 1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 2,
  "numIndexesAfter": 3,
  "ok": 1
}

be-mean> db.restaurantes.getIndexes()
[
  {
    "v": 1,
    "key": {
      "_id": 1
    },
    "name": "_id_",
    "ns": "be-mean.restaurantes"
  },
  {
    "v": 1,
    "key": {
      "name": 1
    },
    "name": "name_1",
    "ns": "be-mean.restaurantes"
  },
  {
    "v": 1,
    "key": {
      "cuisine": 1
    },
    "name": "cuisine_1",
    "ns": "be-mean.restaurantes",
    "borough": 1
  }
]

## Refazer a query para os dois campos juntos utilizando o explain para ver o resultado da busca.
```
db.restaurantes.find({$and:[{cuisine: "Spanish"}, {borough: "Brooklyn"}]}).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.restaurantes",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "borough": {
            "$eq": "Brooklyn"
          }
        },
        {
          "cuisine": {
            "$eq": "Spanish"
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
          "cuisine": 1
        },
        "indexName": "cuisine_1",
        "isMultiKey": false,
        "isUnique": false,
        "isSparse": false,
        "isPartial": false,
        "indexVersion": 1,
        "direction": "forward",
        "indexBounds": {
          "cuisine": [
            "[\"Spanish\", \"Spanish\"]"
          ]
        }
      }
    },
    "rejectedPlans": [ ]
  },
  "executionStats": {
    "executionSuccess": true,
    "nReturned": 138,
    "executionTimeMillis": 62,
    "totalKeysExamined": 637,
    "totalDocsExamined": 637,
    "executionStages": {
      "stage": "FETCH",
      "filter": {
        "borough": {
          "$eq": "Brooklyn"
        }
      },
      "nReturned": 138,
      "executionTimeMillisEstimate": 30,
      "works": 638,
      "advanced": 138,
      "needTime": 499,
      "needYield": 0,
      "saveState": 5,
      "restoreState": 5,
      "isEOF": 1,
      "invalidates": 0,
      "docsExamined": 637,
      "alreadyHasObj": 0,
      "inputStage": {
        "stage": "IXSCAN",
        "nReturned": 637,
        "executionTimeMillisEstimate": 20,
        "works": 638,
        "advanced": 637,
        "needTime": 0,
        "needYield": 0,
        "saveState": 5,
        "restoreState": 5,
        "isEOF": 1,
        "invalidates": 0,
        "keyPattern": {
          "cuisine": 1
        },
        "indexName": "cuisine_1",
        "isMultiKey": false,
        "isUnique": false,
        "isSparse": false,
        "isPartial": false,
        "indexVersion": 1,
        "direction": "forward",
        "indexBounds": {
          "cuisine": [
            "[\"Spanish\", \"Spanish\"]"
          ]
        },
        "keysExamined": 637,
        "dupsTested": 0,
        "dupsDropped": 0,
        "seenInvalidated": 0
      }
    }
  },
  "serverInfo": {
    "host": "Julianos-MacBook-Pro.local",
    "port": 27017,
    "version": "3.2.7",
    "gitVersion": "4249c1d2b5999ebbf1fdf3bc0e0e3b3ff5c0aaf2"
  },
  "ok": 1
}
```