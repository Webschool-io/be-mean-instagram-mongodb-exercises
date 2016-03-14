# MongoDB - Aula 06 - Exercício
User: [Cerezini](https://github.com/Cerezini)
Autor: Mateus Cerezini Gomes

## 1. Fazer uma query para o campo name utilizando `explain` para ver o resultado da busca.
```js
 be-mean-instagram> db.pokemons.find({name: 'Charmander'}).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean-instagram.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "name": {
        "$eq": "Charmander"
      }
    },
    "winningPlan": {
      "stage": "COLLSCAN",
      "filter": {
        "name": {
          "$eq": "Charmander"
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
    "totalDocsExamined": 614,
    "executionStages": {
      "stage": "COLLSCAN",
      "filter": {
        "name": {
          "$eq": "Charmander"
        }
      },
      "nReturned": 1,
      "executionTimeMillisEstimate": 0,
      "works": 616,
      "advanced": 1,
      "needTime": 614,
      "needFetch": 0,
      "saveState": 4,
      "restoreState": 4,
      "isEOF": 1,
      "invalidates": 0,
      "direction": "forward",
      "docsExamined": 614
    }
  },
  "serverInfo": {
    "host": "matrix",
    "port": 27017,
    "version": "3.0.9",
    "gitVersion": "20d60d3491908f1ae252fe452300de3978a040c7"
  },
  "ok": 1
}
```


## 2. Criar um `index` um para o campo `name`.
```js
be-mean-instagram> db.pokemons.createIndex({name: 1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}
```


## 3. Refazer a query para o campo `name` utilizando `explain` para ver o resultado da busca.
```js
be-mean-instagram> db.pokemons.find({name: 'Charmander'}).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean-instagram.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "name": {
        "$eq": "Charmander"
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
            "[\"Charmander\", \"Charmander\"]"
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
            "[\"Charmander\", \"Charmander\"]"
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
    "host": "matrix",
    "port": 27017,
    "version": "3.0.9",
    "gitVersion": "20d60d3491908f1ae252fe452300de3978a040c7"
  },
  "ok": 1
}
```


## 4. Fazer uma query para dois campos juntos utilizando `explain` para ver o resultado da busca.
```js
be-mean-instagram> db.pokemons.find({$and: [{attack: 52},{speed: 65}]}).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean-instagram.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "attack": {
            "$eq": 52
          }
        },
        {
          "speed": {
            "$eq": 65
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
              "$eq": 52
            }
          },
          {
            "speed": {
              "$eq": 65
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
    "executionTimeMillis": 0,
    "totalKeysExamined": 0,
    "totalDocsExamined": 614,
    "executionStages": {
      "stage": "COLLSCAN",
      "filter": {
        "$and": [
          {
            "attack": {
              "$eq": 52
            }
          },
          {
            "speed": {
              "$eq": 65
            }
          }
        ]
      },
      "nReturned": 2,
      "executionTimeMillisEstimate": 0,
      "works": 616,
      "advanced": 2,
      "needTime": 613,
      "needFetch": 0,
      "saveState": 4,
      "restoreState": 4,
      "isEOF": 1,
      "invalidates": 0,
      "direction": "forward",
      "docsExamined": 614
    }
  },
  "serverInfo": {
    "host": "matrix",
    "port": 27017,
    "version": "3.0.9",
    "gitVersion": "20d60d3491908f1ae252fe452300de3978a040c7"
  },
  "ok": 1
}
```


## 5. Criar um `index` para esses dois campos juntos.
```js
db.pokemons.createIndex({attack: 1, speed: 1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 2,
  "numIndexesAfter": 3,
  "ok": 1
}
```


## 6. Refazer a query para os dois campos juntos utilizando `explain` para ver o resultado da busca.
```js
 be-mean-instagram> db.pokemons.find({$and: [{attack: 52},{speed: 65}]}).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean-instagram.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "attack": {
            "$eq": 52
          }
        },
        {
          "speed": {
            "$eq": 65
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
          "speed": 1
        },
        "indexName": "attack_1_speed_1",
        "isMultiKey": false,
        "direction": "forward",
        "indexBounds": {
          "attack": [
            "[52.0, 52.0]"
          ],
          "speed": [
            "[65.0, 65.0]"
          ]
        }
      }
    },
    "rejectedPlans": [ ]
  },
  "executionStats": {
    "executionSuccess": true,
    "nReturned": 2,
    "executionTimeMillis": 0,
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
          "attack": 1,
          "speed": 1
        },
        "indexName": "attack_1_speed_1",
        "isMultiKey": false,
        "direction": "forward",
        "indexBounds": {
          "attack": [
            "[52.0, 52.0]"
          ],
          "speed": [
            "[65.0, 65.0]"
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
    "host": "matrix",
    "port": 27017,
    "version": "3.0.9",
    "gitVersion": "20d60d3491908f1ae252fe452300de3978a040c7"
  },
  "ok": 1
}
```
