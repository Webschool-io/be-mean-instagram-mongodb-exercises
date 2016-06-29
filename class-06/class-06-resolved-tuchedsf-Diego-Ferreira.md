#MongoDB - Aula 06 - Exercícios
autor: Diego Ferreira

##1. Fazer uma query para o campo `name` utilizando `explain` para ver o resultado da busca
```
Air-de-Diego(mongod-3.0.7) be-mean> var query = { name : "Wartortle"}
Air-de-Diego(mongod-3.0.7) be-mean> db.pokemons.find(query).explain()
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.pokemons",
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
  "serverInfo": {
    "host": "Air-de-Diego",
    "port": 27017,
    "version": "3.0.7",
    "gitVersion": "nogitversion"
  },
  "ok": 1
}


Air-de-Diego(mongod-3.0.7) be-mean> db.pokemons.find(query).explain('executionStats').executionStats
{
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
    "executionTimeMillisEstimate": 0,
    "works": 612,
    "advanced": 1,
    "needTime": 610,
    "needFetch": 0,
    "saveState": 4,
    "restoreState": 4,
    "isEOF": 1,
    "invalidates": 0,
    "direction": "forward",
    "docsExamined": 610
  }
}

```

##2. Criar um `index` um para o campo `name`
```

Air-de-Diego(mongod-3.0.7) be-mean> db.pokemons.getIndexes()
[
  {
    "v": 1,
    "key": {
      "_id": 1
    },
    "name": "_id_",
    "ns": "be-mean.pokemons"
  }
]

# Criação do index:

Air-de-Diego(mongod-3.0.7) be-mean> db.pokemons.createIndex({name : 1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}

#Indices apos criacao

Air-de-Diego(mongod-3.0.7) be-mean> db.pokemons.getIndexes()
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

##3. Refazer a query para o campo `name` utilizando `explain` para ver o resultado da busca
```
Air-de-Diego(mongod-3.0.7) be-mean> db.pokemons.find(query).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 1,
  "executionTimeMillis": 10,
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
          "[\"Wartortle\", \"Wartortle\"]"
        ]
      },
      "keysExamined": 1,
      "dupsTested": 0,
      "dupsDropped": 0,
      "seenInvalidated": 0,
      "matchTested": 0
    }
  }
}
```

##4. Fazer uma query para dois campos juntos utilizando `explain` para ver o resultado da busca
```
Air-de-Diego(mongod-3.0.7) be-mean> var query = { $and:[ { attack: { $gt: 50 } }, { defense: { $gt: 40 } } ] }
Air-de-Diego(mongod-3.0.7) be-mean> db.pokemons.find(query).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 428,
  "executionTimeMillis": 4,
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
            "$gt": 40
          }
        }
      ]
    },
    "nReturned": 428,
    "executionTimeMillisEstimate": 0,
    "works": 612,
    "advanced": 428,
    "needTime": 183,
    "needFetch": 0,
    "saveState": 4,
    "restoreState": 4,
    "isEOF": 1,
    "invalidates": 0,
    "direction": "forward",
    "docsExamined": 610
  }
}

```

##5. Criar um `index` para esses dois campos juntos
```
Air-de-Diego(mongod-3.0.7) be-mean> db.pokemons.createIndex({attack : 1, defense : 1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 2,
  "numIndexesAfter": 3,
  "ok": 1
}

```

##6. Refazer a query para os dois campos juntos utilizando `explain` para ver o resultado da busca
```
Air-de-Diego(mongod-3.0.7) be-mean> db.pokemons.find(query).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 428,
  "executionTimeMillis": 5,
  "totalKeysExamined": 444,
  "totalDocsExamined": 428,
  "executionStages": {
    "stage": "FETCH",
    "nReturned": 428,
    "executionTimeMillisEstimate": 0,
    "works": 445,
    "advanced": 428,
    "needTime": 16,
    "needFetch": 0,
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
      "works": 444,
      "advanced": 428,
      "needTime": 16,
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
          "(50.0, inf.0]"
        ],
        "defense": [
          "(40.0, inf.0]"
        ]
      },
      "keysExamined": 444,
      "dupsTested": 0,
      "dupsDropped": 0,
      "seenInvalidated": 0,
      "matchTested": 0
    }
  }
}
```
