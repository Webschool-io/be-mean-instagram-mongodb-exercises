#MongoDB - Aula 06 - Exercícios
User: [oescarabel](https://www.github.com/oescarabel)
Autor: Guilherme Henrique Escarabel Silva

##1. Fazer uma query para o campo `name` utilizando `explain` para ver o resultado da busca
```js
sca(mongod-3.2.6) be-mean-instagram> db.pokemons.find({name}).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean-instagram.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "name": {
        "$eq": "street"
      }
    },
    "winningPlan": {
      "stage": "COLLSCAN",
      "filter": {
        "name": {
          "$eq": "street"
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
          "$eq": "street"
        }
      },
      "nReturned": 0,
      "executionTimeMillisEstimate": 0,
      "works": 612,
      "advanced": 0,
      "needTime": 611,
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
    "host": "sca.local",
    "port": 27017,
    "version": "3.2.6",
    "gitVersion": "05552b562c7a0b3143a729aaa0838e558dc49b25"
  },
  "ok": 1
}
```

##2. Criar um `index` um para o campo `name`
```js
sca(mongod-3.2.6) be-mean-instagram> db.pokemons.createIndex({ name: 1 })
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}
```

##3. Refazer a query para o campo `name` utilizando `explain` para ver o resultado da busca
```js
sca(mongod-3.2.6) be-mean-instagram> db.pokemons.find({name: ""}).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean-instagram.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "name": {
        "$eq": ""
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
            "[\"\", \"\"]"
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
            "[\"\", \"\"]"
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
    "host": "sca.local",
    "port": 27017,
    "version": "3.2.6",
    "gitVersion": "05552b562c7a0b3143a729aaa0838e558dc49b25"
  },
  "ok": 1
}
```

##4. Fazer uma query para dois campos juntos utilizando `explain` para ver o resultado da busca
```js
sca(mongod-3.2.6) be-mean-instagram> db.pokemons.find({
...   $and:
...     [{
...       attack:
...         {$gte: 50}},
...         {speed:
...           {$lt:40}
...         }
...     ]}).explain("executionStats")
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean-instagram.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "speed": {
            "$lt": 40
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
            "speed": {
              "$lt": 40
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
    "nReturned": 63,
    "executionTimeMillis": 4,
    "totalKeysExamined": 0,
    "totalDocsExamined": 610,
    "executionStages": {
      "stage": "COLLSCAN",
      "filter": {
        "$and": [
          {
            "speed": {
              "$lt": 40
            }
          },
          {
            "attack": {
              "$gte": 50
            }
          }
        ]
      },
      "nReturned": 63,
      "executionTimeMillisEstimate": 0,
      "works": 612,
      "advanced": 63,
      "needTime": 548,
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
    "host": "sca.local",
    "port": 27017,
    "version": "3.2.6",
    "gitVersion": "05552b562c7a0b3143a729aaa0838e558dc49b25"
  },
  "ok": 1
}

```

##5. Criar um `index` para esses dois campos juntos
```js
sca(mongod-3.2.6) be-mean-instagram> db.pokemons.createIndex({ hp: 1, speed: 1 })
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 2,
  "numIndexesAfter": 3,
  "ok": 1
}
```

##6. Refazer a query para os dois campos juntos utilizando `explain` para ver o resultado da busca
```js
sca(mongod-3.2.6) be-mean-instagram> db.pokemons.find({$and:
...     [{
...       moves: /desvio/i
...     },
...     {
...       defense:
...       {
...         $not:
...         {
...           $lte:49
...         }
...       }
...     }]
...   }).explain("executionStats")
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean-instagram.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "moves": /desvio/i
        },
        {
          "$not": {
            "defense": {
              "$lte": 49
            }
          }
        }
      ]
    },
    "winningPlan": {
      "stage": "COLLSCAN",
      "filter": {
        "$and": [
          {
            "moves": /desvio/i
          },
          {
            "$not": {
              "defense": {
                "$lte": 49
              }
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
    "nReturned": 0,
    "executionTimeMillis": 0,
    "totalKeysExamined": 0,
    "totalDocsExamined": 610,
    "executionStages": {
      "stage": "COLLSCAN",
      "filter": {
        "$and": [
          {
            "moves": /desvio/i
          },
          {
            "$not": {
              "defense": {
                "$lte": 49
              }
            }
          }
        ]
      },
      "nReturned": 0,
      "executionTimeMillisEstimate": 0,
      "works": 612,
      "advanced": 0,
      "needTime": 611,
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
    "host": "sca.local",
    "port": 27017,
    "version": "3.2.6",
    "gitVersion": "05552b562c7a0b3143a729aaa0838e558dc49b25"
  },
  "ok": 1
}
```
