# MongoDB - Aula 06 - Exercício

autor: Diego Pereira Grassato(diegograssato)

## Fazer um query sem index para o campo **name** utilizando o explain.

```
913563b68bf2(mongod-3.2.1) pokemons> db.pokemons.find({name: "Charmander"}).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 1,
  "executionTimeMillis": 0,
  "totalKeysExamined": 0,
  "totalDocsExamined": 4,
  "executionStages": {
    "stage": "COLLSCAN",
    "filter": {
      "name": {
        "$eq": "Charmander"
      }
    },
    "nReturned": 1,
    "executionTimeMillisEstimate": 0,
    "works": 6,
    "advanced": 1,
    "needTime": 4,
    "needYield": 0,
    "saveState": 0,
    "restoreState": 0,
    "isEOF": 1,
    "invalidates": 0,
    "direction": "forward",
    "docsExamined": 4
  }
}

913563b68bf2(mongod-3.2.1) pokemons> db.pokemons.find({ name: /pikachu/i }).explain('executionStats').executionStats.totalDocsExamined
4

```

## Criar um index para o campo **name**.

```
913563b68bf2(mongod-3.2.1) pokemons> db.pokemons.createIndex({name: 1})
{
	"createdCollectionAutomatically" : false,
	"numIndexesBefore" : 1,
	"numIndexesAfter" : 2,
	"ok" : 1
}
```

## Fazer um query com index para o campo **name** utilizando o explain.

```
913563b68bf2(mongod-3.2.1) pokemons> db.pokemons.find({name: "Charmander"}).explain('executionStats').executionStats
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
          "[\"Charmander\", \"Charmander\"]"
        ]
      },
      "keysExamined": 1,
      "dupsTested": 0,
      "dupsDropped": 0,
      "seenInvalidated": 0
    }
  }
}


913563b68bf2(mongod-3.2.1) pokemons> db.pokemons.find({ name: /pikachu/i }).explain('executionStats').executionStats.totalDocsExamined
1


```

## Fazer uma query sem index para dois campos juntos utilizando o explain.

```
var query = {
	$and: [
		{ attack: { $gte: 50 } },
		{ defense: { $gte: 30 } }
	]
}
db.pokemons.find(query).explain('executionStats').executionStats.totalDocsExamined
4

913563b68bf2(mongod-3.2.1) pokemons> db.pokemons.find(query).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 0,
  "executionTimeMillis": 0,
  "totalKeysExamined": 0,
  "totalDocsExamined": 4,
  "executionStages": {
    "stage": "COLLSCAN",
    "filter": {
      "$and": [
        {
          "attack": {
            "$gte": 50
          }
        },
        {
          "defense": {
            "$gte": 30
          }
        }
      ]
    },
    "nReturned": 0,
    "executionTimeMillisEstimate": 0,
    "works": 6,
    "advanced": 0,
    "needTime": 5,
    "needYield": 0,
    "saveState": 0,
    "restoreState": 0,
    "isEOF": 1,
    "invalidates": 0,
    "direction": "forward",
    "docsExamined": 4
  }
}

```

## Criar um index para dois campos juntos.

```

913563b68bf2(mongod-3.2.1) pokemons> db.pokemons.createIndex({attack: 1, defense: 1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 2,
  "numIndexesAfter": 3,
  "ok": 1
}

```

## Fazer uma query com index para dois campos juntos utilizando o explain.

```
913563b68bf2(mongod-3.2.1) pokemons> db.pokemons.find(query).explain('executionStats').executionStats.totalDocsExamined
0

913563b68bf2(mongod-3.2.1) pokemons> db.pokemons.find(query).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 0,
  "executionTimeMillis": 0,
  "totalKeysExamined": 2,
  "totalDocsExamined": 0,
  "executionStages": {
    "stage": "FETCH",
    "nReturned": 0,
    "executionTimeMillisEstimate": 0,
    "works": 3,
    "advanced": 0,
    "needTime": 2,
    "needYield": 0,
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
      "works": 3,
      "advanced": 0,
      "needTime": 2,
      "needYield": 0,
      "saveState": 0,
      "restoreState": 0,
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
          "[50.0, inf.0]"
        ],
        "defense": [
          "[30.0, inf.0]"
        ]
      },
      "keysExamined": 2,
      "dupsTested": 0,
      "dupsDropped": 0,
      "seenInvalidated": 0
    }
  }
}

```
