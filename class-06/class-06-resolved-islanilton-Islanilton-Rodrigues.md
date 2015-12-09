# MongoDB - Aula 06 - Exercício
autor: Islanilton Rodrigues 

## 1. Realizando a query pelo name sem indexe 

,,

islanilton-pc(mongod-3.0.7) be-mean-instagram> db.pokemons.find({"name": "Cubone"}).explain('executionStats').executionStats;
{
  "executionSuccess": true,
  "nReturned": 1,
  "executionTimeMillis": 0,
  "totalKeysExamined": 0,
  "totalDocsExamined": 620,
  "executionStages": {
    "stage": "COLLSCAN",
    "filter": {
      "name": {
        "$eq": "Cubone"
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
}


## 2. Realizando a query pelo name com index criado

islanilton-pc(mongod-3.0.7) be-mean-instagram> db.pokemons.createIndex({name:1});
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}


islanilton-pc(mongod-3.0.7) be-mean-instagram> db.pokemons.getIndexes();
[
  {
    "v": 1,
    "key": {
      "_id": 1
    },
    "name": "_id_",
    "ns": "be-mean-instagram.pokemons"
  },
  {
    "v": 1,
    "key": {
      "name": 1
    },
    "name": "name_1",
    "ns": "be-mean-instagram.pokemons"
  }
]


islanilton-pc(mongod-3.0.7) be-mean-instagram> db.pokemons.find({"name": "Cubone"}).explain('executionStats').executionStats;
{
  "executionSuccess": true,
  "nReturned": 1,
  "executionTimeMillis": 19,
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
          "[\"Cubone\", \"Cubone\"]"
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



## 3. Realizando a query com dois campos juntos sem o index criado

islanilton-pc(mongod-3.0.7) be-mean-instagram> var query = {$and: [{hp:60},{defense:95}]};

islanilton-pc(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query).explain('executionStats').executionStats;
{
  "executionSuccess": true,
  "nReturned": 2,
  "executionTimeMillis": 22,
  "totalKeysExamined": 0,
  "totalDocsExamined": 620,
  "executionStages": {
    "stage": "COLLSCAN",
    "filter": {
      "$and": [
        {
          "defense": {
            "$eq": 95
          }
        },
        {
          "hp": {
            "$eq": 60
          }
        }
      ]
    },
    "nReturned": 2,
    "executionTimeMillisEstimate": 0,
    "works": 622,
    "advanced": 2,
    "needTime": 619,
    "needFetch": 0,
    "saveState": 4,
    "restoreState": 4,
    "isEOF": 1,
    "invalidates": 0,
    "direction": "forward",
    "docsExamined": 620
  }
}


## 4. Realizando a query com dois campos juntos e com os dois indexes

islanilton-pc(mongod-3.0.7) be-mean-instagram> db.pokemons.createIndex({hp:1,defense:1});
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 2,
  "numIndexesAfter": 3,
  "ok": 1
}


islanilton-pc(mongod-3.0.7) be-mean-instagram> db.pokemons.getIndexes();
[
  {
    "v": 1,
    "key": {
      "_id": 1
    },
    "name": "_id_",
    "ns": "be-mean-instagram.pokemons"
  },
  {
    "v": 1,
    "key": {
      "name": 1
    },
    "name": "name_1",
    "ns": "be-mean-instagram.pokemons"
  },
  {
    "v": 1,
    "key": {
      "hp": 1,
      "defense": 1
    },
    "name": "hp_1_defense_1",
    "ns": "be-mean-instagram.pokemons"
  }
]


islanilton-pc(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query).explain('executionStats').executionStats;
{
  "executionSuccess": true,
  "nReturned": 2,
  "executionTimeMillis": 48,
  "totalKeysExamined": 2,
  "totalDocsExamined": 2,
  "executionStages": {
    "stage": "FETCH",
    "nReturned": 2,
    "executionTimeMillisEstimate": 0,
    "works": 3,
    "advanced": 2,
    "needTime": 0,
    "needFetch": 0,
    "saveState": 0,
    "restoreState": 0,
    "isEOF": 1,
    "invalidates": 0,
    "docsExamined": 2,
    "alreadyHasObj": 0,
    "inputStage": {
      "stage": "IXSCAN",
      "nReturned": 2,
      "executionTimeMillisEstimate": 0,
      "works": 3,
      "advanced": 2,
      "needTime": 0,
      "needFetch": 0,
      "saveState": 0,
      "restoreState": 0,
      "isEOF": 1,
      "invalidates": 0,
      "keyPattern": {
        "hp": 1,
        "defense": 1
      },
      "indexName": "hp_1_defense_1",
      "isMultiKey": false,
      "direction": "forward",
      "indexBounds": {
        "hp": [
          "[60.0, 60.0]"
        ],
        "defense": [
          "[95.0, 95.0]"
        ]
      },
      "keysExamined": 2,
      "dupsTested": 0,
      "dupsDropped": 0,
      "seenInvalidated": 0,
      "matchTested": 0
    }
  }
}

