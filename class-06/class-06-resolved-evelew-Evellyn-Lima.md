# MongoDb - Aula 06 - Exercício
# autor: Evellyn Lima

## Criar dois índices, um simples e 1 composto.
### Simples
> db.pokemons.createIndex({ name: 1 })

### Composto
> db.pokemons.createIndex({ name: 1 , speed: 1})

## Fazer quatro buscas no banco.
### 1 simples sem indice
```
> db.pokemons.find({ name: "Rattata" }).explain('executionStats')
{
        "executionSuccess" : true,
        "nReturned" : 1,
        "executionTimeMillis" : 94,
        "totalKeysExamined" : 0,
        "totalDocsExamined" : 610,
        "executionStages" : {
                "stage" : "COLLSCAN",
                "filter" : {
                        "name" : {
                                "$eq" : "Rattata"
                        }
                },
                "nReturned" : 1,
                "executionTimeMillisEstimate" : 30,
                "works" : 612,
                "advanced" : 1,
                "needTime" : 610,
                "needYield" : 0,
                "saveState" : 5,
                "restoreState" : 5,
                "isEOF" : 1,
                "invalidates" : 0,
                "direction" : "forward",
                "docsExamined" : 610
        }
}
```
### A mesma busca simples porem com índice
```
> db.pokemons.find({ name: "Rattata" }).explain('executionStats')
{
        "executionSuccess" : true,
        "nReturned" : 1,
        "executionTimeMillis" : 75,
        "totalKeysExamined" : 1,
        "totalDocsExamined" : 1,
        "executionStages" : {
                "stage" : "FETCH",
                "nReturned" : 1,
                "executionTimeMillisEstimate" : 11,
                "works" : 2,
                "advanced" : 1,
                "needTime" : 0,
                "needYield" : 0,
                "saveState" : 2,
                "restoreState" : 2,
                "isEOF" : 1,
                "invalidates" : 0,
                "docsExamined" : 1,
                "alreadyHasObj" : 0,
                "inputStage" : {
                        "stage" : "IXSCAN",
                        "nReturned" : 1,
                        "executionTimeMillisEstimate" : 11,
                        "works" : 2,
                        "advanced" : 1,
                        "needTime" : 0,
                        "needYield" : 0,
                        "saveState" : 2,
                        "restoreState" : 2,
                        "isEOF" : 1,
                        "invalidates" : 0,
                        "keyPattern" : {
                                "name" : 1
                        },
                        "indexName" : "name_1",
                        "isMultiKey" : false,
                        "multiKeyPaths" : {
                                "name" : [ ]
                        },
                        "isUnique" : false,
                        "isSparse" : false,
						 "isPartial" : false,
                        "indexVersion" : 2,
                        "direction" : "forward",
                        "indexBounds" : {
                                "name" : [
                                        "[\"Rattata\", \"Rattata\"]"
                                ]
                        },
                        "keysExamined" : 1,
                        "seeks" : 1,
                        "dupsTested" : 0,
                        "dupsDropped" : 0,
                        "seenInvalidated" : 0
                }
        }
}
```

### Uma busca composta sem índice
```
> db.pokemons.find({ $and: [{ name: "Rattata"}, { speed: {$gt: 70} } ]}).explain('executionStats')
{
        "executionSuccess" : true,
        "nReturned" : 1,
        "executionTimeMillis" : 55,
        "totalKeysExamined" : 0,
        "totalDocsExamined" : 610,
        "executionStages" : {
                "stage" : "COLLSCAN",
                "filter" : {
                        "$and" : [
                                {
                                        "name" : {
                                                "$eq" : "Rattata"
                                        }
                                },
                                {
                                        "speed" : {
                                                "$gt" : 70
                                        }
                                }
                        ]
                },
                "nReturned" : 1,
                "executionTimeMillisEstimate" : 0,
                "works" : 612,
                "advanced" : 1,
                "needTime" : 610,
                "needYield" : 0,
                "saveState" : 4,
                "restoreState" : 4,
                "isEOF" : 1,
                "invalidates" : 0,
                "direction" : "forward",
                "docsExamined" : 610
        }
}
```
### A mesma busca composto com índice  
```
> db.pokemons.find({ $and: [{ name: "Rattata"}, { speed: {$gt: 70} } ]}).explain('executionStats')

{
        "executionSuccess" : true,
        "nReturned" : 1,
        "executionTimeMillis" : 25,
        "totalKeysExamined" : 1,
        "totalDocsExamined" : 1,
        "executionStages" : {
                "stage" : "FETCH",
                "nReturned" : 1,
                "executionTimeMillisEstimate" : 0,
                "works" : 3,
                "advanced" : 1,
                "needTime" : 0,
                "needYield" : 0,
                "saveState" : 1,
                "restoreState" : 1,
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
                        "saveState" : 1,
                        "restoreState" : 1,
                        "isEOF" : 1,
                        "invalidates" : 0,
                        "keyPattern" : {
                                "name" : 1,
                                "speed" : 1
                        },
                        "indexName" : "name_1_speed_1",
                        "isMultiKey" : false,
                        "multiKeyPaths" : {        "name" : [ ],
                                "speed" : [ ]
                        },
                        "isUnique" : false,
                        "isSparse" : false,
                        "isPartial" : false,
                        "indexVersion" : 2,
                        "direction" : "forward",
                        "indexBounds" : {
                                "name" : [
                                        "[\"Rattata\", \"Rattata\"]"
                                ],
                                "speed" : [
                                        "(70.0, inf.0]"
                                ]
                        },
                        "keysExamined" : 1,
                        "seeks" : 1,
                        "dupsTested" : 0,
                        "dupsDropped" : 0,
                        "seenInvalidated" : 0
                }
        }
}
```