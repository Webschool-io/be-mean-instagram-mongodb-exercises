# MongoDB - Aula 06 - Exercício
autor: Andrew Esteves

# 1. Fazer uma query para o campo name utilizando explain para ver o resultado da busca
```
db.pokemons.find({ name: /pikachu/i }).explain("executionStats")
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean-pokemons.pokemons",
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
    "executionTimeMillis": 11,
    "totalKeysExamined": 0,
    "totalDocsExamined": 10,
    "executionStages": {
      "stage": "COLLSCAN",
      "filter": {
        "name": /pikachu/i
      },
      "nReturned": 1,
      "executionTimeMillisEstimate": 0,
      "works": 12,
      "advanced": 1,
      "needTime": 10,
      "needFetch": 0,
      "saveState": 0,
      "restoreState": 0,
      "isEOF": 1,
      "invalidates": 0,
      "direction": "forward",
      "docsExamined": 10
    }
  },
  "serverInfo": {
    "host": "Air-de-Andrew",
    "port": 27017,
    "version": "3.0.4",
    "gitVersion": "nogitversion"
  },
  "ok": 1
}

```

# 2. Criar um index um para o campo name
```
db.pokemons.createIndex({ name: 1 })
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}

```

# 3. Refazer a query para o campo name utilizando explain para ver o resultado da busca
```
db.pokemons.find({ name: /pikachu/i }).explain("executionStats")
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean-pokemons.pokemons",
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
    "executionTimeMillis": 8,
    "totalKeysExamined": 10,
    "totalDocsExamined": 1,
    "executionStages": {
      "stage": "FETCH",
      "nReturned": 1,
      "executionTimeMillisEstimate": 0,
      "works": 11,
      "advanced": 1,
      "needTime": 9,
      "needFetch": 0,
      "saveState": 0,
      "restoreState": 0,
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
        "works": 10,
        "advanced": 1,
        "needTime": 9,
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
            "[\"\", {})",
            "[/pikachu/i, /pikachu/i]"
          ]
        },
        "keysExamined": 10,
        "dupsTested": 0,
        "dupsDropped": 0,
        "seenInvalidated": 0,
        "matchTested": 1
      }
    }
  },
  "serverInfo": {
    "host": "Air-de-Andrew",
    "port": 27017,
    "version": "3.0.4",
    "gitVersion": "nogitversion"
  },
  "ok": 1
}


```

# 4. Fazer uma query para dois campos juntos utilizando explain para ver o resultado da busca
```
db.pokemons.find({$and : [{defense: 50}, {attack: { $gte: 50}}]}).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean-pokemons.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "defense": {
            "$eq": 50
          }
        },
        {
          "attack": {
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
            "defense": {
              "$eq": 50
            }
          },
          {
            "attack": {
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
    "nReturned": 2,
    "executionTimeMillis": 1,
    "totalKeysExamined": 0,
    "totalDocsExamined": 10,
    "executionStages": {
      "stage": "COLLSCAN",
      "filter": {
        "$and": [
          {
            "defense": {
              "$eq": 50
            }
          },
          {
            "attack": {
              "$gte": 50
            }
          }
        ]
      },
      "nReturned": 2,
      "executionTimeMillisEstimate": 0,
      "works": 12,
      "advanced": 2,
      "needTime": 9,
      "needFetch": 0,
      "saveState": 0,
      "restoreState": 0,
      "isEOF": 1,
      "invalidates": 0,
      "direction": "forward",
      "docsExamined": 10
    }
  },
  "serverInfo": {
    "host": "Air-de-Andrew",
    "port": 27017,
    "version": "3.0.4",
    "gitVersion": "nogitversion"
  },
  "ok": 1
}

```

# 5. Criar um index para esses dois campos juntos
```
db.pokemons.createIndex({defense: 1, attack: 1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 2,
  "numIndexesAfter": 3,
  "ok": 1
}

```

# 6. Refazer a query para os dois campos juntos utilizando explain para ver o resultado da busca
```
db.pokemons.find({$and : [{defense: 50}, {attack: { $gte: 50}}]}).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean-pokemons.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "defense": {
            "$eq": 50
          }
        },
        {
          "attack": {
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
          "defense": 1,
          "attack": 1
        },
        "indexName": "defense_1_attack_1",
        "isMultiKey": false,
        "direction": "forward",
        "indexBounds": {
          "defense": [
            "[50.0, 50.0]"
          ],
          "attack": [
            "[50.0, inf.0]"
          ]
        }
      }
    },
    "rejectedPlans": [ ]
  },
  "executionStats": {
    "executionSuccess": true,
    "nReturned": 2,
    "executionTimeMillis": 2,
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
          "defense": 1,
          "attack": 1
        },
        "indexName": "defense_1_attack_1",
        "isMultiKey": false,
        "direction": "forward",
        "indexBounds": {
          "defense": [
            "[50.0, 50.0]"
          ],
          "attack": [
            "[50.0, inf.0]"
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
    "host": "Air-de-Andrew",
    "port": 27017,
    "version": "3.0.4",
    "gitVersion": "nogitversion"
  },
  "ok": 1
}


```
