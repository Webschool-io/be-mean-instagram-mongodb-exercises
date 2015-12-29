# MongoDB - Aula 06 - Exercício
Autor: Paulo Roberto

## 1. Query sem indice do campo name.
```
> db.pokemons.getIndexes()
[
        {
                "v" : 1,
                "key" : {
                        "_id" : 1
                },
                "name" : "_id_",
                "ns" : "be-mean.pokemons"
        }
]
> db.pokemons.find({name:/Pikachu/i}).limit(1).explain('executionStats').executionStats
{
        "executionSuccess" : true,
        "nReturned" : 1,
        "executionTimeMillis" : 22,
        "totalKeysExamined" : 0,
        "totalDocsExamined" : 47,
        "executionStages" : {
                "stage" : "LIMIT",
                "nReturned" : 1,
                "executionTimeMillisEstimate" : 20,
                "works" : 49,
                "advanced" : 1,
                "needTime" : 47,
                "needYield" : 0,
                "saveState" : 1,
                "restoreState" : 1,
                "isEOF" : 1,
                "invalidates" : 0,
                "limitAmount" : 1,
                "inputStage" : {
                        "stage" : "COLLSCAN",
                        "filter" : {
                                "name" : /Pikachu/i
                        },
                        "nReturned" : 1,
                        "executionTimeMillisEstimate" : 20,
                        "works" : 48,
                        "advanced" : 1,
                        "needTime" : 47,
                        "needYield" : 0,
                        "saveState" : 1,
                        "restoreState" : 1,
                        "isEOF" : 0,
                        "invalidates" : 0,
                        "direction" : "forward",
                        "docsExamined" : 47
                }
        }
}
```
## 2. Após a criação do indice.
```
> db.pokemons.createIndex({'name':1})
{
        "createdCollectionAutomatically" : false,
        "numIndexesBefore" : 1,
        "numIndexesAfter" : 2,
        "ok" : 1
}
> db.pokemons.getIndexes()
[
        {
                "v" : 1,
                "key" : {
                        "_id" : 1
                },
                "name" : "_id_",
                "ns" : "be-mean.pokemons"
        },
        {
                "v" : 1,
                "key" : {
                        "name" : 1
                },
                "name" : "name_1",
                "ns" : "be-mean.pokemons"
        }
]
> db.pokemons.find({name:/Pikachu/i}).limit(1).explain('executionStats
').executionStats
{
        "executionSuccess" : true,
        "nReturned" : 1,
        "executionTimeMillis" : 2,
        "totalKeysExamined" : 396,
        "totalDocsExamined" : 1,
        "executionStages" : {
                "stage" : "LIMIT",
                "nReturned" : 1,
                "executionTimeMillisEstimate" : 0,
                "works" : 397,
                "advanced" : 1,
                "needTime" : 395,
                "needYield" : 0,
                "saveState" : 3,
                "restoreState" : 3,
                "isEOF" : 1,
                "invalidates" : 0,
                "limitAmount" : 1,
                "inputStage" : {
                        "stage" : "FETCH",
                        "nReturned" : 1,
                        "executionTimeMillisEstimate" : 0,
                        "works" : 396,
                        "advanced" : 1,
                        "needTime" : 395,
                        "needYield" : 0,
                        "saveState" : 3,
                        "restoreState" : 3,
                        "isEOF" : 0,
                        "invalidates" : 0,
                        "docsExamined" : 1,
                        "alreadyHasObj" : 0,
                        "inputStage" : {
                                "stage" : "IXSCAN",
                                "filter" : {
                                        "name" : /Pikachu/i
                                },
                                "nReturned" : 1,
                                "executionTimeMillisEstimate" : 0,
                                "works" : 396,
                                "advanced" : 1,
                                "needTime" : 395,
                                "needYield" : 0,
                                "saveState" : 3,
                                "restoreState" : 3,
                                "isEOF" : 0,
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
                                                "[\"\", {})",
                                                "[/Pikachu/i, /Pikachu
/i]"
                                        ]
                                },
                                "keysExamined" : 396,
                                "dupsTested" : 0,
                                "dupsDropped" : 0,
                                "seenInvalidated" : 0
                        }
                }
        }
}
```
## 3. Consulta por 2 campos sem indice.
```
> db.pokemons.find({defense:{$gte:40}, attack:{$gt:10}}).limit(1).explain('executionStats').executionStats
{
        "executionSuccess" : true,
        "nReturned" : 1,
        "executionTimeMillis" : 0,
        "totalKeysExamined" : 0,
        "totalDocsExamined" : 1,
        "executionStages" : {
                "stage" : "LIMIT",
                "nReturned" : 1,
                "executionTimeMillisEstimate" : 0,
                "works" : 3,
                "advanced" : 1,
                "needTime" : 1,
                "needYield" : 0,
                "saveState" : 0,
                "restoreState" : 0,
                "isEOF" : 1,
                "invalidates" : 0,
                "limitAmount" : 1,
                "inputStage" : {
                        "stage" : "COLLSCAN",
                        "filter" : {
                                "$and" : [
                                        {
                                                "attack" : {
                                                        "$gt" : 10
                                                }
                                        },
                                        {
                                                "defense" : {
                                                        "$gte" : 40
                                                }
                                        }
                                ]
                        },
                        "nReturned" : 1,
                        "executionTimeMillisEstimate" : 0,
                        "works" : 2,
                        "advanced" : 1,
                        "needTime" : 1,
                        "needYield" : 0,
                        "saveState" : 0,
                        "restoreState" : 0,
                        "isEOF" : 0,
                        "invalidates" : 0,
                        "direction" : "forward",
                        "docsExamined" : 1
                }
        }
}
```
## 4. Após criação de indice composto.
```
> db.pokemons.createIndex({defense:1, attack:1})
> db.pokemons.find({defense:{$gte:40}, attack:{$gt:10}}).limit(1).explain('executionStats').executionStats
{
        "executionSuccess" : true,
        "nReturned" : 1,
        "executionTimeMillis" : 0,
        "totalKeysExamined" : 1,
        "totalDocsExamined" : 1,
        "executionStages" : {
                "stage" : "LIMIT",
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
                "limitAmount" : 1,
                "inputStage" : {
                        "stage" : "FETCH",
                        "nReturned" : 1,
                        "executionTimeMillisEstimate" : 0,
                        "works" : 1,
                        "advanced" : 1,
                        "needTime" : 0,
                        "needYield" : 0,
                        "saveState" : 0,
                        "restoreState" : 0,
                        "isEOF" : 0,
                        "invalidates" : 0,
                        "docsExamined" : 1,
                        "alreadyHasObj" : 0,
                        "inputStage" : {
                                "stage" : "IXSCAN",
                                "nReturned" : 1,
                                "executionTimeMillisEstimate" : 0,
                                "works" : 1,
                                "advanced" : 1,
                                "needTime" : 0,
                                "needYield" : 0,
                                "saveState" : 0,
                                "restoreState" : 0,
                                "isEOF" : 0,
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
                                                "[40.0, 1.#INF]"
                                        ],
                                        "attack" : [
                                                "(10.0, 1.#INF]"
                                        ]
                                },
                                "keysExamined" : 1,
                                "dupsTested" : 0,
                                "dupsDropped" : 0,
                                "seenInvalidated" : 0
                        }
                }
        }
}
```
