#MongoDB - Aula 06 - Exercício
Autor: Cauê Bruno de Almeida

# 1. Criar dois índices - um para o campo `name` e outro para quaisquer dois campos juntos.

```js
// Primeiro sem o índice sob o campo name
be-mean-pokemons> db.pokemons.find({"name": "Charmilion"}).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean-pokemons.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "name": {
        "$eq": "Charmilion"
      }
    },
    "winningPlan": {
      "stage": "COLLSCAN",
      "filter": {
        "name": {
          "$eq": "Charmilion"
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
    "totalDocsExamined": 9,
    "executionStages": {
      "stage": "COLLSCAN",
      "filter": {
        "name": {
          "$eq": "Charmilion"
        }
      },
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
      "direction": "forward",
      "docsExamined": 9
    }
  },
  "serverInfo": {
    "host": "Caues-MacBook-Pro.local",
    "port": 27017,
    "version": "3.0.5",
    "gitVersion": "nogitversion"
  },
  "ok": 1
}

db.pokemons.createIndex({name : 1})

// Agora com índice sob o campo name
be-mean-pokemons> db.pokemons.find({"name": "Charmilion"}).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean-pokemons.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "name": {
        "$eq": "Charmilion"
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
            "[\"Charmilion\", \"Charmilion\"]"
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
          "name": 1
        },
        "indexName": "name_1",
        "isMultiKey": false,
        "direction": "forward",
        "indexBounds": {
          "name": [
            "[\"Charmilion\", \"Charmilion\"]"
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
    "host": "Caues-MacBook-Pro.local",
    "port": 27017,
    "version": "3.0.5",
    "gitVersion": "nogitversion"
  },
  "ok": 1
}


// Agora para outros dois campos quaisquer juntos
// Sem índice

be-mean-pokemons> db.pokemons.find({ name : 'Charmilion', moves : ['investida', 'desvio'] }).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean-pokemons.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "moves": {
            "$eq": [
              "investida",
              "desvio"
            ]
          }
        },
        {
          "name": {
            "$eq": "Charmilion"
          }
        }
      ]
    },
    "winningPlan": {
      "stage": "KEEP_MUTATIONS",
      "inputStage": {
        "stage": "FETCH",
        "filter": {
          "moves": {
            "$eq": [
              "investida",
              "desvio"
            ]
          }
        },
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
              "[\"Charmilion\", \"Charmilion\"]"
            ]
          }
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
      "stage": "KEEP_MUTATIONS",
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
      "inputStage": {
        "stage": "FETCH",
        "filter": {
          "moves": {
            "$eq": [
              "investida",
              "desvio"
            ]
          }
        },
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
            "name": 1
          },
          "indexName": "name_1",
          "isMultiKey": false,
          "direction": "forward",
          "indexBounds": {
            "name": [
              "[\"Charmilion\", \"Charmilion\"]"
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
  },
  "serverInfo": {
    "host": "Caues-MacBook-Pro.local",
    "port": 27017,
    "version": "3.0.5",
    "gitVersion": "nogitversion"
  },
  "ok": 1
}

// Criando índice
be-mean-pokemons> db.pokemons.getIndexes()
[
  {
    "v": 1,
    "key": {
      "_id": 1
    },
    "name": "_id_",
    "ns": "be-mean-pokemons.pokemons"
  },
  {
    "v": 1,
    "key": {
      "name": 1
    },
    "name": "name_1",
    "ns": "be-mean-pokemons.pokemons"
  },
  {
    "v": 1,
    "key": {
      "description": 1,
      "moves": 1
    },
    "name": "description_1_moves_1",
    "ns": "be-mean-pokemons.pokemons"
  }
]

// Agora com índice
be-mean-pokemons> db.pokemons.find({ name : 'Charmilion', moves : ['investida', 'desvio'] }).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean-pokemons.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "moves": {
            "$eq": [
              "investida",
              "desvio"
            ]
          }
        },
        {
          "name": {
            "$eq": "Charmilion"
          }
        }
      ]
    },
    "winningPlan": {
      "stage": "KEEP_MUTATIONS",
      "inputStage": {
        "stage": "FETCH",
        "filter": {
          "moves": {
            "$eq": [
              "investida",
              "desvio"
            ]
          }
        },
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
              "[\"Charmilion\", \"Charmilion\"]"
            ]
          }
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
      "stage": "KEEP_MUTATIONS",
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
      "inputStage": {
        "stage": "FETCH",
        "filter": {
          "moves": {
            "$eq": [
              "investida",
              "desvio"
            ]
          }
        },
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
            "name": 1
          },
          "indexName": "name_1",
          "isMultiKey": false,
          "direction": "forward",
          "indexBounds": {
            "name": [
              "[\"Charmilion\", \"Charmilion\"]"
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
  },
  "serverInfo": {
    "host": "Caues-MacBook-Pro.local",
    "port": 27017,
    "version": "3.0.5",
    "gitVersion": "nogitversion"
  },
  "ok": 1
}

```
