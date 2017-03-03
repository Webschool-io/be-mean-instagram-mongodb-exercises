# MongoDB - Aula 06 - Exercício
autor: Fernando Lucas

# 1. Fazer uma query para o campo name utilizando explain para ver o resultado da busca
```
fernando(mongod-3.2.6) be-mean-pokemons> var query = {name: /luladrao/i}
fernando(mongod-3.2.6) be-mean-pokemons> db.pokemons.find(query).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean-pokemons.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "name": /luladrao/i
    },
    "winningPlan": {
      "stage": "FETCH",
      "inputStage": {
        "stage": "IXSCAN",
        "filter": {
          "name": /luladrao/i
        },
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
            "[\"\", {})",
            "[/luladrao/i, /luladrao/i]"
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
    "totalKeysExamined": 12,
    "totalDocsExamined": 1,
    "executionStages": {
      "stage": "FETCH",
      "nReturned": 1,
      "executionTimeMillisEstimate": 0,
      "works": 13,
      "advanced": 1,
      "needTime": 11,
      "needYield": 0,
      "saveState": 0,
      "restoreState": 0,
      "isEOF": 1,
      "invalidates": 0,
      "docsExamined": 1,
      "alreadyHasObj": 0,
      "inputStage": {
        "stage": "IXSCAN",
        "filter": {
          "name": /luladrao/i
        },
        "nReturned": 1,
        "executionTimeMillisEstimate": 0,
        "works": 13,
        "advanced": 1,
        "needTime": 11,
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
            "[\"\", {})",
            "[/luladrao/i, /luladrao/i]"
          ]
        },
        "keysExamined": 12,
        "dupsTested": 0,
        "dupsDropped": 0,
        "seenInvalidated": 0
      }
    }
  },
  "serverInfo": {
    "host": "fernando",
    "port": 27017,
    "version": "3.2.6",
    "gitVersion": "05552b562c7a0b3143a729aaa0838e558dc49b25"
  },
  "ok": 1
}

```

# 2. Criar um index um para o campo name
```
fernando(mongod-3.2.6) be-mean-pokemons> var index = {name: 1}
fernando(mongod-3.2.6) be-mean-pokemons> db.pokemons.createIndex(index)
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}

```

# 3. Refazer a query para o campo name utilizando explain para ver o resultado da busca
```
fernando(mongod-3.2.6) be-mean-pokemons> var query = {name: /luladrao/i}
fernando(mongod-3.2.6) be-mean-pokemons> db.pokemons.find(query).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean-pokemons.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "name": /luladrao/i
    },
    "winningPlan": {
      "stage": "FETCH",
      "inputStage": {
        "stage": "IXSCAN",
        "filter": {
          "name": /luladrao/i
        },
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
            "[\"\", {})",
            "[/luladrao/i, /luladrao/i]"
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
    "totalKeysExamined": 12,
    "totalDocsExamined": 1,
    "executionStages": {
      "stage": "FETCH",
      "nReturned": 1,
      "executionTimeMillisEstimate": 0,
      "works": 13,
      "advanced": 1,
      "needTime": 11,
      "needYield": 0,
      "saveState": 0,
      "restoreState": 0,
      "isEOF": 1,
      "invalidates": 0,
      "docsExamined": 1,
      "alreadyHasObj": 0,
      "inputStage": {
        "stage": "IXSCAN",
        "filter": {
          "name": /luladrao/i
        },
        "nReturned": 1,
        "executionTimeMillisEstimate": 0,
        "works": 13,
        "advanced": 1,
        "needTime": 11,
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
            "[\"\", {})",
            "[/luladrao/i, /luladrao/i]"
          ]
        },
        "keysExamined": 12,
        "dupsTested": 0,
        "dupsDropped": 0,
        "seenInvalidated": 0
      }
    }
  },
  "serverInfo": {
    "host": "fernando",
    "port": 27017,
    "version": "3.2.6",
    "gitVersion": "05552b562c7a0b3143a729aaa0838e558dc49b25"
  },
  "ok": 1
}

```

