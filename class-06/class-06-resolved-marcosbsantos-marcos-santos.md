##MongoDB -Aula06- Exercícios
##autor: MARCOS SANTOS

##1. Query para o campo name sem indice:

db.pokemons.find({name:{}}).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 0,
  "executionTimeMillis": 0,
  "totalKeysExamined": 0,
  "totalDocsExamined": 610,
  "executionStages": {
    "stage": "COLLSCAN",
    "filter": {
      "name": {
        "$eq": {
          
        }
      }
    },
    "nReturned": 0,
    "executionTimeMillisEstimate": 0,
    "works": 612,
    "advanced": 0,
    "needTime": 611,
    "needFetch": 0,
    "saveState": 4,
    "restoreState": 4,
    "isEOF": 1,
    "invalidates": 0,
    "direction": "forward",
    "docsExamined": 610
  }
}

##2. Criar um index para o campo name

db.pokemons.createIndex({name:1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}

##3. Query para o campo name com indice

 db.pokemons.find({name:{}}).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 0,
  "executionTimeMillis": 31,
  "totalKeysExamined": 0,
  "totalDocsExamined": 0,
  "executionStages": {
    "stage": "FETCH",
    "nReturned": 0,
    "executionTimeMillisEstimate": 0,
    "works": 1,
    "advanced": 0,
    "needTime": 0,
    "needFetch": 0,
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
          "[{}, {}]"
        ]
      },
      "keysExamined": 0,
      "dupsTested": 0,
      "dupsDropped": 0,
      "seenInvalidated": 0,
      "matchTested": 0
    }
  }
}

##4. Query para os dois campos sem indice

 db.pokemons.find({"attack": {$gte: 1}, "defense": {$lt: 100}}).explain('executionStats') 
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean-instagram.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "defense": {
            "$lt": 100
          }
        },
        {
          "attack": {
            "$gte": 1
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
              "$lt": 100
            }
          },
          {
            "attack": {
              "$gte": 1
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
    "nReturned": 501,
    "executionTimeMillis": 1,
    "totalKeysExamined": 0,
    "totalDocsExamined": 610,
    "executionStages": {
      "stage": "COLLSCAN",
      "filter": {
        "$and": [
          {
            "defense": {
              "$lt": 100
            }
          },
          {
            "attack": {
              "$gte": 1
            }
          }
        ]
      },
      "nReturned": 501,
      "executionTimeMillisEstimate": 0,
      "works": 612,
      "advanced": 501,
      "needTime": 110,
      "needFetch": 0,
      "saveState": 4,
      "restoreState": 4,
      "isEOF": 1,
      "invalidates": 0,
      "direction": "forward",
      "docsExamined": 610
    }
  },
  "serverInfo": {
    "host": "oncase",
    "port": 27017,
    "version": "3.0.7",
    "gitVersion": "6ce7cbe8c6b899552dadd907604559806aa2e9bd"
  },
  "ok": 1
}


##5. Criar indice para dois campos juntos

db.pokemons.createIndex({attack:1,defense:1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 2,
  "numIndexesAfter": 3,
  "ok": 1
}


##6. Query para os dois campos com indice

 db.pokemons.find({"attack": {$gte: 1}, "defense": {$lt: 100}}).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean-instagram.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "defense": {
            "$lt": 100
          }
        },
        {
          "attack": {
            "$gte": 1
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
            "[1.0, inf.0]"
          ],
          "defense": [
            "[-inf.0, 100.0)"
          ]
        }
      }
    },
    "rejectedPlans": [ ]
  },
  "executionStats": {
    "executionSuccess": true,
    "nReturned": 501,
    "executionTimeMillis": 2,
    "totalKeysExamined": 547,
    "totalDocsExamined": 501,
    "executionStages": {
      "stage": "FETCH",
      "nReturned": 501,
      "executionTimeMillisEstimate": 0,
      "works": 547,
      "advanced": 501,
      "needTime": 45,
      "needFetch": 0,
      "saveState": 4,
      "restoreState": 4,
      "isEOF": 1,
      "invalidates": 0,
      "docsExamined": 501,
      "alreadyHasObj": 0,
      "inputStage": {
        "stage": "IXSCAN",
        "nReturned": 501,
        "executionTimeMillisEstimate": 0,
        "works": 547,
        "advanced": 501,
        "needTime": 45,
        "needFetch": 0,
        "saveState": 4,
        "restoreState": 4,
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
            "[1.0, inf.0]"
          ],
          "defense": [
            "[-inf.0, 100.0)"
          ]
        },
        "keysExamined": 547,
        "dupsTested": 0,
        "dupsDropped": 0,
        "seenInvalidated": 0,
        "matchTested": 0
      }
    }
  },
  "serverInfo": {
    "host": "oncase",
    "port": 27017,
    "version": "3.0.7",
    "gitVersion": "6ce7cbe8c6b899552dadd907604559806aa2e9bd"
  },
  "ok": 1
}


 
