# MongoDB - Aula 06 - Exercício
autor: Marcelo Santana Martins

# 1. Fazer uma query para o campo name utilizando explain para ver o resultado da busca
```
marcelo-VirtualBox(mongod-3.0.7) be-mean> db.pokemons.find({ name: /pikachu/i }).explain("executionStats")
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.pokemons",
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
    "executionTimeMillis": 0,
    "totalKeysExamined": 0,
    "totalDocsExamined": 610,
    "executionStages": {
      "stage": "COLLSCAN",
      "filter": {
        "name": /pikachu/i
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
    "host": "marcelo-VirtualBox",
    "port": 27017,
    "version": "3.0.7",
    "gitVersion": "6ce7cbe8c6b899552dadd907604559806aa2e9bd"
  },
  "ok": 1
}
```

# 2. Criar um index um para o campo name
```
marcelo-VirtualBox(mongod-3.0.7) be-mean> db.pokemons.createIndex({ name: 1 })
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}
```

# 3. Refazer a query para o campo name utilizando explain para ver o resultado da busca
```
marcelo-VirtualBox(mongod-3.0.7) be-mean> db.pokemons.find({ name: /pikachu/i }).explain("executionStats")
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.pokemons",
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
    "executionTimeMillis": 22,
    "totalKeysExamined": 610,
    "totalDocsExamined": 1,
    "executionStages": {
      "stage": "FETCH",
      "nReturned": 1,
      "executionTimeMillisEstimate": 0,
      "works": 611,
      "advanced": 1,
      "needTime": 609,
      "needFetch": 0,
      "saveState": 4,
      "restoreState": 4,
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
        "works": 610,
        "advanced": 1,
        "needTime": 609,
        "needFetch": 0,
        "saveState": 4,
        "restoreState": 4,
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
        "keysExamined": 610,
        "dupsTested": 0,
        "dupsDropped": 0,
        "seenInvalidated": 0,
        "matchTested": 1
      }
    }
  },
  "serverInfo": {
    "host": "marcelo-VirtualBox",
    "port": 27017,
    "version": "3.0.7",
    "gitVersion": "6ce7cbe8c6b899552dadd907604559806aa2e9bd"
  },
  "ok": 1
}
```

# 4. Fazer uma query para dois campos juntos utilizando explain para ver o resultado da busca
```
marcelo-VirtualBox(mongod-3.0.7) be-mean> db.pokemons.find({$and:[{ name: /pikachu/i }, { defense: { $gt: 30 }}]}).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "defense": {
            "$gt": 30
          }
        },
        {
          "name": /pikachu/i
        }
      ]
    },
    "winningPlan": {
      "stage": "KEEP_MUTATIONS",
      "inputStage": {
        "stage": "FETCH",
        "filter": {
          "defense": {
            "$gt": 30
          }
        },
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
      }
    },
    "rejectedPlans": [ ]
  },
  "executionStats": {
    "executionSuccess": true,
    "nReturned": 1,
    "executionTimeMillis": 0,
    "totalKeysExamined": 610,
    "totalDocsExamined": 1,
    "executionStages": {
      "stage": "KEEP_MUTATIONS",
      "nReturned": 1,
      "executionTimeMillisEstimate": 0,
      "works": 611,
      "advanced": 1,
      "needTime": 609,
      "needFetch": 0,
      "saveState": 4,
      "restoreState": 4,
      "isEOF": 1,
      "invalidates": 0,
      "inputStage": {
        "stage": "FETCH",
        "filter": {
          "defense": {
            "$gt": 30
          }
        },
        "nReturned": 1,
        "executionTimeMillisEstimate": 0,
        "works": 611,
        "advanced": 1,
        "needTime": 609,
        "needFetch": 0,
        "saveState": 4,
        "restoreState": 4,
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
          "works": 610,
          "advanced": 1,
          "needTime": 609,
          "needFetch": 0,
          "saveState": 4,
          "restoreState": 4,
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
          "keysExamined": 610,
          "dupsTested": 0,
          "dupsDropped": 0,
          "seenInvalidated": 0,
          "matchTested": 1
        }
      }
    }
  },
  "serverInfo": {
    "host": "marcelo-VirtualBox",
    "port": 27017,
    "version": "3.0.7",
    "gitVersion": "6ce7cbe8c6b899552dadd907604559806aa2e9bd"
  },
  "ok": 1
}
```

# 5. Criar um index para esses dois campos juntos
```
marcelo-VirtualBox(mongod-3.0.7) be-mean>  db.pokemons.createIndex({name: 1, defense: 1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 2,
  "numIndexesAfter": 3,
  "ok": 1
}
```

# 6. Refazer a query para os dois campos juntos utilizando explain para ver o resultado da busca
```
marcelo-VirtualBox(mongod-3.0.7) be-mean> db.pokemons.find({$and:[{ name: /pikachu/i }, { defense: { $gt: 30 }}]}).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "defense": {
            "$gt": 30
          }
        },
        {
          "name": /pikachu/i
        }
      ]
    },
    "winningPlan": {
      "stage": "FETCH",
      "inputStage": {
        "stage": "IXSCAN",
        "filter": {
          "name": /pikachu/i
        },
        "keyPattern": {
          "name": 1,
          "defense": 1
        },
        "indexName": "name_1_defense_1",
        "isMultiKey": false,
        "direction": "forward",
        "indexBounds": {
          "name": [
            "[\"\", {})",
            "[/pikachu/i, /pikachu/i]"
          ],
          "defense": [
            "(30.0, inf.0]"
          ]
        }
      }
    },
    "rejectedPlans": [
      {
        "stage": "KEEP_MUTATIONS",
        "inputStage": {
          "stage": "FETCH",
          "filter": {
            "defense": {
              "$gt": 30
            }
          },
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
        }
      }
    ]
  },
  "executionStats": {
    "executionSuccess": true,
    "nReturned": 1,
    "executionTimeMillis": 1,
    "totalKeysExamined": 610,
    "totalDocsExamined": 1,
    "executionStages": {
      "stage": "FETCH",
      "nReturned": 1,
      "executionTimeMillisEstimate": 0,
      "works": 612,
      "advanced": 1,
      "needTime": 609,
      "needFetch": 0,
      "saveState": 9,
      "restoreState": 9,
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
        "works": 610,
        "advanced": 1,
        "needTime": 609,
        "needFetch": 0,
        "saveState": 9,
        "restoreState": 9,
        "isEOF": 1,
        "invalidates": 0,
        "keyPattern": {
          "name": 1,
          "defense": 1
        },
        "indexName": "name_1_defense_1",
        "isMultiKey": false,
        "direction": "forward",
        "indexBounds": {
          "name": [
            "[\"\", {})",
            "[/pikachu/i, /pikachu/i]"
          ],
          "defense": [
            "(30.0, inf.0]"
          ]
        },
        "keysExamined": 610,
        "dupsTested": 0,
        "dupsDropped": 0,
        "seenInvalidated": 0,
        "matchTested": 1
      }
    }
  },
  "serverInfo": {
    "host": "marcelo-VirtualBox",
    "port": 27017,
    "version": "3.0.7",
    "gitVersion": "6ce7cbe8c6b899552dadd907604559806aa2e9bd"
  },
  "ok": 1
}
```
