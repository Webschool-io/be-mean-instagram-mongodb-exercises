# MongoDB - Aula 06 - Exercício
Autor: Caio Henrique Ribeiro Martins

# 1. Fazer uma query para o campo name utilizando explain para ver o resultado da busca
```
caio-pc(mongod-3.2.7) be-mean> var query = {name:/pikachu/i}
caio-pc(mongod-3.2.7) be-mean> db.pokemons.find(query).explain('executionStats')
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
    "executionTimeMillis": 1,
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
    "host": "caio-pc",
    "port": 27017,
    "version": "3.2.7",
    "gitVersion": "4249c1d2b5999ebbf1fdf3bc0e0e3b3ff5c0aaf2"
  },
  "ok": 1
}

```
# 3. Refazer a query para o campo name utilizando explain para ver o resultado da busca

caio-pc(mongod-3.2.7) be-mean> var query = {name : /pikachu/i}
caio-pc(mongod-3.2.7) be-mean> db.pokemons.find(query).explain('executionStats')
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
    "host": "caio-pc",
    "port": 27017,
    "version": "3.2.7",
    "gitVersion": "4249c1d2b5999ebbf1fdf3bc0e0e3b3ff5c0aaf2"
  },
  "ok": 1
}
```
```
# 4. Fazer uma query para dois campos juntos utilizando explain para ver o resultado da busca
```
caio-pc(mongod-3.2.7) be-mean> var query = {  $and: [{defense:{$gt:10}} , {attack:{$gt:40}} ] }
caio-pc(mongod-3.2.7) be-mean> db.pokemons.find(query).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "attack": {
            "$gt": 40
          }
        },
        {
          "defense": {
            "$gt": 10
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
              "$gt": 40
            }
          },
          {
            "defense": {
              "$gt": 10
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
    "nReturned": 534,
    "executionTimeMillis": 0,
    "totalKeysExamined": 0,
    "totalDocsExamined": 610,
    "executionStages": {
      "stage": "COLLSCAN",
      "filter": {
        "$and": [
          {
            "attack": {
              "$gt": 40
            }
          },
          {
            "defense": {
              "$gt": 10
            }
          }
        ]
      },
      "nReturned": 534,
      "executionTimeMillisEstimate": 0,
      "works": 612,
      "advanced": 534,
      "needTime": 77,
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
    "host": "caio-pc",
    "port": 27017,
    "version": "3.2.7",
    "gitVersion": "4249c1d2b5999ebbf1fdf3bc0e0e3b3ff5c0aaf2"
  },
  "ok": 1
}

```
# 5. Criar um index para esses dois campos juntos

```
caio-pc(mongod-3.2.7) be-mean> var index = {defense: 1,attack :1}
caio-pc(mongod-3.2.7) be-mean> db.pokemons.createIndex(index)
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}

```

# 6. Refazer a query para os dois campos juntos utilizando explain para ver o resultado da busca
```
caio-pc(mongod-3.2.7) be-mean> var query = {  $and: [{defense:{$gt:10}} , {attack:{$gt:40}} ] }
caio-pc(mongod-3.2.7) be-mean> db.pokemons.find(query).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "attack": {
            "$gt": 40
          }
        },
        {
          "defense": {
            "$gt": 10
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
        "isUnique": false,
        "isSparse": false,
        "isPartial": false,
        "indexVersion": 1,
        "direction": "forward",
        "indexBounds": {
          "defense": [
            "(10.0, inf.0]"
          ],
          "attack": [
            "(40.0, inf.0]"
          ]
        }
      }
    },
    "rejectedPlans": [ ]
  },
  "executionStats": {
    "executionSuccess": true,
    "nReturned": 534,
    "executionTimeMillis": 1,
    "totalKeysExamined": 561,
    "totalDocsExamined": 534,
    "executionStages": {
      "stage": "FETCH",
      "nReturned": 534,
      "executionTimeMillisEstimate": 0,
      "works": 562,
      "advanced": 534,
      "needTime": 27,
      "needYield": 0,
      "saveState": 4,
      "restoreState": 4,
      "isEOF": 1,
      "invalidates": 0,
      "docsExamined": 534,
      "alreadyHasObj": 0,
      "inputStage": {
        "stage": "IXSCAN",
        "nReturned": 534,
        "executionTimeMillisEstimate": 0,
        "works": 562,
        "advanced": 534,
        "needTime": 27,
        "needYield": 0,
        "saveState": 4,
        "restoreState": 4,
        "isEOF": 1,
        "invalidates": 0,
        "keyPattern": {
          "defense": 1,
          "attack": 1
        },
        "indexName": "defense_1_attack_1",
        "isMultiKey": false,
        "isUnique": false,
        "isSparse": false,
        "isPartial": false,
        "indexVersion": 1,
        "direction": "forward",
        "indexBounds": {
          "defense": [
            "(10.0, inf.0]"
          ],
          "attack": [
            "(40.0, inf.0]"
          ]
        },
        "keysExamined": 561,
        "dupsTested": 0,
        "dupsDropped": 0,
        "seenInvalidated": 0
      }
    }
  },
  "serverInfo": {
    "host": "caio-pc",
    "port": 27017,
    "version": "3.2.7",
    "gitVersion": "4249c1d2b5999ebbf1fdf3bc0e0e3b3ff5c0aaf2"
  },
  "ok": 1
}

```
