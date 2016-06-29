# MongoDB - Aula 06 - Exercício
autor: Ederson Devaldo da Silva

## Fazer uma query para o campo `name` utilizando `explain` para ver o resultado da busca

```
codevops(mongod-3.0.6) be-mean> var query = {name: 1}
codevops(mongod-3.0.6) be-mean> db.pokemons.find(query).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "name": {
        "$eq": 1
      }
    },
    "winningPlan": {
      "stage": "COLLSCAN",
      "filter": {
        "name": {
          "$eq": 1
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
    "totalDocsExamined": 610,
    "executionStages": {
      "stage": "COLLSCAN",
      "filter": {
        "name": {
          "$eq": 1
        }
      },
      "nReturned": 0,
      "executionTimeMillisEstimate": 0,
      "works": 612,
      "advanced": 0,
      "needTime": 611,
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
    "host": "codevops",
    "port": 27017,
    "version": "3.0.6",
    "gitVersion": "nogitversion"
  },
  "ok": 1
}
```

## Criar um `index` para o campo `name`

```
codevops(mongod-3.0.6) be-mean> db.pokemons.createIndex({ name:1 })
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}
codevops(mongod-3.0.6) be-mean> db.pokemons.getIndexes()
[
  {
    "v": 1,
    "key": {
      "_id": 1
    },
    "name": "_id_",
    "ns": "be-mean.pokemons"
  },
  {
    "v": 1,
    "key": {
      "name": 1
    },
    "name": "name_1",
    "ns": "be-mean.pokemons"
  }
]
```

## Refazer a query para o campo `name` utilizando `explain` para ver o resultado da busca

```
codevops(mongod-3.0.6) be-mean> db.pokemons.find(query).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "name": {
        "$eq": 1
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
            "[1.0, 1.0]"
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
      "needFetch": 0,
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
            "[1.0, 1.0]"
          ]
        },
        "keysExamined": 0,
        "dupsTested": 0,
        "dupsDropped": 0,
        "seenInvalidated": 0,
        "matchTested": 0
      }
    }
  },
  "serverInfo": {
    "host": "codevops",
    "port": 27017,
    "version": "3.0.6",
    "gitVersion": "nogitversion"
  },
  "ok": 1
}
```

## Fazer uma query para dois campos juntos utilizando `explain` para ver o resultado da busca

```
var query = {defense: {$gt: 10}, speed: {$gt: 20}}
codevops(mongod-3.0.6) be-mean> db.pokemons.find(query).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "defense": {
            "$gt": 10
          }
        },
        {
          "speed": {
            "$gt": 20
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
              "$gt": 10
            }
          },
          {
            "speed": {
              "$gt": 20
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
    "nReturned": 583,
    "executionTimeMillis": 1,
    "totalKeysExamined": 0,
    "totalDocsExamined": 610,
    "executionStages": {
      "stage": "COLLSCAN",
      "filter": {
        "$and": [
          {
            "defense": {
              "$gt": 10
            }
          },
          {
            "speed": {
              "$gt": 20
            }
          }
        ]
      },
      "nReturned": 583,
      "executionTimeMillisEstimate": 0,
      "works": 612,
      "advanced": 583,
      "needTime": 28,
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
    "host": "codevops",
    "port": 27017,
    "version": "3.0.6",
    "gitVersion": "nogitversion"
  },
  "ok": 1
}
```

## Criar um `index` para esses dois campos juntos

```
codevops(mongod-3.0.6) be-mean> db.pokemons.createIndex({ defense:1, speed:1 })
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 2,
  "numIndexesAfter": 3,
  "ok": 1
}
```


## Refazer a query para os dois campos juntos utilizando `explain` para ver o resultado da busca

```
var query = {defense: {$gt: 10}, speed: {$gt: 20}}
codevops(mongod-3.0.6) be-mean> db.pokemons.find(query).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "defense": {
            "$gt": 10
          }
        },
        {
          "speed": {
            "$gt": 20
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
          "speed": 1
        },
        "indexName": "defense_1_speed_1",
        "isMultiKey": false,
        "direction": "forward",
        "indexBounds": {
          "defense": [
            "(10.0, inf.0]"
          ],
          "speed": [
            "(20.0, inf.0]"
          ]
        }
      }
    },
    "rejectedPlans": [ ]
  },
  "executionStats": {
    "executionSuccess": true,
    "nReturned": 583,
    "executionTimeMillis": 1,
    "totalKeysExamined": 601,
    "totalDocsExamined": 583,
    "executionStages": {
      "stage": "FETCH",
      "nReturned": 583,
      "executionTimeMillisEstimate": 0,
      "works": 601,
      "advanced": 583,
      "needTime": 17,
      "needFetch": 0,
      "saveState": 4,
      "restoreState": 4,
      "isEOF": 1,
      "invalidates": 0,
      "docsExamined": 583,
      "alreadyHasObj": 0,
      "inputStage": {
        "stage": "IXSCAN",
        "nReturned": 583,
        "executionTimeMillisEstimate": 0,
        "works": 601,
        "advanced": 583,
        "needTime": 17,
        "needFetch": 0,
        "saveState": 4,
        "restoreState": 4,
        "isEOF": 1,
        "invalidates": 0,
        "keyPattern": {
          "defense": 1,
          "speed": 1
        },
        "indexName": "defense_1_speed_1",
        "isMultiKey": false,
        "direction": "forward",
        "indexBounds": {
          "defense": [
            "(10.0, inf.0]"
          ],
          "speed": [
            "(20.0, inf.0]"
          ]
        },
        "keysExamined": 601,
        "dupsTested": 0,
        "dupsDropped": 0,
        "seenInvalidated": 0,
        "matchTested": 0
      }
    }
  },
  "serverInfo": {
    "host": "codevops",
    "port": 27017,
    "version": "3.0.6",
    "gitVersion": "nogitversion"
  },
  "ok": 1
}
```