# 4. Fazer uma query para dois campos juntos utilizando explain para ver o resultado da busca
```
fernando(mongod-3.2.6) be-mean-pokemons> var query = { $or: [{name: /luladra/i}, {attack: {$lte: 50}}]}
fernando(mongod-3.2.6) be-mean-pokemons> db.pokemons.find(query).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean-pokemons.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "$or": [
        {
          "attack": {
            "$lte": 50
          }
        },
        {
          "name": /luladra/i
        }
      ]
    },
    "winningPlan": {
      "stage": "SUBPLAN",
      "inputStage": {
        "stage": "COLLSCAN",
        "filter": {
          "$or": [
            {
              "attack": {
                "$lte": 50
              }
            },
            {
              "name": /luladra/i
            }
          ]
        },
        "direction": "forward"
      }
    },
    "rejectedPlans": [ ]
  },
  "executionStats": {
    "executionSuccess": true,
    "nReturned": 4,
    "executionTimeMillis": 0,
    "totalKeysExamined": 0,
    "totalDocsExamined": 13,
    "executionStages": {
      "stage": "SUBPLAN",
      "nReturned": 4,
      "executionTimeMillisEstimate": 0,
      "works": 15,
      "advanced": 4,
      "needTime": 10,
      "needYield": 0,
      "saveState": 0,
      "restoreState": 0,
      "isEOF": 1,
      "invalidates": 0,
      "inputStage": {
        "stage": "COLLSCAN",
        "filter": {
          "$or": [
            {
              "attack": {
                "$lte": 50
              }
            },
            {
              "name": /luladra/i
            }
          ]
        },
        "nReturned": 4,
        "executionTimeMillisEstimate": 0,
        "works": 15,
        "advanced": 4,
        "needTime": 10,
        "needYield": 0,
        "saveState": 0,
        "restoreState": 0,
        "isEOF": 1,
        "invalidates": 0,
        "direction": "forward",
        "docsExamined": 13
      }
    }
  },
  "serverInfo": {
    "host": "fernando",
    "port": 27017,
    "version": "3.2.6",
    "gitVersion": "05552b562c7a0b3143a729aaa0838e558dc49b25"
  },
  "ok": 1
}

```

# 5. Criar um index para esses dois campos juntos
```
fernando(mongod-3.2.6) be-mean-pokemons> var index = {name: 1, attack: 1}
fernando(mongod-3.2.6) be-mean-pokemons> db.pokemons.createIndex(index)
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 2,
  "numIndexesAfter": 3,
  "ok": 1
}

```

# 6. Refazer a query para os dois campos juntos utilizando explain para ver o resultado da busca
```
fernando(mongod-3.2.6) be-mean-pokemons> var query = { $or: [{name: /charmander/i }, {attack: { $lte: 50 }}]}
fernando(mongod-3.2.6) be-mean-pokemons> db.pokemons.find(query).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean-pokemons.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "$or": [
        {
          "attack": {
            "$lte": 50
          }
        },
        {
          "name": /charmander/i
        }
      ]
    },
    "winningPlan": {
      "stage": "SUBPLAN",
      "inputStage": {
        "stage": "COLLSCAN",
        "filter": {
          "$or": [
            {
              "attack": {
                "$lte": 50
              }
            },
            {
              "name": /charmander/i
            }
          ]
        },
        "direction": "forward"
      }
    },
    "rejectedPlans": [ ]
  },
  "executionStats": {
    "executionSuccess": true,
    "nReturned": 4,
    "executionTimeMillis": 0,
    "totalKeysExamined": 0,
    "totalDocsExamined": 13,
    "executionStages": {
      "stage": "SUBPLAN",
      "nReturned": 4,
      "executionTimeMillisEstimate": 0,
      "works": 15,
      "advanced": 4,
      "needTime": 10,
      "needYield": 0,
      "saveState": 0,
      "restoreState": 0,
      "isEOF": 1,
      "invalidates": 0,
      "inputStage": {
        "stage": "COLLSCAN",
        "filter": {
          "$or": [
            {
              "attack": {
                "$lte": 50
              }
            },
            {
              "name": /charmander/i
            }
          ]
        },
        "nReturned": 4,
        "executionTimeMillisEstimate": 0,
        "works": 15,
        "advanced": 4,
        "needTime": 10,
        "needYield": 0,
        "saveState": 0,
        "restoreState": 0,
        "isEOF": 1,
        "invalidates": 0,
        "direction": "forward",
        "docsExamined": 13
      }
    }
  },
  "serverInfo": {
    "host": "fernando",
    "port": 27017,
    "version": "3.2.6",
    "gitVersion": "05552b562c7a0b3143a729aaa0838e558dc49b25"
  },
  "ok": 1
}


```