# MongoDB - Aula 06 - Exercício
User: lucasduarte
Autor: Lucas Duarte Anicio

## Fazer uma query para o campo name utilizando `explain` para ver o resultado da busca.

```

be-mean> db.pokemons.find({name:"pikachu"}).explain("executionStats")
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "name": {
        "$eq": "pikachu"
      }
    },
    "winningPlan": {
      "stage": "COLLSCAN",
      "filter": {
        "name": {
          "$eq": "pikachu"
        }
      },
      "direction": "forward"
    },
    "rejectedPlans": [ ]
  },
  "executionStats": {
    "executionSuccess": true,
    "nReturned": 0,
    "executionTimeMillis": 0,
    "totalKeysExamined": 0,
    "totalDocsExamined": 620,
    "executionStages": {
      "stage": "COLLSCAN",
      "filter": {
        "name": {
          "$eq": "pikachu"
        }
      },
      "nReturned": 0,
      "executionTimeMillisEstimate": 0,
      "works": 622,
      "advanced": 0,
      "needTime": 621,
      "needYield": 0,
      "saveState": 4,
      "restoreState": 4,
      "isEOF": 1,
      "invalidates": 0,
      "direction": "forward",
      "docsExamined": 620
    }
  },
  "serverInfo": {
    "host": "lucas-pc",
    "port": 27017,
    "version": "3.2.3",
    "gitVersion": "b326ba837cf6f49d65c2f85e1b70f6f31ece7937"
  },
  "ok": 1
}



```

##Criar um `index` um para o campo `name`.

```
be-mean> db.pokemons.createIndex( {name: 1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}



```

## Refazer a query para o campo `name` utilizando `explain` para ver o resultado da busca.

```

be-mean> db.pokemons.find({name:"pikachu"}).explain("executionStats")
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "name": {
        "$eq": "pikachu"
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
            "[\"pikachu\", \"pikachu\"]"
          ]
        }
      }
    },
    "rejectedPlans": [ ]
  },
  "executionStats": {
    "executionSuccess": true,
    "nReturned": 0,
    "executionTimeMillis": 0,
    "totalKeysExamined": 0,
    "totalDocsExamined": 0,
    "executionStages": {
      "stage": "FETCH",
      "nReturned": 0,
      "executionTimeMillisEstimate": 0,
      "works": 1,
      "advanced": 0,
      "needTime": 0,
      "needYield": 0,
      "saveState": 0,
      "restoreState": 0,
      "isEOF": 1,
      "invalidates": 0,
      "docsExamined": 0,
      "alreadyHasObj": 0,
      "inputStage": {
        "stage": "IXSCAN",
        "nReturned": 0,
        "executionTimeMillisEstimate": 0,
        "works": 1,
        "advanced": 0,
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
            "[\"pikachu\", \"pikachu\"]"
          ]
        },
        "keysExamined": 0,
        "dupsTested": 0,
        "dupsDropped": 0,
        "seenInvalidated": 0
      }
    }
  },
  "serverInfo": {
    "host": "lucas-pc",
    "port": 27017,
    "version": "3.2.3",
    "gitVersion": "b326ba837cf6f49d65c2f85e1b70f6f31ece7937"
  },
  "ok": 1
}


```

## Fazer uma query para dois campos juntos utilizando `explain` para ver o resultado da busca.

```

be-mean> db.pokemons.find({name:"Bellsprout", speed:40}).explain("executionStats")
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "name": {
            "$eq": "Bellsprout"
          }
        },
        {
          "speed": {
            "$eq": 40
          }
        }
      ]
    },
    "winningPlan": {
      "stage": "FETCH",
      "filter": {
        "speed": {
          "$eq": 40
        }
      },
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
            "[\"Bellsprout\", \"Bellsprout\"]"
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
      "filter": {
        "speed": {
          "$eq": 40
        }
      },
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
            "[\"Bellsprout\", \"Bellsprout\"]"
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
    "host": "lucas-pc",
    "port": 27017,
    "version": "3.2.3",
    "gitVersion": "b326ba837cf6f49d65c2f85e1b70f6f31ece7937"
  },
  "ok": 1
}


```

## Criar um `index` para esses dois campos juntos.

```

be-mean> db.pokemons.createIndex({name: 1, speed: 1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 3,
  "numIndexesAfter": 4,
  "ok": 1
}


```

## Refazer a query para os dois campos juntos utilizando `explain` para ver o resultado da busca.

```

be-mean> db.pokemons.find({name:"Bellsprout", speed:40}).explain("executionStats")
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "name": {
            "$eq": "Bellsprout"
          }
        },
        {
          "speed": {
            "$eq": 40
          }
        }
      ]
    },
    "winningPlan": {
      "stage": "FETCH",
      "inputStage": {
        "stage": "IXSCAN",
        "keyPattern": {
          "name": 1,
          "speed": 1
        },
        "indexName": "name_1_speed_1",
        "isMultiKey": false,
        "isUnique": false,
        "isSparse": false,
        "isPartial": false,
        "indexVersion": 1,
        "direction": "forward",
        "indexBounds": {
          "name": [
            "[\"Bellsprout\", \"Bellsprout\"]"
          ],
          "speed": [
            "[40.0, 40.0]"
          ]
        }
      }
    },
    "rejectedPlans": [
      {
        "stage": "FETCH",
        "filter": {
          "speed": {
            "$eq": 40
          }
        },
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
              "[\"Bellsprout\", \"Bellsprout\"]"
            ]
          }
        }
      }
    ]
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
      "works": 3,
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
          "name": 1,
          "speed": 1
        },
        "indexName": "name_1_speed_1",
        "isMultiKey": false,
        "isUnique": false,
        "isSparse": false,
        "isPartial": false,
        "indexVersion": 1,
        "direction": "forward",
        "indexBounds": {
          "name": [
            "[\"Bellsprout\", \"Bellsprout\"]"
          ],
          "speed": [
            "[40.0, 40.0]"
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
    "host": "lucas-pc",
    "port": 27017,
    "version": "3.2.3",
    "gitVersion": "b326ba837cf6f49d65c2f85e1b70f6f31ece7937"
  },
  "ok": 1
}


```
