## MongoDb Aula - 06
Autor: Mário Mello

## 1. Fazer uma query por nome sem "indexização" utilzando o explain
```
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons> db.pokemons.find({name: "Wartortle"}).explain('executionStats');
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean-pokemons.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "name": {
        "$eq": "Wartortle"
      }
    },
    "winningPlan": {
      "stage": "COLLSCAN",
      "filter": {
        "name": {
          "$eq": "Wartortle"
        }
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
        "name": {
          "$eq": "Wartortle"
        }
      },
      "nReturned": 1,
      "executionTimeMillisEstimate": 10,
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
    "host": "macbook-mariosmello.home",
    "port": 27017,
    "version": "3.2.6",
    "gitVersion": "05552b562c7a0b3143a729aaa0838e558dc49b25"
  },
  "ok": 1
}
```

## 2. Criar um Index pelo nome e fazer uma query  utilzando o explain
```
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons> db.pokemons.createIndex({name: 1});
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons> db.pokemons.getIndexes()
[
  {
    "v": 1,
    "key": {
      "_id": 1
    },
    "name": "_id_",
    "ns": "be-mean-pokemons.pokemons"
  },
  {
    "v": 1,
    "key": {
      "name": 1
    },
    "name": "name_1",
    "ns": "be-mean-pokemons.pokemons"
  }
]
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons> db.pokemons.find({name: "Wartortle"}).explain('executionStats');
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean-pokemons.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "name": {
        "$eq": "Wartortle"
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
            "[\"Wartortle\", \"Wartortle\"]"
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
            "[\"Wartortle\", \"Wartortle\"]"
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
    "host": "macbook-mariosmello.home",
    "port": 27017,
    "version": "3.2.6",
    "gitVersion": "05552b562c7a0b3143a729aaa0838e558dc49b25"
  },
  "ok": 1
}
```

## 3. Fazer uma query de dois campos juntos sem "indexização" utilzando o explain
```
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons> db.pokemons.find({ $and: [ {attack: {$gt: 50}},  {defense: {$gt: 50}}  ] }).explain('executionStats');
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean-pokemons.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "attack": {
            "$gt": 50
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
              "$gt": 50
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
    "nReturned": 374,
    "executionTimeMillis": 0,
    "totalKeysExamined": 0,
    "totalDocsExamined": 610,
    "executionStages": {
      "stage": "COLLSCAN",
      "filter": {
        "$and": [
          {
            "attack": {
              "$gt": 50
            }
          },
          {
            "defense": {
              "$gt": 50
            }
          }
        ]
      },
      "nReturned": 374,
      "executionTimeMillisEstimate": 0,
      "works": 612,
      "advanced": 374,
      "needTime": 237,
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
    "host": "macbook-mariosmello.home",
    "port": 27017,
    "version": "3.2.6",
    "gitVersion": "05552b562c7a0b3143a729aaa0838e558dc49b25"
  },
  "ok": 1
}
```

## 4.  Fazer uma query pela index dupla criada,  utilzando o explain
```
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons> db.pokemons.createIndexes([{attack: 1}, {defense: 1}]);
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 2,
  "numIndexesAfter": 4,
  "ok": 1
}
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons> db.pokemons.getIndexes()
[
  {
    "v": 1,
    "key": {
      "_id": 1
    },
    "name": "_id_",
    "ns": "be-mean-pokemons.pokemons"
  },
  {
    "v": 1,
    "key": {
      "name": 1
    },
    "name": "name_1",
    "ns": "be-mean-pokemons.pokemons"
  },
  {
    "v": 1,
    "key": {
      "attack": 1
    },
    "name": "attack_1",
    "ns": "be-mean-pokemons.pokemons"
  },
  {
    "v": 1,
    "key": {
      "defense": 1
    },
    "name": "defense_1",
    "ns": "be-mean-pokemons.pokemons"
  }
]
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons> db.pokemons.find({ $and: [ {attack: {$gt: 50}},  {defense: {$gt: 50}}  ] }).explain('executionStats');
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean-pokemons.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "attack": {
            "$gt": 50
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
      "filter": {
        "attack": {
          "$gt": 50
        }
      },
      "inputStage": {
        "stage": "IXSCAN",
        "keyPattern": {
          "defense": 1
        },
        "indexName": "defense_1",
        "isMultiKey": false,
        "isUnique": false,
        "isSparse": false,
        "isPartial": false,
        "indexVersion": 1,
        "direction": "forward",
        "indexBounds": {
          "defense": [
            "(50.0, inf.0]"
          ]
        }
      }
    },
    "rejectedPlans": [
      {
        "stage": "FETCH",
        "filter": {
          "defense": {
            "$gt": 50
          }
        },
        "inputStage": {
          "stage": "IXSCAN",
          "keyPattern": {
            "attack": 1
          },
          "indexName": "attack_1",
          "isMultiKey": false,
          "isUnique": false,
          "isSparse": false,
          "isPartial": false,
          "indexVersion": 1,
          "direction": "forward",
          "indexBounds": {
            "attack": [
              "(50.0, inf.0]"
            ]
          }
        }
      }
    ]
  },
  "executionStats": {
    "executionSuccess": true,
    "nReturned": 374,
    "executionTimeMillis": 2,
    "totalKeysExamined": 435,
    "totalDocsExamined": 435,
    "executionStages": {
      "stage": "FETCH",
      "filter": {
        "attack": {
          "$gt": 50
        }
      },
      "nReturned": 374,
      "executionTimeMillisEstimate": 0,
      "works": 436,
      "advanced": 374,
      "needTime": 61,
      "needYield": 0,
      "saveState": 5,
      "restoreState": 5,
      "isEOF": 1,
      "invalidates": 0,
      "docsExamined": 435,
      "alreadyHasObj": 0,
      "inputStage": {
        "stage": "IXSCAN",
        "nReturned": 435,
        "executionTimeMillisEstimate": 0,
        "works": 436,
        "advanced": 435,
        "needTime": 0,
        "needYield": 0,
        "saveState": 5,
        "restoreState": 5,
        "isEOF": 1,
        "invalidates": 0,
        "keyPattern": {
          "defense": 1
        },
        "indexName": "defense_1",
        "isMultiKey": false,
        "isUnique": false,
        "isSparse": false,
        "isPartial": false,
        "indexVersion": 1,
        "direction": "forward",
        "indexBounds": {
          "defense": [
            "(50.0, inf.0]"
          ]
        },
        "keysExamined": 435,
        "dupsTested": 0,
        "dupsDropped": 0,
        "seenInvalidated": 0
      }
    }
  },
  "serverInfo": {
    "host": "macbook-mariosmello.home",
    "port": 27017,
    "version": "3.2.6",
    "gitVersion": "05552b562c7a0b3143a729aaa0838e558dc49b25"
  },
  "ok": 1
}
```
