# MongoDB - Aula 06 - Exercício
User: [Doozeer](https://github.com/Doozeer)
Autor: Leonardo Filipe

# Fazer uma query para o campo name utilizando `explain` para ver o resultado da busca.
```js
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean> db.pokemons.find({name: "Cloyster"}).explain("executionStats")
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "name": {
        "$eq": "Cloyster"
      }
    },
    "winningPlan": {
      "stage": "COLLSCAN",
      "filter": {
        "name": {
          "$eq": "Cloyster"
        }
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
    "totalDocsExamined": 610,
    "executionStages": {
      "stage": "COLLSCAN",
      "filter": {
        "name": {
          "$eq": "Cloyster"
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
    "host": "Leonardos-MacBook-Pro.local",
    "port": 27017,
    "version": "3.2.0",
    "gitVersion": "45d947729a0315accb6d4f15a6b06be6d9c19fe7"
  },
  "ok": 1
}
```

# Criar um `index` um para o campo `name`.
```js
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean> db.pokemons.createIndex({name: 1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}
```

# Refazer a query para o campo `name` utilizando `explain` para ver o resultado da busca.
```js
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean> db.pokemons.find({name: "Cloyster"}).explain("executionStats")
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "name": {
        "$eq": "Cloyster"
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
            "[\"Cloyster\", \"Cloyster\"]"
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
            "[\"Cloyster\", \"Cloyster\"]"
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
    "host": "Leonardos-MacBook-Pro.local",
    "port": 27017,
    "version": "3.2.0",
    "gitVersion": "45d947729a0315accb6d4f15a6b06be6d9c19fe7"
  },
  "ok": 1
}
```

# Fazer uma query para dois campos juntos utilizando `explain` para ver o resultado da busca.
```js
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean> db.pokemons.find({$and: [{defense: {$lte: 50}}, {attack: {$gte: 100}}]}).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "defense": {
            "$lte": 50
          }
        },
        {
          "attack": {
            "$gte": 100
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
              "$lte": 50
            }
          },
          {
            "attack": {
              "$gte": 100
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
    "nReturned": 4,
    "executionTimeMillis": 0,
    "totalKeysExamined": 0,
    "totalDocsExamined": 610,
    "executionStages": {
      "stage": "COLLSCAN",
      "filter": {
        "$and": [
          {
            "defense": {
              "$lte": 50
            }
          },
          {
            "attack": {
              "$gte": 100
            }
          }
        ]
      },
      "nReturned": 4,
      "executionTimeMillisEstimate": 0,
      "works": 612,
      "advanced": 4,
      "needTime": 607,
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
    "host": "Leonardos-MacBook-Pro.local",
    "port": 27017,
    "version": "3.2.0",
    "gitVersion": "45d947729a0315accb6d4f15a6b06be6d9c19fe7"
  },
  "ok": 1
}
```

# Criar um `index` para esses dois campos juntos.
```js
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean> db.pokemons.createIndex({attack: 1, defense: 1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 2,
  "numIndexesAfter": 3,
  "ok": 1
}
```

# Refazer a query para os dois campos juntos utilizando `explain` para ver o resultado da busca.
```js
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean> db.pokemons.find({$and: [{defense: {$lte: 50}}, {attack: {$gte: 100}}]}).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "defense": {
            "$lte": 50
          }
        },
        {
          "attack": {
            "$gte": 100
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
        "isUnique": false,
        "isSparse": false,
        "isPartial": false,
        "indexVersion": 1,
        "direction": "forward",
        "indexBounds": {
          "attack": [
            "[100.0, inf.0]"
          ],
          "defense": [
            "[-inf.0, 50.0]"
          ]
        }
      }
    },
    "rejectedPlans": [ ]
  },
  "executionStats": {
    "executionSuccess": true,
    "nReturned": 4,
    "executionTimeMillis": 0,
    "totalKeysExamined": 34,
    "totalDocsExamined": 4,
    "executionStages": {
      "stage": "FETCH",
      "nReturned": 4,
      "executionTimeMillisEstimate": 0,
      "works": 35,
      "advanced": 4,
      "needTime": 30,
      "needYield": 0,
      "saveState": 0,
      "restoreState": 0,
      "isEOF": 1,
      "invalidates": 0,
      "docsExamined": 4,
      "alreadyHasObj": 0,
      "inputStage": {
        "stage": "IXSCAN",
        "nReturned": 4,
        "executionTimeMillisEstimate": 0,
        "works": 35,
        "advanced": 4,
        "needTime": 30,
        "needYield": 0,
        "saveState": 0,
        "restoreState": 0,
        "isEOF": 1,
        "invalidates": 0,
        "keyPattern": {
          "attack": 1,
          "defense": 1
        },
        "indexName": "attack_1_defense_1",
        "isMultiKey": false,
        "isUnique": false,
        "isSparse": false,
        "isPartial": false,
        "indexVersion": 1,
        "direction": "forward",
        "indexBounds": {
          "attack": [
            "[100.0, inf.0]"
          ],
          "defense": [
            "[-inf.0, 50.0]"
          ]
        },
        "keysExamined": 34,
        "dupsTested": 0,
        "dupsDropped": 0,
        "seenInvalidated": 0
      }
    }
  },
  "serverInfo": {
    "host": "Leonardos-MacBook-Pro.local",
    "port": 27017,
    "version": "3.2.0",
    "gitVersion": "45d947729a0315accb6d4f15a6b06be6d9c19fe7"
  },
  "ok": 1
}
```