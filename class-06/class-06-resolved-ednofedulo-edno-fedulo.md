# MongoDB - Aula 06 - Exercício
**autor**: Edno Fedulo

# 1. Fazer uma query para o campo name utilizando explain para ver o resultado da busca
```js
asus-K46CM(mongod-3.2.1) be-mean> db.pokemons.find({name:"Pikachu"}).explain("executionStats")
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "name": {
        "$eq": "Pikachu"
      }
    },
    "winningPlan": {
      "stage": "COLLSCAN",
      "filter": {
        "name": {
          "$eq": "Pikachu"
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
          "$eq": "Pikachu"
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
    "host": "asus-K46CM",
    "port": 27017,
    "version": "3.2.1",
    "gitVersion": "a14d55980c2cdc565d4704a7e3ad37e4e535c1b2"
  },
  "ok": 1
}
```
# 2. Criar um index um para o campo name

```js
asus-K46CM(mongod-3.2.1) be-mean> db.pokemons.createIndex({name:1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}
```
#3. Refazer a query para o campo name utilizando explain para ver o resultado da busca

```js
asus-K46CM(mongod-3.2.1) be-mean> db.pokemons.find({name:"Pikachu"}).explain("executionStats")
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "name": {
        "$eq": "Pikachu"
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
            "[\"Pikachu\", \"Pikachu\"]"
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
            "[\"Pikachu\", \"Pikachu\"]"
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
    "host": "asus-K46CM",
    "port": 27017,
    "version": "3.2.1",
    "gitVersion": "a14d55980c2cdc565d4704a7e3ad37e4e535c1b2"
  },
  "ok": 1
}
```
#4. Fazer uma query para dois campos juntos utilizando explain para ver o resultado da busca

```js
asus-K46CM(mongod-3.2.1) be-mean> db.pokemons.find({$and:[{attack: {$gt: 50}},{hp: {$lt:40}}]}).explain("executionStats")
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "hp": {
            "$lt": 40
          }
        },
        {
          "attack": {
            "$gt": 50
          }
        }
      ]
    },
    "winningPlan": {
      "stage": "COLLSCAN",
      "filter": {
        "$and": [
          {
            "hp": {
              "$lt": 40
            }
          },
          {
            "attack": {
              "$gt": 50
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
    "nReturned": 17,
    "executionTimeMillis": 1,
    "totalKeysExamined": 0,
    "totalDocsExamined": 610,
    "executionStages": {
      "stage": "COLLSCAN",
      "filter": {
        "$and": [
          {
            "hp": {
              "$lt": 40
            }
          },
          {
            "attack": {
              "$gt": 50
            }
          }
        ]
      },
      "nReturned": 17,
      "executionTimeMillisEstimate": 0,
      "works": 612,
      "advanced": 17,
      "needTime": 594,
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
    "host": "asus-K46CM",
    "port": 27017,
    "version": "3.2.1",
    "gitVersion": "a14d55980c2cdc565d4704a7e3ad37e4e535c1b2"
  },
  "ok": 1
}
```
#5. Criar um index para esses dois campos juntos

```js
asus-K46CM(mongod-3.2.1) be-mean> db.pokemons.createIndex({hp: 1, attack: 1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 2,
  "numIndexesAfter": 3,
  "ok": 1
}
```
#6. Refazer a query para os dois campos juntos utilizando explain para ver o resultado da busca
```js
asus-K46CM(mongod-3.2.1) be-mean> db.pokemons.find({$and:[{attack: {$gt: 50}},{hp: {$lt:40}}]}).explain("executionStats")
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "hp": {
            "$lt": 40
          }
        },
        {
          "attack": {
            "$gt": 50
          }
        }
      ]
    },
    "winningPlan": {
      "stage": "FETCH",
      "inputStage": {
        "stage": "IXSCAN",
        "keyPattern": {
          "hp": 1,
          "attack": 1
        },
        "indexName": "hp_1_attack_1",
        "isMultiKey": false,
        "isUnique": false,
        "isSparse": false,
        "isPartial": false,
        "indexVersion": 1,
        "direction": "forward",
        "indexBounds": {
          "hp": [
            "[-inf.0, 40.0)"
          ],
          "attack": [
            "(50.0, inf.0]"
          ]
        }
      }
    },
    "rejectedPlans": [ ]
  },
  "executionStats": {
    "executionSuccess": true,
    "nReturned": 17,
    "executionTimeMillis": 1,
    "totalKeysExamined": 26,
    "totalDocsExamined": 17,
    "executionStages": {
      "stage": "FETCH",
      "nReturned": 17,
      "executionTimeMillisEstimate": 0,
      "works": 26,
      "advanced": 17,
      "needTime": 8,
      "needYield": 0,
      "saveState": 0,
      "restoreState": 0,
      "isEOF": 1,
      "invalidates": 0,
      "docsExamined": 17,
      "alreadyHasObj": 0,
      "inputStage": {
        "stage": "IXSCAN",
        "nReturned": 17,
        "executionTimeMillisEstimate": 0,
        "works": 26,
        "advanced": 17,
        "needTime": 8,
        "needYield": 0,
        "saveState": 0,
        "restoreState": 0,
        "isEOF": 1,
        "invalidates": 0,
        "keyPattern": {
          "hp": 1,
          "attack": 1
        },
        "indexName": "hp_1_attack_1",
        "isMultiKey": false,
        "isUnique": false,
        "isSparse": false,
        "isPartial": false,
        "indexVersion": 1,
        "direction": "forward",
        "indexBounds": {
          "hp": [
            "[-inf.0, 40.0)"
          ],
          "attack": [
            "(50.0, inf.0]"
          ]
        },
        "keysExamined": 26,
        "dupsTested": 0,
        "dupsDropped": 0,
        "seenInvalidated": 0
      }
    }
  },
  "serverInfo": {
    "host": "asus-K46CM",
    "port": 27017,
    "version": "3.2.1",
    "gitVersion": "a14d55980c2cdc565d4704a7e3ad37e4e535c1b2"
  },
  "ok": 1
}
```