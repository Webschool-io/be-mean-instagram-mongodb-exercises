# MongoDB - Aula 06 - Exercício
autor: Wellerson Roberto

## 1. Fazer uma query para o campo name utilizando explain para ver o resultado da busca ##

```
> db.pokemons.find({name: "Beedrill"}).explain("executionStats").executionStats
{
        "executionSuccess" : true,
        "nReturned" : 1,
        "executionTimeMillis" : 0,
        "totalKeysExamined" : 0,
        "totalDocsExamined" : 620,
        "executionStages" : {
                "stage" : "COLLSCAN",
                "filter" : {
                        "name" : {
                                "$eq" : "Beedrill"
                        }
                },
                "nReturned" : 1,
                "executionTimeMillisEstimate" : 0,
                "works" : 622,
                "advanced" : 1,
                "needTime" : 620,
                "needYield" : 0,
                "saveState" : 4,
                "restoreState" : 4,
                "isEOF" : 1,
                "invalidates" : 0,
                "direction" : "forward",
                "docsExamined" : 620
        }
}
```

## 2. Criar um index um para o campo name ##

```
> db.pokemons.createIndex({name: 1})
{
        "createdCollectionAutomatically" : false,
        "numIndexesBefore" : 1,
        "numIndexesAfter" : 2,
        "ok" : 1
}
```

## 3. Refazer a query para o campo name utilizando explain para ver o resultado da busca ##
```
> db.pokemons.find({name: "Beedrill"}).explain("executionStats").executionStats
{
        "executionSuccess" : true,
        "nReturned" : 1,
        "executionTimeMillis" : 0,
        "totalKeysExamined" : 1,
        "totalDocsExamined" : 1,
        "executionStages" : {
                "stage" : "FETCH",
                "nReturned" : 1,
                "executionTimeMillisEstimate" : 0,
                "works" : 2,
                "advanced" : 1,
                "needTime" : 0,
                "needYield" : 0,
                "saveState" : 0,
                "restoreState" : 0,
                "isEOF" : 1,
                "invalidates" : 0,
                "docsExamined" : 1,
                "alreadyHasObj" : 0,
                "inputStage" : {
                        "stage" : "IXSCAN",
                        "nReturned" : 1,
                        "executionTimeMillisEstimate" : 0,
                        "works" : 2,
                        "advanced" : 1,
                        "needTime" : 0,
                        "needYield" : 0,
                        "saveState" : 0,
                        "restoreState" : 0,
                        "isEOF" : 1,
                        "invalidates" : 0,
                        "keyPattern" : {
                                "name" : 1
                        },
                        "indexName" : "name_1",
                        "isMultiKey" : false,
                        "isUnique" : false,
                        "isSparse" : false,
                        "isPartial" : false,
                        "indexVersion" : 1,
                        "direction" : "forward",
                        "indexBounds" : {
                                "name" : [
                                        "[\"Beedrill\", \"Beedrill\"]"
                                ]
                        },
                        "keysExamined" : 1,
                        "dupsTested" : 0,
                        "dupsDropped" : 0,
                        "seenInvalidated" : 0
                }
        }
}
```

## 4. Fazer uma query para dois campos juntos utilizando explain para ver o resultado da busca ##

```
> db.pokemons.find({defense: {$gt: 80}, attack: {$gt: 100}}).explain("executionStats").executionStats
{
        "executionSuccess" : true,
        "nReturned" : 59,
        "executionTimeMillis" : 15,
        "totalKeysExamined" : 0,
        "totalDocsExamined" : 620,
        "executionStages" : {
                "stage" : "COLLSCAN",
                "filter" : {
                        "$and" : [
                                {
                                        "attack" : {
                                                "$gt" : 100
                                        }
                                },
                                {
                                        "defense" : {
                                                "$gt" : 80
                                        }
                                }
                        ]
                },
                "nReturned" : 59,
                "executionTimeMillisEstimate" : 0,
                "works" : 622,
                "advanced" : 59,
                "needTime" : 562,
                "needYield" : 0,
                "saveState" : 4,
                "restoreState" : 4,
                "isEOF" : 1,
                "invalidates" : 0,
                "direction" : "forward",
                "docsExamined" : 620
        }
}
```

## 5. Criar um index para esses dois campos juntos ##

```
> db.pokemons.createIndex({defense: 1, attack: 1})
{
        "createdCollectionAutomatically" : false,
        "numIndexesBefore" : 2,
        "numIndexesAfter" : 3,
        "ok" : 1
}
```

## 6. Refazer a query para os dois campos juntos utilizando explain para ver o resultado da busca ##

```
> db.pokemons.find({defense: {$gt: 80}, attack: {$gt: 100}}).explain("executionStats").executionStats
{
        "executionSuccess" : true,
        "nReturned" : 59,
        "executionTimeMillis" : 0,
        "totalKeysExamined" : 94,
        "totalDocsExamined" : 59,
        "executionStages" : {
                "stage" : "FETCH",
                "nReturned" : 59,
                "executionTimeMillisEstimate" : 0,
                "works" : 95,
                "advanced" : 59,
                "needTime" : 35,
                "needYield" : 0,
                "saveState" : 0,
                "restoreState" : 0,
                "isEOF" : 1,
                "invalidates" : 0,
                "docsExamined" : 59,
                "alreadyHasObj" : 0,
                "inputStage" : {
                        "stage" : "IXSCAN",
                        "nReturned" : 59,
                        "executionTimeMillisEstimate" : 0,
                        "works" : 95,
                        "advanced" : 59,
                        "needTime" : 35,
                        "needYield" : 0,
                        "saveState" : 0,
                        "restoreState" : 0,
                        "isEOF" : 1,
                        "invalidates" : 0,
                        "keyPattern" : {
                                "defense" : 1,
                                "attack" : 1
                        },
                        "indexName" : "defense_1_attack_1",
                        "isMultiKey" : false,
                        "isUnique" : false,
                        "isSparse" : false,
                        "isPartial" : false,
                        "indexVersion" : 1,
                        "direction" : "forward",
                        "indexBounds" : {
                                "defense" : [
                                        "(80.0, 1.#INF]"
                                ],
                                "attack" : [
                                        "(100.0, 1.#INF]"
                                ]
                        },
                        "keysExamined" : 94,
                        "dupsTested" : 0,
                        "dupsDropped" : 0,
                        "seenInvalidated" : 0
                }
        }
}
```
