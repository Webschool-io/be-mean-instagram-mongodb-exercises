# MongoDB - Aula 06 - Exercício
autor: [Michel Ferreira Souza](https://github.com/souzacristsf)

## 1. Fazer uma query para o campo `name` utilizando explain para ver o resultado da busca

**Resultado da consulta sem index**

```
Souza(mongod-3.0.8) be-mean> db.pokemons.count()
620

Souza(mongod-3.0.8) be-mean> db.pokemons.find({ name: /Pidgeotto/i }).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "name": /Pidgeotto/i
    },
    "winningPlan": {
      "stage": "COLLSCAN",
      "filter": {
        "name": /Pidgeotto/i
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
    "totalDocsExamined": 620,
    "executionStages": {
      "stage": "COLLSCAN",
      "filter": {
        "name": /Pidgeotto/i
      },
      "nReturned": 1,
      "executionTimeMillisEstimate": 0,
      "works": 622,
      "advanced": 1,
      "needTime": 620,
      "needFetch": 0,
      "saveState": 4,
      "restoreState": 4,
      "isEOF": 1,
      "invalidates": 0,
      "direction": "forward",
      "docsExamined": 620
    }
  },
  "serverInfo": {
    "host": "Souza",
    "port": 27017,
    "version": "3.0.8",
    "gitVersion": "83d8cc25e00e42856924d84e220fbe4a839e605d"
  },
  "ok": 1
}

```

**Resultado da consulta com index**

```
Souza(mongod-3.0.8) be-mean> db.pokemons.find({ name: "Pidgeotto" }).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "name": {
        "$eq": "Pidgeotto"
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
            "[\"Pidgeotto\", \"Pidgeotto\"]"
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
            "[\"Pidgeotto\", \"Pidgeotto\"]"
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
    "host": "Souza",
    "port": 27017,
    "version": "3.0.8",
    "gitVersion": "83d8cc25e00e42856924d84e220fbe4a839e605d"
  },
  "ok": 1
}

```
## 2. Criar um index um para o campo `name`

```
Souza(mongod-3.0.8) be-mean> db.pokemons.createIndex({name: 1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}
Souza(mongod-3.0.8) be-mean> db.system.indexes.find()
{
  "v": 1,
  "key": {
    "_id": 1
  },
  "name": "_id_",
  "ns": "be-mean.restaurantes"
}
{
  "v": 1,
  "key": {
    "_id": 1
  },
  "name": "_id_",
  "ns": "be-mean.pokemons"
}
{
  "v": 1,
  "key": {
    "name": 1
  },
  "name": "name_1",
  "ns": "be-mean.pokemons"
}
Fetched 3 record(s) in 1ms

```


db.pokemons.createIndex({ name: 1 })
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}

## 3. Refazer a query para o campo `name` utilizando `explain` para ver o resultado da busca

```
Souza(mongod-3.0.8) be-mean> db.pokemons.find({ name: "Pidgeotto" }).explain('executionStats').executionStats.totalDocsExamined
1
Souza(mongod-3.0.8) be-mean> db.pokemons.find({ name: "Pidgeotto" }).explain('executionStats').executionStats.executionTimeMillis
0

```

## 4. Fazer uma query para `dois` campos juntos utilizando `explain` para ver o resultado da busca

```
Souza(mongod-3.0.8) be-mean> db.pokemons.find({$and: [{attack: {$gt: 40}},{defense: {$gt: 50}}]}).explain('executionStats').executionStats.totalDocsExamined
620
Souza(mongod-3.0.8) be-mean> db.pokemons.find({$and: [{attack: {$gt: 40}},{defense: {$gt: 50}}]}).explain('executionStats').executionStats.executionTimeMillis
0


Souza(mongod-3.0.8) be-mean> db.pokemons.find({$and: [{attack: {$gt: 40}},{defense: {$gt: 50}}]}).explain('executionStats')
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
            "attack": {
              "$gt": 40
            }
          },
          {
            "defense": {
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
    "nReturned": 421,
    "executionTimeMillis": 0,
    "totalKeysExamined": 0,
    "totalDocsExamined": 620,
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
              "$gt": 50
            }
          }
        ]
      },
      "nReturned": 421,
      "executionTimeMillisEstimate": 0,
      "works": 622,
      "advanced": 421,
      "needTime": 200,
      "needFetch": 0,
      "saveState": 4,
      "restoreState": 4,
      "isEOF": 1,
      "invalidates": 0,
      "direction": "forward",
      "docsExamined": 620
    }
  },
  "serverInfo": {
    "host": "Souza",
    "port": 27017,
    "version": "3.0.8",
    "gitVersion": "83d8cc25e00e42856924d84e220fbe4a839e605d"
  },
  "ok": 1
}

```

## 5. Criar um `index` para esses `dois` campos juntos

```
Souza(mongod-3.0.8) be-mean> db.pokemons.createIndex({attack: 1, defense: 1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 2,
  "numIndexesAfter": 3,
  "ok": 1
}


```

## 6. Refazer a query para os `dois` campos juntos utilizando `explain` para ver o resultado da busca

```
Souza(mongod-3.0.8) be-mean> db.pokemons.find({$and: [{attack: {$gt: 40}},{defense: {$gt: 50}}]}).explain('executionStats')
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
          "attack": 1,
          "defense": 1
        },
        "indexName": "attack_1_defense_1",
        "isMultiKey": false,
        "direction": "forward",
        "indexBounds": {
          "attack": [
            "(40.0, inf.0]"
          ],
          "defense": [
            "(50.0, inf.0]"
          ]
        }
      }
    },
    "rejectedPlans": [ ]
  },
  "executionStats": {
    "executionSuccess": true,
    "nReturned": 421,
    "executionTimeMillis": 1,
    "totalKeysExamined": 455,
    "totalDocsExamined": 421,
    "executionStages": {
      "stage": "FETCH",
      "nReturned": 421,
      "executionTimeMillisEstimate": 0,
      "works": 456,
      "advanced": 421,
      "needTime": 34,
      "needFetch": 0,
      "saveState": 3,
      "restoreState": 3,
      "isEOF": 1,
      "invalidates": 0,
      "docsExamined": 421,
      "alreadyHasObj": 0,
      "inputStage": {
        "stage": "IXSCAN",
        "nReturned": 421,
        "executionTimeMillisEstimate": 0,
        "works": 455,
        "advanced": 421,
        "needTime": 34,
        "needFetch": 0,
        "saveState": 3,
        "restoreState": 3,
        "isEOF": 1,
        "invalidates": 0,
        "keyPattern": {
          "attack": 1,
          "defense": 1
        },
        "indexName": "attack_1_defense_1",
        "isMultiKey": false,
        "direction": "forward",
        "indexBounds": {
          "attack": [
            "(40.0, inf.0]"
          ],
          "defense": [
            "(50.0, inf.0]"
          ]
        },
        "keysExamined": 455,
        "dupsTested": 0,
        "dupsDropped": 0,
        "seenInvalidated": 0,
        "matchTested": 0
      }
    }
  },
  "serverInfo": {
    "host": "Souza",
    "port": 27017,
    "version": "3.0.8",
    "gitVersion": "83d8cc25e00e42856924d84e220fbe4a839e605d"
  },
  "ok": 1
}


```

