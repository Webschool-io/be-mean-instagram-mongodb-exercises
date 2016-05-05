# MongoDB - Aula 06 - Exercício
autor: Rony Souza

## 1.  Indice para campo `name`

```
db.pokemons.find({ name: 'Charizard' }).explain('executionStats').executionStats
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
        "$eq": "Charizard"
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

# 2. Criar um index um para o campo name

```
 db.pokemons.createIndex({name: 1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}


```
# 3. Refazer a query para o campo name utilizando explain para ver o resultado da busca


```
db.pokemons.find( { name : 'Charizard' } ).explain('executionStats').executionStats
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
          "[\"Charizard\", \"Charizard\"]"
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

# 4. Fazer uma query para dois campos juntos utilizando explain para ver o resultado da busca

```js
> db.pokemons.find({$and : [{defense: 70}, {attack: { $gt: 110}}]}).explain('executionStats').executionStats
{
        "executionSuccess" : true,
        "nReturned" : 4,
        "executionTimeMillis" : 0,
        "totalKeysExamined" : 0,
        "totalDocsExamined" : 610,
        "executionStages" : {
                "stage" : "COLLSCAN",
                "filter" : {
                        "$and" : [
                                {
                                        "defense" : {
                                                "$eq" : 70
                                        }
                                },
                                {
                                        "attack" : {
                                                "$gt" : 110
                                        }
                                }
                        ]
                },
                "nReturned" : 4,
                "executionTimeMillisEstimate" : 0,
                "works" : 612,
                "advanced" : 4,
                "needTime" : 607,
                "needFetch" : 0,
                "saveState" : 4,
                "restoreState" : 4,
                "isEOF" : 1,
                "invalidates" : 0,
                "direction" : "forward",
                "docsExamined" : 610
        }
}
```


# 5. Criar um index para esses dois campos juntos

```
db.pokemons.createIndex({ speed: 1, types: 1 })
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 2,
  "numIndexesAfter": 3,
  "ok": 1
}
```
# 6. Refazer a query para os dois campos juntos utilizando explain para ver o resultado da busca
```
db.pokemons.find( { types: 'normal', speed: 72 } ).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 2,
  "executionTimeMillis": 0,
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
        "speed": 1,
        "types": 1
      },
      "indexName": "speed_1_types_1",
      "isMultiKey": true,
      "direction": "forward",
      "indexBounds": {
        "speed": [
          "[72.0, 72.0]"
        ],
        "types": [
          "[\"normal\", \"normal\"]"
        ]
      },
      "keysExamined": 2,
      "dupsTested": 2,
      "dupsDropped": 0,
      "seenInvalidated": 0,
      "matchTested": 0
    }
  }
}
```

```


