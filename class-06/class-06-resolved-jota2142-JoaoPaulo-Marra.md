# MongoDB - Aula 06 - Exercício

Autor: João Paulo Costa Marra

## Find do campo "name" utilizando "explain"

```
Jota-PC(mongod-3.2.1) be-mean> db.pokemons.find({name: /charmander/i}).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "name": /charmander/i
    },
    "winningPlan": {
      "stage": "COLLSCAN",
      "filter": {
        "name": /charmander/i
      },
      "direction": "forward"
    },
    "rejectedPlans": [ ]
  },
  "executionStats": {
    "executionSuccess": true,
    "nReturned": 1,
    "executionTimeMillis": 26,
    "totalKeysExamined": 0,
    "totalDocsExamined": 610,
    "executionStages": {
      "stage": "COLLSCAN",
      "filter": {
        "name": /charmander/i
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
    "host": "Jota-PC",
    "port": 27017,
    "version": "3.2.1",
    "gitVersion": "a14d55980c2cdc565d4704a7e3ad37e4e535c1b2"
  },
  "ok": 1
}
```

## Criando índice para o "name"

```
Jota-PC(mongod-3.2.1) be-mean> db.pokemons.createIndex( { name: 1 } )
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}
```

## Find com o campo "name" indexado

```
Jota-PC(mongod-3.2.1) be-mean> db.pokemons.find({"name": "Charmander"}).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.pokemons",
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
        "isUnique": false,
        "isSparse": false,
        "isPartial": false,
        "indexVersion": 1,
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
    "executionTimeMillis": 33,
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
            "[\"Charmander\", \"Charmander\"]"
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
    "host": "Jota-PC",
    "port": 27017,
    "version": "3.2.1",
    "gitVersion": "a14d55980c2cdc565d4704a7e3ad37e4e535c1b2"
  },
  "ok": 1
}
```

## Criando index para dois campos

```
Jota-PC(mongod-3.2.1) be-mean> db.pokemons.createIndex({attack: 1, defense: 1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 2,
  "numIndexesAfter": 3,
  "ok": 1
}
```

## Resultado após serem indexados

```
Jota-PC(mongod-3.2.1) be-mean> db.pokemons.find({$and: [{"attack": {$gt: 40}, "defense": {$lte: 50}}]}).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "defense": {
            "$lte": 50
          }
        },
        {
          "attack": {
            "$gt": 40
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
          "defense": 1
        },
        "indexName": "attack_1_defense_1",
        "isMultiKey": false,
        "isUnique": false,
        "isSparse": false,
        "isPartial": false,
        "indexVersion": 1,
        "direction": "forward",
        "indexBounds": {
          "attack": [
            "(40.0, 1.#INF]"
          ],
          "defense": [
            "[-1.#INF, 50.0]"
          ]
        }
      }
    },
    "rejectedPlans": [ ]
  },
  "executionStats": {
    "executionSuccess": true,
    "nReturned": 123,
    "executionTimeMillis": 45,
    "totalKeysExamined": 199,
    "totalDocsExamined": 123,
    "executionStages": {
      "stage": "FETCH",
      "nReturned": 123,
      "executionTimeMillisEstimate": 10,
      "works": 200,
      "advanced": 123,
      "needTime": 76,
      "needYield": 0,
      "saveState": 1,
      "restoreState": 1,
      "isEOF": 1,
      "invalidates": 0,
      "docsExamined": 123,
      "alreadyHasObj": 0,
      "inputStage": {
        "stage": "IXSCAN",
        "nReturned": 123,
        "executionTimeMillisEstimate": 10,
        "works": 200,
        "advanced": 123,
        "needTime": 76,
        "needYield": 0,
        "saveState": 1,
        "restoreState": 1,
        "isEOF": 1,
        "invalidates": 0,
        "keyPattern": {
          "attack": 1,
          "defense": 1
        },
        "indexName": "attack_1_defense_1",
        "isMultiKey": false,
        "isUnique": false,
        "isSparse": false,
        "isPartial": false,
        "indexVersion": 1,
        "direction": "forward",
        "indexBounds": {
          "attack": [
            "(40.0, 1.#INF]"
          ],
          "defense": [
            "[-1.#INF, 50.0]"
          ]
        },
        "keysExamined": 199,
        "dupsTested": 0,
        "dupsDropped": 0,
        "seenInvalidated": 0
      }
    }
  },
  "serverInfo": {
    "host": "Jota-PC",
    "port": 27017,
    "version": "3.2.1",
    "gitVersion": "a14d55980c2cdc565d4704a7e3ad37e4e535c1b2"
  },
  "ok": 1
}
```
