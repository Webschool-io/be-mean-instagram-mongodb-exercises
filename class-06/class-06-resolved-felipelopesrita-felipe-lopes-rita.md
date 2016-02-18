# MongoDB - Aula 06 - Exercício
User: https://github.com/felipelopesrita
Autor: Felipe José Lopes Rita

# Fazer uma query para o campo name utilizando `explain` para ver o resultado da busca
StarKiller(mongod-3.2.0) be-mean> db.pokemons.find({name:"Pikachu"}).explain('executionStats').executionStats
{
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
}

# Criar um `index` um para o campo `name`.
StarKiller(mongod-3.2.0) be-mean> db.pokemons.createIndex({name:1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}

# Refazer a query para o campo `name` utilizando `explain` para ver o resultado da busca.
db.pokemons.find({name:"Pikachu"}).explain('executionStats').executionStats
{
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
}

# Fazer uma query para dois campos juntos utilizando `explain` para ver o resultado da busca.
StarKiller(mongod-3.2.0) be-mean> db.pokemons.find({name:"Pikachu", attack: {$gt: 50} }).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 1,
  "executionTimeMillis": 0,
  "totalKeysExamined": 0,
  "totalDocsExamined": 610,
  "executionStages": {
    "stage": "COLLSCAN",
    "filter": {
      "$and": [
        {
          "name": {
            "$eq": "Pikachu"
          }
        },
        {
          "attack": {
            "$gt": 50
          }
        }
      ]
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
}

# Criar um `index` para esses dois campos juntos.
StarKiller(mongod-3.2.0) be-mean> db.pokemons.createIndex({name:1, attack:1});
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}

# Refazer a query para os dois campos juntos utilizando `explain` para ver o resultado da busca.
StarKiller(mongod-3.2.0) be-mean> db.pokemons.find({name:"Pikachu", attack: {$gt: 50} }).explain('executionStats').executionStats
{
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
        "name": 1,
        "attack": 1
      },
      "indexName": "name_1_attack_1",
      "isMultiKey": false,
      "isUnique": false,
      "isSparse": false,
      "isPartial": false,
      "indexVersion": 1,
      "direction": "forward",
      "indexBounds": {
        "name": [
          "[\"Pikachu\", \"Pikachu\"]"
        ],
        "attack": [
          "(50.0, inf.0]"
        ]
      },
      "keysExamined": 1,
      "dupsTested": 0,
      "dupsDropped": 0,
      "seenInvalidated": 0
    }
  }
}
