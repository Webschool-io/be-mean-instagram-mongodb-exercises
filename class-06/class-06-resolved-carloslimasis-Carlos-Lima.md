## 1. Fazer uma query para o campo name utilizando explain para ver o resultado da busca
```
MacBook-de-Carlos(mongod-3.0.5) be-mean> var query = {name: "Pikachu"}
MacBook-de-Carlos(mongod-3.0.5) be-mean> query
{
  "name": "Pikachu"
}
MacBook-de-Carlos(mongod-3.0.5) be-mean> db.pokemons.find(query).explain("executionStats")
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "name": {
        "$eq": "Pikachu"
      }
    },
    "winningPlan": {
      "stage": "COLLSCAN",
      "filter": {
        "name": {
          "$eq": "Pikachu"
        }
      },
      "direction": "forward"
    },
    "rejectedPlans": [ ]
  },
  "executionStats": {
    "executionSuccess": true,
    "nReturned": 1,
    "executionTimeMillis": 4,
    "totalKeysExamined": 0,
    "totalDocsExamined": 610,
    "executionStages": {
      "stage": "COLLSCAN",
      "filter": {
        "name": {
          "$eq": "Pikachu"
        }
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
  },
  "serverInfo": {
    "host": "MacBook-de-Carlos.local",
    "port": 27017,
    "version": "3.0.5",
    "gitVersion": "nogitversion"
  },
  "ok": 1
}

```
#2. Criar um index um para o campo name
```
MacBook-de-Carlos(mongod-3.0.5) be-mean> db.pokemons.createIndex({name: -1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}
```

#3. Refazer a query para o campo name utilizando explain para ver o resultado da busca
```
MacBook-de-Carlos(mongod-3.0.5) be-mean> db.pokemons.find(query).explain("executionStats")
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "name": {
        "$eq": "Pikachu"
      }
    },
    "winningPlan": {
      "stage": "FETCH",
      "inputStage": {
        "stage": "IXSCAN",
        "keyPattern": {
          "name": -1
        },
        "indexName": "name_-1",
        "isMultiKey": false,
        "direction": "forward",
        "indexBounds": {
          "name": [
            "[\"Pikachu\", \"Pikachu\"]"
          ]
        }
      }
    },
    "rejectedPlans": [ ]
  },
  "executionStats": {
    "executionSuccess": true,
    "nReturned": 1,
    "executionTimeMillis": 0,
    "totalKeysExamined": 1,
    "totalDocsExamined": 1,
    "executionStages": {
      "stage": "FETCH",
      "nReturned": 1,
      "executionTimeMillisEstimate": 0,
      "works": 2,
      "advanced": 1,
      "needTime": 0,
      "needFetch": 0,
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
        "needFetch": 0,
        "saveState": 0,
        "restoreState": 0,
        "isEOF": 1,
        "invalidates": 0,
        "keyPattern": {
          "name": -1
        },
        "indexName": "name_-1",
        "isMultiKey": false,
        "direction": "forward",
        "indexBounds": {
          "name": [
            "[\"Pikachu\", \"Pikachu\"]"
          ]
        },
        "keysExamined": 1,
        "dupsTested": 0,
        "dupsDropped": 0,
        "seenInvalidated": 0,
        "matchTested": 0
      }
    }
  },
  "serverInfo": {
    "host": "MacBook-de-Carlos.local",
    "port": 27017,
    "version": "3.0.5",
    "gitVersion": "nogitversion"
  },
  "ok": 1
}
```
#4. Fazer uma query para dois campos juntos utilizando explain para ver o resultado da busca
```
MacBook-de-Carlos(mongod-3.0.5) be-mean> var query = {$and: [{attack: {$lte: 50}}, {defense: {$gte: 10}}]}
MacBook-de-Carlos(mongod-3.0.5) be-mean> query
{
  "$and": [
    {
      "attack": {
        "$lte": 50
      }
    },
    {
      "defense": {
        "$gte": 10
      }
    }
  ]
}
MacBook-de-Carlos(mongod-3.0.5) be-mean> db.pokemons.find(query).explain("executionStats")
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "attack": {
            "$lte": 50
          }
        },
        {
          "defense": {
            "$gte": 10
          }
        }
      ]
    },
    "winningPlan": {
      "stage": "COLLSCAN",
      "filter": {
        "$and": [
          {
            "attack": {
              "$lte": 50
            }
          },
          {
            "defense": {
              "$gte": 10
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
    "nReturned": 146,
    "executionTimeMillis": 138,
    "totalKeysExamined": 0,
    "totalDocsExamined": 610,
    "executionStages": {
      "stage": "COLLSCAN",
      "filter": {
        "$and": [
          {
            "attack": {
              "$lte": 50
            }
          },
          {
            "defense": {
              "$gte": 10
            }
          }
        ]
      },
      "nReturned": 146,
      "executionTimeMillisEstimate": 30,
      "works": 612,
      "advanced": 146,
      "needTime": 465,
      "needFetch": 0,
      "saveState": 5,
      "restoreState": 5,
      "isEOF": 1,
      "invalidates": 0,
      "direction": "forward",
      "docsExamined": 610
    }
  },
  "serverInfo": {
    "host": "MacBook-de-Carlos.local",
    "port": 27017,
    "version": "3.0.5",
    "gitVersion": "nogitversion"
  },
  "ok": 1
}
```
#5. Criar um index para esses dois campos juntos
```
MacBook-de-Carlos(mongod-3.0.5) be-mean> db.pokemons.createIndex({attack: 1, defense: 1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 2,
  "numIndexesAfter": 3,
  "ok": 1
}
```
#6. Refazer a query para os dois campos juntos utilizando explain para ver o resultado da busca
```
MacBook-de-Carlos(mongod-3.0.5) be-mean> db.pokemons.find(query).explain("executionStats")
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "attack": {
            "$lte": 50
          }
        },
        {
          "defense": {
            "$gte": 10
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
            "[-inf.0, 50.0]"
          ],
          "defense": [
            "[10.0, inf.0]"
          ]
        }
      }
    },
    "rejectedPlans": [ ]
  },
  "executionStats": {
    "executionSuccess": true,
    "nReturned": 146,
    "executionTimeMillis": 4,
    "totalKeysExamined": 147,
    "totalDocsExamined": 146,
    "executionStages": {
      "stage": "FETCH",
      "nReturned": 146,
      "executionTimeMillisEstimate": 0,
      "works": 148,
      "advanced": 146,
      "needTime": 1,
      "needFetch": 0,
      "saveState": 1,
      "restoreState": 1,
      "isEOF": 1,
      "invalidates": 0,
      "docsExamined": 146,
      "alreadyHasObj": 0,
      "inputStage": {
        "stage": "IXSCAN",
        "nReturned": 146,
        "executionTimeMillisEstimate": 0,
        "works": 148,
        "advanced": 146,
        "needTime": 1,
        "needFetch": 0,
        "saveState": 1,
        "restoreState": 1,
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
            "[-inf.0, 50.0]"
          ],
          "defense": [
            "[10.0, inf.0]"
          ]
        },
        "keysExamined": 147,
        "dupsTested": 0,
        "dupsDropped": 0,
        "seenInvalidated": 0,
        "matchTested": 0
      }
    }
  },
  "serverInfo": {
    "host": "MacBook-de-Carlos.local",
    "port": 27017,
    "version": "3.0.5",
    "gitVersion": "nogitversion"
  },
  "ok": 1
}
```

