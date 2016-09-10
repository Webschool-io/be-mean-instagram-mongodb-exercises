# MongoDB - Aula 06 - Exercício
autor: Leonardo Gonçalves de Souza

## Fazer uma query para o campo `name` utilizando `explain` para ver o resultado da busca.
```
Leonardo-PC(d:\mongodb\bin\mongod.exe-3.0.5) be-mean> query
{
  "name": /Charmander/i
}
Leonardo-PC(d:\mongodb\bin\mongod.exe-3.0.5) be-mean> db.pokemons.find(query).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 0,
  "executionTimeMillis": 1,
  "totalKeysExamined": 0,
  "totalDocsExamined": 618,
  "executionStages": {
    "stage": "COLLSCAN",
    "filter": {
      "name": {
        "$eq": /Charmander/i
      }
    },
    "nReturned": 0,
    "executionTimeMillisEstimate": 0,
    "works": 620,
    "advanced": 0,
    "needTime": 619,
    "needFetch": 0,
    "saveState": 4,
    "restoreState": 4,
    "isEOF": 1,
    "invalidates": 0,
    "direction": "forward",
    "docsExamined": 618
  }
}
```

## Criar um `index` um para o campo `name`.
```
Leonardo-PC(d:\mongodb\bin\mongod.exe-3.0.5) be-mean> db.pokemons.createIndex({name: 1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}
Leonardo-PC(d:\mongodb\bin\mongod.exe-3.0.5) be-mean> db.pokemons.getIndexes()
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

## Refazer a query para o campo `name` utilizando `explain` para ver o resultado da busca.
```
Leonardo-PC(d:\mongodb\bin\mongod.exe-3.0.5) be-mean> db.pokemons.find(query).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 1,
  "executionTimeMillis": 2,
  "totalKeysExamined": 618,
  "totalDocsExamined": 1,
  "executionStages": {
    "stage": "FETCH",
    "nReturned": 1,
    "executionTimeMillisEstimate": 0,
    "works": 619,
    "advanced": 1,
    "needTime": 617,
    "needFetch": 0,
    "saveState": 4,
    "restoreState": 4,
    "isEOF": 1,
    "invalidates": 0,
    "docsExamined": 1,
    "alreadyHasObj": 0,
    "inputStage": {
      "stage": "IXSCAN",
      "filter": {
        "name": /Charmander/i
      },
      "nReturned": 1,
      "executionTimeMillisEstimate": 0,
      "works": 618,
      "advanced": 1,
      "needTime": 617,
      "needFetch": 0,
      "saveState": 4,
      "restoreState": 4,
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
          "[\"\", {})",
          "[/Charmander/i, /Charmander/i]"
        ]
      },
      "keysExamined": 618,
      "dupsTested": 0,
      "dupsDropped": 0,
      "seenInvalidated": 0,
      "matchTested": 1
    }
  }
}
```

## Fazer uma query para dois campos juntos utilizando `explain` para ver o resultado da busca.
```
Leonardo-PC(d:\mongodb\bin\mongod.exe-3.0.5) be-mean> db.pokemons.find(query).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 542,
  "executionTimeMillis": 0,
  "totalKeysExamined": 0,
  "totalDocsExamined": 618,
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
            "$gt": 25
          }
        }
      ]
    },
    "nReturned": 542,
    "executionTimeMillisEstimate": 0,
    "works": 620,
    "advanced": 542,
    "needTime": 77,
    "needFetch": 0,
    "saveState": 4,
    "restoreState": 4,
    "isEOF": 1,
    "invalidates": 0,
    "direction": "forward",
    "docsExamined": 618
  }
}
```

## Criar um `index` para esses dois campos juntos.
```
Leonardo-PC(d:\mongodb\bin\mongod.exe-3.0.5) be-mean> db.pokemons.createIndex({attack: 1, defense: 1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 2,
  "numIndexesAfter": 3,
  "ok": 1
}
```

## Refazer a query para os dois campos juntos utilizando `explain` para ver o resultado da busca.
```
Leonardo-PC(d:\mongodb\bin\mongod.exe-3.0.5) be-mean> db.pokemons.find(query).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 542,
  "executionTimeMillis": 2,
  "totalKeysExamined": 546,
  "totalDocsExamined": 542,
  "executionStages": {
    "stage": "FETCH",
    "nReturned": 542,
    "executionTimeMillisEstimate": 0,
    "works": 547,
    "advanced": 542,
    "needTime": 4,
    "needFetch": 0,
    "saveState": 4,
    "restoreState": 4,
    "isEOF": 1,
    "invalidates": 0,
    "docsExamined": 542,
    "alreadyHasObj": 0,
    "inputStage": {
      "stage": "IXSCAN",
      "nReturned": 542,
      "executionTimeMillisEstimate": 0,
      "works": 546,
      "advanced": 542,
      "needTime": 4,
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
          "(40.0, 1.#INF]"
        ],
        "defense": [
          "(25.0, 1.#INF]"
        ]
      },
      "keysExamined": 546,
      "dupsTested": 0,
      "dupsDropped": 0,
      "seenInvalidated": 0,
      "matchTested": 0
    }
  }
}
```
