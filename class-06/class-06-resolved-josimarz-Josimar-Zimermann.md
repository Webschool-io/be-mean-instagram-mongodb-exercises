# MongoDB - Aula 06 - Exercício
**Autor**: Josimar Zimermann - [josimarz](https://github.com/josimarz)

## 1 - Executar `explain` para uma consulta sobre o atributo `name` da coleção `pokemons`.

```js
var query = {
... name: "Marowak"
... }
db.pokemons.find(query).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "name": {
        "$eq": "Marowak"
      }
    },
    "winningPlan": {
      "stage": "COLLSCAN",
      "filter": {
        "name": {
          "$eq": "Marowak"
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
          "$eq": "Marowak"
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
    "host": "nightwolf",
    "port": 27017,
    "version": "3.2.1",
    "gitVersion": "a14d55980c2cdc565d4704a7e3ad37e4e535c1b2"
  },
  "ok": 1
}
```

## 2 - Criar um índice para o atributo `name` na coleção `pokemons`.

```js
db.pokemons.createIndex({
... name: 1
... })
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}
```

## 3 - Executar `explain` para uma consulta sobre o atributo `name` da coleção `pokemons` após criar o índice.

```js
var query = {
... name: "Marowak"
... }
db.pokemons.find(query).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "name": {
        "$eq": "Marowak"
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
            "[\"Marowak\", \"Marowak\"]"
          ]
        }
      }
    },
    "rejectedPlans": [ ]
  },
  "executionStats": {
    "executionSuccess": true,
    "nReturned": 0,
    "executionTimeMillis": 1,
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
            "[\"Marowak\", \"Marowak\"]"
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
    "host": "nightwolf",
    "port": 27017,
    "version": "3.2.1",
    "gitVersion": "a14d55980c2cdc565d4704a7e3ad37e4e535c1b2"
  },
  "ok": 1
}
```

## 4 - Executar `explain` para uma consulta sobre dois campos na coleção `pokemons`.

```js
var query = {
... attack: {$gt: 70},
... defense: {$lt: 50}
... }
db.pokemons.find(query).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "defense": {
            "$lt": 50
          }
        },
        {
          "attack": {
            "$gt": 70
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
              "$lt": 50
            }
          },
          {
            "attack": {
              "$gt": 70
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
    "nReturned": 23,
    "executionTimeMillis": 0,
    "totalKeysExamined": 0,
    "totalDocsExamined": 610,
    "executionStages": {
      "stage": "COLLSCAN",
      "filter": {
        "$and": [
          {
            "defense": {
              "$lt": 50
            }
          },
          {
            "attack": {
              "$gt": 70
            }
          }
        ]
      },
      "nReturned": 23,
      "executionTimeMillisEstimate": 0,
      "works": 612,
      "advanced": 23,
      "needTime": 588,
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
    "host": "nightwolf",
    "port": 27017,
    "version": "3.2.1",
    "gitVersion": "a14d55980c2cdc565d4704a7e3ad37e4e535c1b2"
  },
  "ok": 1
}
```

## 5 - Criar índice para as duas propriedades consultadas no passo anterior.

```js
db.pokemons.createIndex({
... attack: 1,
... defense: 1
... }
... )
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 2,
  "numIndexesAfter": 3,
  "ok": 1
}
```

## 6 - Executar `explain` numa consulta sobre os dois campos indexados no passo anterior.

```js
var query = {
... attack: {$gt: 70},
... defense: {$lt: 50}
... }
db.pokemons.find(query).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "defense": {
            "$lt": 50
          }
        },
        {
          "attack": {
            "$gt": 70
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
            "(70.0, inf.0]"
          ],
          "defense": [
            "[-inf.0, 50.0)"
          ]
        }
      }
    },
    "rejectedPlans": [ ]
  },
  "executionStats": {
    "executionSuccess": true,
    "nReturned": 23,
    "executionTimeMillis": 1,
    "totalKeysExamined": 77,
    "totalDocsExamined": 23,
    "executionStages": {
      "stage": "FETCH",
      "nReturned": 23,
      "executionTimeMillisEstimate": 0,
      "works": 78,
      "advanced": 23,
      "needTime": 54,
      "needYield": 0,
      "saveState": 0,
      "restoreState": 0,
      "isEOF": 1,
      "invalidates": 0,
      "docsExamined": 23,
      "alreadyHasObj": 0,
      "inputStage": {
        "stage": "IXSCAN",
        "nReturned": 23,
        "executionTimeMillisEstimate": 0,
        "works": 78,
        "advanced": 23,
        "needTime": 54,
        "needYield": 0,
        "saveState": 0,
        "restoreState": 0,
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
            "(70.0, inf.0]"
          ],
          "defense": [
            "[-inf.0, 50.0)"
          ]
        },
        "keysExamined": 77,
        "dupsTested": 0,
        "dupsDropped": 0,
        "seenInvalidated": 0
      }
    }
  },
  "serverInfo": {
    "host": "nightwolf",
    "port": 27017,
    "version": "3.2.1",
    "gitVersion": "a14d55980c2cdc565d4704a7e3ad37e4e535c1b2"
  },
  "ok": 1
}
```