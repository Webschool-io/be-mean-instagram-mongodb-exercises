# MongoDB - Aula 06 - Exercício
autor: João Paulo Ribeiro

Utilizando a coleção de pokemons no Banco de Dados be-mean.

## 1. Criar index para o campo 'name'

  ```
  joao-Inspiron-5437(mongod-3.0.7) be-mean> db.pokemons.createIndex({name:1})
  {
    "createdCollectionAutomatically": false,
    "numIndexesBefore": 1,
    "numIndexesAfter": 2,
    "ok": 1
  }

  joao-Inspiron-5437(mongod-3.0.7) be-mean> db.pokemons.getIndexes()
  [
    {
      "v": 1,
      "key": {
        "_id": 1
      },
      "name": "_id_",
      "ns": "be-mean.pokemons"
    },
    {
      "v": 1,
      "key": {
        "name": 1
      },
      "name": "name_1",
      "ns": "be-mean.pokemons"
    }
  ]
  ```

## 2. Criar index para dois campos juntos

  ```
  joao-Inspiron-5437(mongod-3.0.7) be-mean> db.pokemons.createIndex({attack:-1,defense:-1})
  {
    "createdCollectionAutomatically": false,
    "numIndexesBefore": 2,
    "numIndexesAfter": 3,
    "ok": 1
  }

  joao-Inspiron-5437(mongod-3.0.7) be-mean> db.pokemons.getIndexes()
  [
    {
      "v": 1,
      "key": {
        "_id": 1
      },
      "name": "_id_",
      "ns": "be-mean.pokemons"
    },
    {
      "v": 1,
      "key": {
        "name": 1
      },
      "name": "name_1",
      "ns": "be-mean.pokemons"
    },
    {
      "v": 1,
      "key": {
        "attack": -1,
        "defense": -1
      },
      "name": "attack_-1_defense_-1",
      "ns": "be-mean.pokemons"
    }
  ]

  ```
## 3. Buscar com uma query com index campo "name" e uma query sem index com campo "name"

### Com Index
  ```
  joao-Inspiron-5437(mongod-3.0.7) be-mean> db.pokemons.find({name:'Pidgey'}).explain('executionStats')
  {
    "queryPlanner": {
      "plannerVersion": 1,
      "namespace": "be-mean.pokemons",
      "indexFilterSet": false,
      "parsedQuery": {
        "name": {
          "$eq": "Pidgey"
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
              "[\"Pidgey\", \"Pidgey\"]"
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
              "[\"Pidgey\", \"Pidgey\"]"
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
      "host": "joao-Inspiron-5437",
      "port": 27017,
      "version": "3.0.7",
      "gitVersion": "6ce7cbe8c6b899552dadd907604559806aa2e9bd"
    },
    "ok": 1
  }
  ```
### Sem Index
  ```
  joao-Inspiron-5437(mongod-3.0.7) be-mean> db.pokemons.find({name:'Pidgey'}).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "name": {
        "$eq": "Pidgey"
      }
    },
    "winningPlan": {
      "stage": "COLLSCAN",
      "filter": {
        "name": {
          "$eq": "Pidgey"
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
    "totalDocsExamined": 620,
    "executionStages": {
      "stage": "COLLSCAN",
      "filter": {
        "name": {
          "$eq": "Pidgey"
        }
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
    "host": "joao-Inspiron-5437",
    "port": 27017,
    "version": "3.0.7",
    "gitVersion": "6ce7cbe8c6b899552dadd907604559806aa2e9bd"
  },
  "ok": 1
}

  ```

## 4. Buscar com uma query com index para os campos escolhidos e com uma query sem index para os campos escolhidos

### Com index
  ```
  joao-Inspiron-5437(mongod-3.0.7) be-mean> db.pokemons.find({attack:45,defense:40}).explain('executionStats')
  {
    "queryPlanner": {
      "plannerVersion": 1,
      "namespace": "be-mean.pokemons",
      "indexFilterSet": false,
      "parsedQuery": {
        "$and": [
          {
            "attack": {
              "$eq": 45
            }
          },
          {
            "defense": {
              "$eq": 40
            }
          }
        ]
      },
      "winningPlan": {
        "stage": "FETCH",
        "inputStage": {
          "stage": "IXSCAN",
          "keyPattern": {
            "attack": -1,
            "defense": -1
          },
          "indexName": "attack_-1_defense_-1",
          "isMultiKey": false,
          "direction": "forward",
          "indexBounds": {
            "attack": [
              "[45.0, 45.0]"
            ],
            "defense": [
              "[40.0, 40.0]"
            ]
          }
        }
      },
      "rejectedPlans": [ ]
    },
    "executionStats": {
      "executionSuccess": true,
      "nReturned": 4,
      "executionTimeMillis": 0,
      "totalKeysExamined": 4,
      "totalDocsExamined": 4,
      "executionStages": {
        "stage": "FETCH",
        "nReturned": 4,
        "executionTimeMillisEstimate": 0,
        "works": 5,
        "advanced": 4,
        "needTime": 0,
        "needFetch": 0,
        "saveState": 0,
        "restoreState": 0,
        "isEOF": 1,
        "invalidates": 0,
        "docsExamined": 4,
        "alreadyHasObj": 0,
        "inputStage": {
          "stage": "IXSCAN",
          "nReturned": 4,
          "executionTimeMillisEstimate": 0,
          "works": 5,
          "advanced": 4,
          "needTime": 0,
          "needFetch": 0,
          "saveState": 0,
          "restoreState": 0,
          "isEOF": 1,
          "invalidates": 0,
          "keyPattern": {
            "attack": -1,
            "defense": -1
          },
          "indexName": "attack_-1_defense_-1",
          "isMultiKey": false,
          "direction": "forward",
          "indexBounds": {
            "attack": [
              "[45.0, 45.0]"
            ],
            "defense": [
              "[40.0, 40.0]"
            ]
          },
          "keysExamined": 4,
          "dupsTested": 0,
          "dupsDropped": 0,
          "seenInvalidated": 0,
          "matchTested": 0
        }
      }
    },
    "serverInfo": {
      "host": "joao-Inspiron-5437",
      "port": 27017,
      "version": "3.0.7",
      "gitVersion": "6ce7cbe8c6b899552dadd907604559806aa2e9bd"
    },
    "ok": 1
  }

  ```
### Sem index
  ```
  joao-Inspiron-5437(mongod-3.0.7) be-mean> db.pokemons.find({attack:45,defense:40}).explain('executionStats')
  {
    "queryPlanner": {
      "plannerVersion": 1,
      "namespace": "be-mean.pokemons",
      "indexFilterSet": false,
      "parsedQuery": {
        "$and": [
          {
            "attack": {
              "$eq": 45
            }
          },
          {
            "defense": {
              "$eq": 40
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
                "$eq": 45
              }
            },
            {
              "defense": {
                "$eq": 40
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
      "nReturned": 4,
      "executionTimeMillis": 0,
      "totalKeysExamined": 0,
      "totalDocsExamined": 620,
      "executionStages": {
        "stage": "COLLSCAN",
        "filter": {
          "$and": [
            {
              "attack": {
                "$eq": 45
              }
            },
            {
              "defense": {
                "$eq": 40
              }
            }
          ]
        },
        "nReturned": 4,
        "executionTimeMillisEstimate": 0,
        "works": 622,
        "advanced": 4,
        "needTime": 617,
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
      "host": "joao-Inspiron-5437",
      "port": 27017,
      "version": "3.0.7",
      "gitVersion": "6ce7cbe8c6b899552dadd907604559806aa2e9bd"
    },
    "ok": 1
  }

  ```
