#MongoDB - Aula 06 - Exercício
autor: Alex Sandro Souza

##1. Fazer uma query para o campo `name` utilizando `explain` para ver o resultado da busca

```js
gigantus(mongod-3.4.10) be-mean> var query = {name: "Inkay"}
gigantus(mongod-3.4.10) be-mean> db.pokemons.find(query).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "name": {
        "$eq": "Inkay"
      }
    },
    "winningPlan": {
      "stage": "COLLSCAN",
      "filter": {
        "name": {
          "$eq": "Inkay"
        }
      },
      "direction": "forward"
    },
    "rejectedPlans": [ ]
  },
  "executionStats": {
    "executionSuccess": true,
    "nReturned": 1,
    "executionTimeMillis": 1,
    "totalKeysExamined": 0,
    "totalDocsExamined": 610,
    "executionStages": {
      "stage": "COLLSCAN",
      "filter": {
        "name": {
          "$eq": "Inkay"
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
    "host": "gigantus",
    "port": 27017,
    "version": "3.4.10",
    "gitVersion": "078f28920cb24de0dd479b5ea6c66c644f6326e9"
  },
  "ok": 1
}

```

##2. Criar um `index` um para o campo `name`

```js
gigantus(mongod-3.4.10) be-mean> db.pokemons.createIndex({name:1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}

```

##3. Refazer a query para o campo `name` utilizando `explain` para ver o resultado da busca

```js
gigantus(mongod-3.4.10) be-mean> var query = {name: "Inkay"}

gigantus(mongod-3.4.10) be-mean> db.pokemons.find(query).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "name": {
        "$eq": "Inkay"
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
        "multiKeyPaths": {
          "name": [ ]
        },
        "isUnique": false,
        "isSparse": false,
        "isPartial": false,
        "indexVersion": 1,
        "direction": "forward",
        "indexBounds": {
          "name": [
            "[\"Inkay\", \"Inkay\"]"
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
        "multiKeyPaths": {
          "name": [ ]
        },
        "isUnique": false,
        "isSparse": false,
        "isPartial": false,
        "indexVersion": 1,
        "direction": "forward",
        "indexBounds": {
          "name": [
            "[\"Inkay\", \"Inkay\"]"
          ]
        },
        "keysExamined": 1,
        "seeks": 1,
        "dupsTested": 0,
        "dupsDropped": 0,
        "seenInvalidated": 0
      }
    }
  },
  "serverInfo": {
    "host": "gigantus",
    "port": 27017,
    "version": "3.4.10",
    "gitVersion": "078f28920cb24de0dd479b5ea6c66c644f6326e9"
  },
  "ok": 1
}

```

##4. Fazer uma query para dois campos juntos utilizando `explain` para ver o resultado da busca

```js
var query = {types:"fire",defense:{$gt:75}}

gigantus(mongod-3.4.10) be-mean> db.pokemons.find(query).explain("executionStats")
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "types": {
            "$eq": "fire"
          }
        },
        {
          "defense": {
            "$gt": 75
          }
        }
      ]
    },
    "winningPlan": {
      "stage": "COLLSCAN",
      "filter": {
        "$and": [
          {
            "types": {
              "$eq": "fire"
            }
          },
          {
            "defense": {
              "$gt": 75
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
    "nReturned": 12,
    "executionTimeMillis": 1,
    "totalKeysExamined": 0,
    "totalDocsExamined": 610,
    "executionStages": {
      "stage": "COLLSCAN",
      "filter": {
        "$and": [
          {
            "types": {
              "$eq": "fire"
            }
          },
          {
            "defense": {
              "$gt": 75
            }
          }
        ]
      },
      "nReturned": 12,
      "executionTimeMillisEstimate": 0,
      "works": 612,
      "advanced": 12,
      "needTime": 599,
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
    "host": "gigantus",
    "port": 27017,
    "version": "3.4.10",
    "gitVersion": "078f28920cb24de0dd479b5ea6c66c644f6326e9"
  },
  "ok": 1
}


```

##5. Criar um `index` para esses dois campos juntos

```js
gigantus(mongod-3.4.10) be-mean> db.pokemons.createIndex({types:1,defense:1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 2,
  "numIndexesAfter": 3,
  "ok": 1
}

```

##6. Refazer a query para os dois campos juntos utilizando `explain` para ver o resultado da busca

```js
var query = {types:"fire",defense:{$gt:75}}

gigantus(mongod-3.4.10) be-mean> db.pokemons.find(query).explain("executionStats")
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "types": {
            "$eq": "fire"
          }
        },
        {
          "defense": {
            "$gt": 75
          }
        }
      ]
    },
    "winningPlan": {
      "stage": "FETCH",
      "inputStage": {
        "stage": "IXSCAN",
        "keyPattern": {
          "types": 1,
          "defense": 1
        },
        "indexName": "types_1_defense_1",
        "isMultiKey": true,
        "multiKeyPaths": {
          "types": [
            "types"
          ],
          "defense": [ ]
        },
        "isUnique": false,
        "isSparse": false,
        "isPartial": false,
        "indexVersion": 1,
        "direction": "forward",
        "indexBounds": {
          "types": [
            "[\"fire\", \"fire\"]"
          ],
          "defense": [
            "(75.0, inf.0]"
          ]
        }
      }
    },
    "rejectedPlans": [ ]
  },
  "executionStats": {
    "executionSuccess": true,
    "nReturned": 12,
    "executionTimeMillis": 1,
    "totalKeysExamined": 12,
    "totalDocsExamined": 12,
    "executionStages": {
      "stage": "FETCH",
      "nReturned": 12,
      "executionTimeMillisEstimate": 0,
      "works": 13,
      "advanced": 12,
      "needTime": 0,
      "needYield": 0,
      "saveState": 0,
      "restoreState": 0,
      "isEOF": 1,
      "invalidates": 0,
      "docsExamined": 12,
      "alreadyHasObj": 0,
      "inputStage": {
        "stage": "IXSCAN",
        "nReturned": 12,
        "executionTimeMillisEstimate": 0,
        "works": 13,
        "advanced": 12,
        "needTime": 0,
        "needYield": 0,
        "saveState": 0,
        "restoreState": 0,
        "isEOF": 1,
        "invalidates": 0,
        "keyPattern": {
          "types": 1,
          "defense": 1
        },
        "indexName": "types_1_defense_1",
        "isMultiKey": true,
        "multiKeyPaths": {
          "types": [
            "types"
          ],
          "defense": [ ]
        },
        "isUnique": false,
        "isSparse": false,
        "isPartial": false,
        "indexVersion": 1,
        "direction": "forward",
        "indexBounds": {
          "types": [
            "[\"fire\", \"fire\"]"
          ],
          "defense": [
            "(75.0, inf.0]"
          ]
        },
        "keysExamined": 12,
        "seeks": 1,
        "dupsTested": 12,
        "dupsDropped": 0,
        "seenInvalidated": 0
      }
    }
  },
  "serverInfo": {
    "host": "gigantus",
    "port": 27017,
    "version": "3.4.10",
    "gitVersion": "078f28920cb24de0dd479b5ea6c66c644f6326e9"
  },
  "ok": 1
}

```