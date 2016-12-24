# MongoDB - Aula 06 - Exercício
autor: **Leonardo Flores**

## 1. Fazer uma query para o campo `name` utilizando `explain` para ver o resultado da busca

```
MBP-de-Leonardo(mongod-3.2.1) be-mean-pokemons> var query = {name: /bulbasaur/i}
MBP-de-Leonardo(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean-pokemons.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "name": /bulbasaur/i
    },
    "winningPlan": {
      "stage": "COLLSCAN",
      "filter": {
        "name": /bulbasaur/i
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
    "totalDocsExamined": 590,
    "executionStages": {
      "stage": "COLLSCAN",
      "filter": {
        "name": /bulbasaur/i
      },
      "nReturned": 1,
      "executionTimeMillisEstimate": 0,
      "works": 592,
      "advanced": 1,
      "needTime": 590,
      "needYield": 0,
      "saveState": 4,
      "restoreState": 4,
      "isEOF": 1,
      "invalidates": 0,
      "direction": "forward",
      "docsExamined": 590
    }
  },
  "serverInfo": {
    "host": "MBP-de-Leonardo",
    "port": 27017,
    "version": "3.2.1",
    "gitVersion": "a14d55980c2cdc565d4704a7e3ad37e4e535c1b2"
  },
  "ok": 1
}
```

## 2. Criar um `index` um para o campo `name`.

```
MBP-de-Leonardo(mongod-3.2.1) be-mean-pokemons> db.pokemons.createIndex({name: 1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}
```


## 3. Refazer a query para o campo `name` utilizando `explain` para ver o resultado da busca.

```
MBP-de-Leonardo(mongod-3.2.1) be-mean-pokemons> var query = {name: 'Bulbasaur'}
MBP-de-Leonardo(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean-pokemons.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "name": {
        "$eq": "Bulbasaur"
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
            "[\"Bulbasaur\", \"Bulbasaur\"]"
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
            "[\"Bulbasaur\", \"Bulbasaur\"]"
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
    "host": "MBP-de-Leonardo",
    "port": 27017,
    "version": "3.2.1",
    "gitVersion": "a14d55980c2cdc565d4704a7e3ad37e4e535c1b2"
  },
  "ok": 1
}
```

## 4. Fazer uma query para dois campos juntos utilizando `explain` para ver o resultado da busca.

```
MBP-de-Leonardo(mongod-3.2.1) be-mean-pokemons> var query = {$and: [{types: 'electric'}, {attack: {$lt: 50}}]}
MBP-de-Leonardo(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean-pokemons.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "types": {
            "$eq": "electric"
          }
        },
        {
          "attack": {
            "$lt": 50
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
              "$eq": "electric"
            }
          },
          {
            "attack": {
              "$lt": 50
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
    "nReturned": 8,
    "executionTimeMillis": 0,
    "totalKeysExamined": 0,
    "totalDocsExamined": 590,
    "executionStages": {
      "stage": "COLLSCAN",
      "filter": {
        "$and": [
          {
            "types": {
              "$eq": "electric"
            }
          },
          {
            "attack": {
              "$lt": 50
            }
          }
        ]
      },
      "nReturned": 8,
      "executionTimeMillisEstimate": 0,
      "works": 592,
      "advanced": 8,
      "needTime": 583,
      "needYield": 0,
      "saveState": 4,
      "restoreState": 4,
      "isEOF": 1,
      "invalidates": 0,
      "direction": "forward",
      "docsExamined": 590
    }
  },
  "serverInfo": {
    "host": "MBP-de-Leonardo",
    "port": 27017,
    "version": "3.2.1",
    "gitVersion": "a14d55980c2cdc565d4704a7e3ad37e4e535c1b2"
  },
  "ok": 1
}
```

## 5. Criar um `index` para esses dois campos juntos.

```
MBP-de-Leonardo(mongod-3.2.1) be-mean-pokemons> db.pokemons.createIndex({types: 1, attack: 1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 2,
  "numIndexesAfter": 3,
  "ok": 1
}
```


## 6. Refazer a query para os dois campos juntos utilizando `explain` para ver o resultado da busca.

```
MBP-de-Leonardo(mongod-3.2.1) be-mean-pokemons> var query = {$and: [{types: 'electric'}, {attack: {$lt: 50}}]}
MBP-de-Leonardo(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean-pokemons.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "types": {
            "$eq": "electric"
          }
        },
        {
          "attack": {
            "$lt": 50
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
          "attack": 1
        },
        "indexName": "types_1_attack_1",
        "isMultiKey": true,
        "isUnique": false,
        "isSparse": false,
        "isPartial": false,
        "indexVersion": 1,
        "direction": "forward",
        "indexBounds": {
          "types": [
            "[\"electric\", \"electric\"]"
          ],
          "attack": [
            "[-inf.0, 50.0)"
          ]
        }
      }
    },
    "rejectedPlans": [ ]
  },
  "executionStats": {
    "executionSuccess": true,
    "nReturned": 8,
    "executionTimeMillis": 0,
    "totalKeysExamined": 8,
    "totalDocsExamined": 8,
    "executionStages": {
      "stage": "FETCH",
      "nReturned": 8,
      "executionTimeMillisEstimate": 0,
      "works": 9,
      "advanced": 8,
      "needTime": 0,
      "needYield": 0,
      "saveState": 0,
      "restoreState": 0,
      "isEOF": 1,
      "invalidates": 0,
      "docsExamined": 8,
      "alreadyHasObj": 0,
      "inputStage": {
        "stage": "IXSCAN",
        "nReturned": 8,
        "executionTimeMillisEstimate": 0,
        "works": 9,
        "advanced": 8,
        "needTime": 0,
        "needYield": 0,
        "saveState": 0,
        "restoreState": 0,
        "isEOF": 1,
        "invalidates": 0,
        "keyPattern": {
          "types": 1,
          "attack": 1
        },
        "indexName": "types_1_attack_1",
        "isMultiKey": true,
        "isUnique": false,
        "isSparse": false,
        "isPartial": false,
        "indexVersion": 1,
        "direction": "forward",
        "indexBounds": {
          "types": [
            "[\"electric\", \"electric\"]"
          ],
          "attack": [
            "[-inf.0, 50.0)"
          ]
        },
        "keysExamined": 8,
        "dupsTested": 8,
        "dupsDropped": 0,
        "seenInvalidated": 0
      }
    }
  },
  "serverInfo": {
    "host": "MBP-de-Leonardo",
    "port": 27017,
    "version": "3.2.1",
    "gitVersion": "a14d55980c2cdc565d4704a7e3ad37e4e535c1b2"
  },
  "ok": 1
}
```