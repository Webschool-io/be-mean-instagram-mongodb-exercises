# MongoDB - Aula 06 - Exercício
Autor: Matheus Rezende

## Fazer uma query para o campo name utilizando `explain` para ver o resultado da busca

```
matheus(mongod-3.0.12) be-mean> var query = {name: /Charizard/i}
matheus(mongod-3.0.12) be-mean> db.pokemons.find(query).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 3,
  "executionTimeMillis": 1,
  "totalKeysExamined": 0,
  "totalDocsExamined": 610,
  "executionStages": {
    "stage": "COLLSCAN",
    "filter": {
      "name": /Charizard/i
    },
    "nReturned": 3,
    "executionTimeMillisEstimate": 0,
    "works": 612,
    "advanced": 3,
    "needTime": 608,
    "needFetch": 0,
    "saveState": 4,
    "restoreState": 4,
    "isEOF": 1,
    "invalidates": 0,
    "direction": "forward",
    "docsExamined": 610
  }

```

## Criar um `index` um para o campo `name`

```
matheus(mongod-3.0.12) be-mean> db.pokemons.createIndex({name: 1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}

```

## Refazer a query para o campo `name` utilizando `explain` para ver o resultado da busca

```
matheus(mongod-3.0.12) be-mean> var query = {name: /Charizard/i}
matheus(mongod-3.0.12) be-mean> db.pokemons.find(query).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 3,
  "executionTimeMillis": 10,
  "totalKeysExamined": 610,
  "totalDocsExamined": 3,
  "executionStages": {
    "stage": "FETCH",
    "nReturned": 3,
    "executionTimeMillisEstimate": 0,
    "works": 611,
    "advanced": 3,
    "needTime": 607,
    "needFetch": 0,
    "saveState": 4,
    "restoreState": 4,
    "isEOF": 1,
    "invalidates": 0,
    "docsExamined": 3,
    "alreadyHasObj": 0,
    "inputStage": {
      "stage": "IXSCAN",
      "filter": {
        "name": /Charizard/i
      },
      "nReturned": 3,
      "executionTimeMillisEstimate": 0,
      "works": 610,
      "advanced": 3,
      "needTime": 607,
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
          "[/Charizard/i, /Charizard/i]"
        ]
      },
      "keysExamined": 610,
      "dupsTested": 0,
      "dupsDropped": 0,
      "seenInvalidated": 0,
      "matchTested": 3
    }
  }
}

```

## Fazer uma query para dois campos juntos utilizando `explain` para ver o resultado da busca

```
matheus(mongod-3.0.12) be-mean> db.pokemons.find({name: /Charizard/i, attack: {$gte: 63}}).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 3,
  "executionTimeMillis": 2,
  "totalKeysExamined": 610,
  "totalDocsExamined": 3,
  "executionStages": {
    "stage": "KEEP_MUTATIONS",
    "nReturned": 3,
    "executionTimeMillisEstimate": 0,
    "works": 611,
    "advanced": 3,
    "needTime": 607,
    "needFetch": 0,
    "saveState": 4,
    "restoreState": 4,
    "isEOF": 1,
    "invalidates": 0,
    "inputStage": {
      "stage": "FETCH",
      "filter": {
        "attack": {
          "$gte": 63
        }
      },
      "nReturned": 3,
      "executionTimeMillisEstimate": 0,
      "works": 611,
      "advanced": 3,
      "needTime": 607,
      "needFetch": 0,
      "saveState": 4,
      "restoreState": 4,
      "isEOF": 1,
      "invalidates": 0,
      "docsExamined": 3,
      "alreadyHasObj": 0,
      "inputStage": {
        "stage": "IXSCAN",
        "filter": {
          "name": /Charizard/i
        },
        "nReturned": 3,
        "executionTimeMillisEstimate": 0,
        "works": 610,
        "advanced": 3,
        "needTime": 607,
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
            "[/Charizard/i, /Charizard/i]"
          ]
        },
        "keysExamined": 610,
        "dupsTested": 0,
        "dupsDropped": 0,
        "seenInvalidated": 0,
        "matchTested": 3
      }
    }
  }
}

```

## Criar um `index` para esses dois campos juntos

```
matheus(mongod-3.0.12) be-mean> db.pokemons.createIndex({name: 1, attack: 1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 2,
  "numIndexesAfter": 3,
  "ok": 1
}

```

## Refazer a query para os dois campos juntos utilizando `explain` para ver o resultado da busca

```
matheus(mongod-3.0.12) be-mean> db.pokemons.find({name: /Charizard/i, attack: {$gte: 63}}).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 3,
  "executionTimeMillis": 5,
  "totalKeysExamined": 610,
  "totalDocsExamined": 3,
  "executionStages": {
    "stage": "FETCH",
    "nReturned": 3,
    "executionTimeMillisEstimate": 0,
    "works": 611,
    "advanced": 3,
    "needTime": 606,
    "needFetch": 0,
    "saveState": 9,
    "restoreState": 9,
    "isEOF": 1,
    "invalidates": 0,
    "docsExamined": 3,
    "alreadyHasObj": 0,
    "inputStage": {
      "stage": "IXSCAN",
      "filter": {
        "name": /Charizard/i
      },
      "nReturned": 3,
      "executionTimeMillisEstimate": 0,
      "works": 610,
      "advanced": 3,
      "needTime": 606,
      "needFetch": 0,
      "saveState": 9,
      "restoreState": 9,
      "isEOF": 1,
      "invalidates": 0,
      "keyPattern": {
        "name": 1,
        "attack": 1
      },
      "indexName": "name_1_attack_1",
      "isMultiKey": false,
      "direction": "forward",
      "indexBounds": {
        "name": [
          "[\"\", {})",
          "[/Charizard/i, /Charizard/i]"
        ],
        "attack": [
          "[63.0, inf.0]"
        ]
      },
      "keysExamined": 610,
      "dupsTested": 0,
      "dupsDropped": 0,
      "seenInvalidated": 0,
      "matchTested": 3
    }
  }
}

```
