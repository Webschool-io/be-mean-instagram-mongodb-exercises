# MongoDB - Aula 06 - Exercício
===
Autor: Gabriel Tomé

###1 - Fazer uma query para o campo name utilizando explain para ver o resultado da busca

```
MacBook-Pro-de-Gabriel-Tome(mongod-3.0.7) pokemons> var query = {name:"Pikachu"}

MacBook-Pro-de-Gabriel-Tome(mongod-3.0.7) pokemons> db.pokemons.find(query).explain()
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "pokemons.pokemons",
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
  "serverInfo": {
    "host": "MacBook-Pro-de-Gabriel-Tome.local",
    "port": 27017,
    "version": "3.0.7",
    "gitVersion": "nogitversion"
  },
  "ok": 1
}

// com executionStats

MacBook-Pro-de-Gabriel-Tome(mongod-3.0.7) pokemons> db.pokemons.find(query).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 1,
  "executionTimeMillis": 1,
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
}

```

###2 - Criar um index um para o campo name

```
MacBook-Pro-de-Gabriel-Tome(mongod-3.0.7) pokemons> db.pokemons.getIndexes()
[
  {
    "v": 1,
    "key": {
      "_id": 1
    },
    "name": "_id_",
    "ns": "pokemons.pokemons"
  }
]
MacBook-Pro-de-Gabriel-Tome(mongod-3.0.7) pokemons> db.pokemons.createIndex({name:1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}
MacBook-Pro-de-Gabriel-Tome(mongod-3.0.7) pokemons> db.pokemons.getIndexes()
[
  {
    "v": 1,
    "key": {
      "_id": 1
    },
    "name": "_id_",
    "ns": "pokemons.pokemons"
  },
  {
    "v": 1,
    "key": {
      "name": 1
    },
    "name": "name_1",
    "ns": "pokemons.pokemons"
  }
]

```

###3 - Refazer a query para o campo name utilizando explain para ver o resultado da busca

```
MacBook-Pro-de-Gabriel-Tome(mongod-3.0.7) pokemons> db.pokemons.find(query).explain()
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "pokemons.pokemons",
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
          "name": 1
        },
        "indexName": "name_1",
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
  "serverInfo": {
    "host": "MacBook-Pro-de-Gabriel-Tome.local",
    "port": 27017,
    "version": "3.0.7",
    "gitVersion": "nogitversion"
  },
  "ok": 1
}


MacBook-Pro-de-Gabriel-Tome(mongod-3.0.7) pokemons> db.pokemons.find(query).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 1,
  "executionTimeMillis": 74,
  "totalKeysExamined": 1,
  "totalDocsExamined": 1,
  "executionStages": {
    "stage": "FETCH",
    "nReturned": 1,
    "executionTimeMillisEstimate": 70,
    "works": 2,
    "advanced": 1,
    "needTime": 0,
    "needFetch": 0,
    "saveState": 1,
    "restoreState": 1,
    "isEOF": 1,
    "invalidates": 0,
    "docsExamined": 1,
    "alreadyHasObj": 0,
    "inputStage": {
      "stage": "IXSCAN",
      "nReturned": 1,
      "executionTimeMillisEstimate": 70,
      "works": 1,
      "advanced": 1,
      "needTime": 0,
      "needFetch": 0,
      "saveState": 1,
      "restoreState": 1,
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
}

```

###4 - Fazer uma query para dois campos juntos utilizando explain para ver o resultado da busca

```
MacBook-Pro-de-Gabriel-Tome(mongod-3.0.7) pokemons> var query = {$and: [ {speed: {$gt:50}}, {attack: {$gt:50}} ]}
MacBook-Pro-de-Gabriel-Tome(mongod-3.0.7) pokemons> query
{
  "$and": [
    {
      "speed": {
        "$gt": 50
      }
    },
    {
      "attack": {
        "$gt": 50
      }
    }
  ]
}
MacBook-Pro-de-Gabriel-Tome(mongod-3.0.7) pokemons> db.pokemons.find(query).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 323,
  "executionTimeMillis": 1,
  "totalKeysExamined": 0,
  "totalDocsExamined": 610,
  "executionStages": {
    "stage": "COLLSCAN",
    "filter": {
      "$and": [
        {
          "attack": {
            "$gt": 50
          }
        },
        {
          "speed": {
            "$gt": 50
          }
        }
      ]
    },
    "nReturned": 323,
    "executionTimeMillisEstimate": 0,
    "works": 612,
    "advanced": 323,
    "needTime": 288,
    "needFetch": 0,
    "saveState": 4,
    "restoreState": 4,
    "isEOF": 1,
    "invalidates": 0,
    "direction": "forward",
    "docsExamined": 610
  }
}
```

###5 - Criar um index para esses dois campos juntos

```
MacBook-Pro-de-Gabriel-Tome(mongod-3.0.7) pokemons> db.pokemons.createIndex({speed:1, attack:1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 2,
  "numIndexesAfter": 3,
  "ok": 1
}
MacBook-Pro-de-Gabriel-Tome(mongod-3.0.7) pokemons> db.pokemons.getIndexes()
[
  {
    "v": 1,
    "key": {
      "_id": 1
    },
    "name": "_id_",
    "ns": "pokemons.pokemons"
  },
  {
    "v": 1,
    "key": {
      "name": 1
    },
    "name": "name_1",
    "ns": "pokemons.pokemons"
  },
  {
    "v": 1,
    "key": {
      "speed": 1,
      "attack": 1
    },
    "name": "speed_1_attack_1",
    "ns": "pokemons.pokemons"
  }
]
```

###6 - Refazer a query para os dois campos juntos utilizando explain para ver o resultado da busca

```
MacBook-Pro-de-Gabriel-Tome(mongod-3.0.7) pokemons> db.pokemons.find(query).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 323,
  "executionTimeMillis": 2,
  "totalKeysExamined": 347,
  "totalDocsExamined": 323,
  "executionStages": {
    "stage": "FETCH",
    "nReturned": 323,
    "executionTimeMillisEstimate": 0,
    "works": 348,
    "advanced": 323,
    "needTime": 24,
    "needFetch": 0,
    "saveState": 2,
    "restoreState": 2,
    "isEOF": 1,
    "invalidates": 0,
    "docsExamined": 323,
    "alreadyHasObj": 0,
    "inputStage": {
      "stage": "IXSCAN",
      "nReturned": 323,
      "executionTimeMillisEstimate": 0,
      "works": 347,
      "advanced": 323,
      "needTime": 24,
      "needFetch": 0,
      "saveState": 2,
      "restoreState": 2,
      "isEOF": 1,
      "invalidates": 0,
      "keyPattern": {
        "speed": 1,
        "attack": 1
      },
      "indexName": "speed_1_attack_1",
      "isMultiKey": false,
      "direction": "forward",
      "indexBounds": {
        "speed": [
          "(50.0, inf.0]"
        ],
        "attack": [
          "(50.0, inf.0]"
        ]
      },
      "keysExamined": 347,
      "dupsTested": 0,
      "dupsDropped": 0,
      "seenInvalidated": 0,
      "matchTested": 0
    }
  }
}
```