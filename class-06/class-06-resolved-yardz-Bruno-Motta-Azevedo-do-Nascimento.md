# MongoDB - Aula 06 - Exercício
autor: Bruno Motta Azevedo do Nascimento

**1** - Query para o campo `name` **sem** índice utilizando `explain` para ver o resultado da busca

```js
be-mean-pokemons> db.pokemons.getIndexes()
[
  {
    "v": 1,
    "key": {
      "_id": 1
    },
    "name": "_id_",
    "ns": "be-mean-pokemons.pokemons"
  }
]

be-mean-pokemons> db.pokemons.find({name:"Pikachu"}).explain('executionStats');
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean-pokemons.pokemons",
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
    "executionTimeMillis": 0,
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
    "host": "MacBook-Pro.local",
    "port": 27017,
    "version": "3.2.10",
    "gitVersion": "79d9b3ab5ce20f51c272b4411202710a082d0317"
  },
  "ok": 1
}
```

**2** - Criar um `índice` um para o campo `name`

```js
be-mean-pokemons> db.pokemons.createIndex({name:1});
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}


be-mean-restaurantes> be-mean-pokemons> db.pokemons.getIndexes();
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


```

**3** - Query para o campo `name` com `índice` utilizando `explain`

```js
db.pokemons.find({name:"Pikachu"}).explain('executionStats');
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean-pokemons.pokemons",
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
      "executionTimeMillisEstimate": 10,
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
    "host": "MacBook-Pro.local",
    "port": 27017,
    "version": "3.2.10",
    "gitVersion": "79d9b3ab5ce20f51c272b4411202710a082d0317"
  },
  "ok": 1
}

```

**4** - Query para dois campos **sem** `índice`

```js
be-mean-pokemons> db.pokemons.getIndexes()
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

be-mean-pokemons> db.pokemons.find({$and:[{defense:{$gte:40}},{attack:{$gte:55}}]}).explain('executionStats');
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean-pokemons.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "attack": {
            "$gte": 55
          }
        },
        {
          "defense": {
            "$gte": 40
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
              "$gte": 55
            }
          },
          {
            "defense": {
              "$gte": 40
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
    "nReturned": 428,
    "executionTimeMillis": 0,
    "totalKeysExamined": 0,
    "totalDocsExamined": 610,
    "executionStages": {
      "stage": "COLLSCAN",
      "filter": {
        "$and": [
          {
            "attack": {
              "$gte": 55
            }
          },
          {
            "defense": {
              "$gte": 40
            }
          }
        ]
      },
      "nReturned": 428,
      "executionTimeMillisEstimate": 0,
      "works": 612,
      "advanced": 428,
      "needTime": 183,
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
    "host": "MacBook-Pro.local",
    "port": 27017,
    "version": "3.2.10",
    "gitVersion": "79d9b3ab5ce20f51c272b4411202710a082d0317"
  },
  "ok": 1
}

```

**5** - Criar índice para `dois campos` juntos

```js
db.pokemons.createIndex({attack:1,defense:1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 2,
  "numIndexesAfter": 3,
  "ok": 1
}
be-mean-pokemons> db.pokemons.getIndexes();
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
      "attack": 1,
      "defense": 1
    },
    "name": "attack_1_defense_1",
    "ns": "be-mean-pokemons.pokemons"
  }
]

```

**6** - Query para os `dois campos` **com** índice

```js
be-mean-pokemons> db.pokemons.find({$and:[{defense:{$gte:40}},{attack:{$gte:55}}]}).explain('executionStats');
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean-pokemons.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "attack": {
            "$gte": 55
          }
        },
        {
          "defense": {
            "$gte": 40
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
            "[55.0, inf.0]"
          ],
          "defense": [
            "[40.0, inf.0]"
          ]
        }
      }
    },
    "rejectedPlans": [ ]
  },
  "executionStats": {
    "executionSuccess": true,
    "nReturned": 428,
    "executionTimeMillis": 1,
    "totalKeysExamined": 437,
    "totalDocsExamined": 428,
    "executionStages": {
      "stage": "FETCH",
      "nReturned": 428,
      "executionTimeMillisEstimate": 0,
      "works": 438,
      "advanced": 428,
      "needTime": 9,
      "needYield": 0,
      "saveState": 3,
      "restoreState": 3,
      "isEOF": 1,
      "invalidates": 0,
      "docsExamined": 428,
      "alreadyHasObj": 0,
      "inputStage": {
        "stage": "IXSCAN",
        "nReturned": 428,
        "executionTimeMillisEstimate": 0,
        "works": 438,
        "advanced": 428,
        "needTime": 9,
        "needYield": 0,
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
        "isUnique": false,
        "isSparse": false,
        "isPartial": false,
        "indexVersion": 1,
        "direction": "forward",
        "indexBounds": {
          "attack": [
            "[55.0, inf.0]"
          ],
          "defense": [
            "[40.0, inf.0]"
          ]
        },
        "keysExamined": 437,
        "dupsTested": 0,
        "dupsDropped": 0,
        "seenInvalidated": 0
      }
    }
  },
  "serverInfo": {
    "host": "MacBook-Pro.local",
    "port": 27017,
    "version": "3.2.10",
    "gitVersion": "79d9b3ab5ce20f51c272b4411202710a082d0317"
  },
  "ok": 1
}
```
