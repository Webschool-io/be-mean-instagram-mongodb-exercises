# MongoDB - Aula 06 - Exercício
autor: Douglas Cofferi

## Fazer uma query para o campo name utilizando explain para ver o resultado da busca

```js
> db.pokemons.find({ name: /pikachu/i}).explain("executionStats")
{
        "queryPlanner" : {
                "plannerVersion" : 1,
                "namespace" : "be-mean.pokemons",
                "indexFilterSet" : false,
                "parsedQuery" : {
                        "name" : /pikachu/i
                },
                "winningPlan" : {
                        "stage" : "EOF"
                },
                "rejectedPlans" : [ ]
        },
        "executionStats" : {
                "executionSuccess" : true,
                "nReturned" : 0,
                "executionTimeMillis" : 0,
                "totalKeysExamined" : 0,
                "totalDocsExamined" : 0,
                "executionStages" : {
                        "stage" : "EOF",
                        "nReturned" : 0,
                        "executionTimeMillisEstimate" : 0,
                        "works" : 1,
                        "advanced" : 0,
                        "needTime" : 0,
                        "needFetch" : 0,
                        "saveState" : 0,
                        "restoreState" : 0,
                        "isEOF" : 1,
                        "invalidates" : 0
                }
        },
        "serverInfo" : {
                "host" : "User",
                "port" : 27017,
                "version" : "3.0.6",
                "gitVersion" : "1ef45a23a4c5e3480ac919b28afcba3c615488f2"
        },
        "ok" : 1
}
```

## Criar um index um para o campo name

```js
> db.pokemons.createIndex({ name: 1})
{
        "createdCollectionAutomatically" : true,
        "numIndexesBefore" : 1,
        "numIndexesAfter" : 2,
        "ok" : 1
}
```

## Refazer a query para o campo name utilizando explain para ver o resultado da busca

```js
> db.pokemons.find({name: /pikachu/i}).explain("executionStats")
{
        "queryPlanner" : {
                "plannerVersion" : 1,
                "namespace" : "be-mean.pokemons",
                "indexFilterSet" : false,
                "parsedQuery" : {
                        "name" : /pikachu/i
                },
                "winningPlan" : {
                        "stage" : "FETCH",
                        "inputStage" : {
                                "stage" : "IXSCAN",
                                "filter" : {
                                        "name" : /pikachu/i
                                },
                                "keyPattern" : {
                                        "name" : 1
                                },
                                "indexName" : "name_1",
                                "isMultiKey" : false,
                                "direction" : "forward",
                                "indexBounds" : {
                                        "name" : [
                                                "[\"\", {})",
                                                "[/pikachu/i, /pikachu/i]"
                                        ]
                                }
                        }
                },
                "rejectedPlans" : [ ]
        },
        "executionStats" : {
                "executionSuccess" : true,
                "nReturned" : 0,
                "executionTimeMillis" : 0,
                "totalKeysExamined" : 0,
                "totalDocsExamined" : 0,
                "executionStages" : {
                        "stage" : "FETCH",
                        "nReturned" : 0,
                        "executionTimeMillisEstimate" : 0,
                        "works" : 1,
                        "advanced" : 0,
                        "needTime" : 0,
                        "needFetch" : 0,
                        "saveState" : 0,
                        "restoreState" : 0,
                        "isEOF" : 1,
                        "invalidates" : 0,
                        "docsExamined" : 0,
                        "alreadyHasObj" : 0,
                        "inputStage" : {
                                "stage" : "IXSCAN",
                                "filter" : {
                                        "name" : /pikachu/i
                                },
                                "nReturned" : 0,
                                "executionTimeMillisEstimate" : 0,
                                "works" : 1,
                                "advanced" : 0,
                                "needTime" : 0,
                                "needFetch" : 0,
                                "saveState" : 0,
                                "restoreState" : 0,
                                "isEOF" : 1,
                                "invalidates" : 0,
                                "keyPattern" : {
                                        "name" : 1
                                },
                                "indexName" : "name_1",
                                "isMultiKey" : false,
                                "direction" : "forward",
                                "indexBounds" : {
                                        "name" : [
                                                "[\"\", {})",
                                                "[/pikachu/i, /pikachu/i]"
                                        ]
                                },
                                "keysExamined" : 0,
                                "dupsTested" : 0,
                                "dupsDropped" : 0,
                                "seenInvalidated" : 0,
                                "matchTested" : 0
                        }
                }
        },
        "serverInfo" : {
                "host" : "User",
                "port" : 27017,
                "version" : "3.0.6",
                "gitVersion" : "1ef45a23a4c5e3480ac919b28afcba3c615488f2"
        },
        "ok" : 1
}
```

## Fazer uma query para dois campos juntos utilizando explain para ver o resultado da busca


```js
> db.pokemons.find({ hp: 35, speed: 90}).explain("executionStats").executionStats
{
        "executionSuccess" : true,
        "nReturned" : 0,
        "executionTimeMillis" : 0,
        "totalKeysExamined" : 0,
        "totalDocsExamined" : 0,
        "executionStages" : {
                "stage" : "COLLSCAN",
                "filter" : {
                        "$and" : [
                                {
                                        "hp" : {
                                                "$eq" : 35
                                        }
                                },
                                {
                                        "speed" : {
                                                "$eq" : 90
                                        }
                                }
                        ]
                },
                "nReturned" : 0,
                "executionTimeMillisEstimate" : 0,
                "works" : 2,
                "advanced" : 0,
                "needTime" : 1,
                "needFetch" : 0,
                "saveState" : 0,
                "restoreState" : 0,
                "isEOF" : 1,
                "invalidates" : 0,
                "direction" : "forward",
                "docsExamined" : 0
        }
}
```

## Criar um index para esses dois campos juntos


```js
> db.pokemons.createIndex({ hp: 1, speed: 1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 2,
  "numIndexesAfter": 3,
  "ok": 1
}
```

## Refazer a query para os dois campos juntos utilizando explain para ver o resultado da busca

```js
> db.pokemons.find({ hp: 35, speed: 90}).explain("executionStats").executionStats
{
        "executionSuccess" : true,
        "nReturned" : 0,
        "executionTimeMillis" : 0,
        "totalKeysExamined" : 0,
        "totalDocsExamined" : 0,
        "executionStages" : {
                "stage" : "FETCH",
                "nReturned" : 0,
                "executionTimeMillisEstimate" : 0,
                "works" : 1,
                "advanced" : 0,
                "needTime" : 0,
                "needFetch" : 0,
                "saveState" : 0,
                "restoreState" : 0,
                "isEOF" : 1,
                "invalidates" : 0,
                "docsExamined" : 0,
                "alreadyHasObj" : 0,
                "inputStage" : {
                        "stage" : "IXSCAN",
                        "nReturned" : 0,
                        "executionTimeMillisEstimate" : 0,
                        "works" : 1,
                        "advanced" : 0,
                        "needTime" : 0,
                        "needFetch" : 0,
                        "saveState" : 0,
                        "restoreState" : 0,
                        "isEOF" : 1,
                        "invalidates" : 0,
                        "keyPattern" : {
                                "hp" : 1,
                                "speed" : 1
                        },
                        "indexName" : "hp_1_speed_1",
                        "isMultiKey" : false,
                        "direction" : "forward",
                        "indexBounds" : {
                                "hp" : [
                                        "[35.0, 35.0]"
                                ],
                                "speed" : [
                                        "[90.0, 90.0]"
                                ]
                        },
                        "keysExamined" : 0,
                        "dupsTested" : 0,
                        "dupsDropped" : 0,
                        "seenInvalidated" : 0,
                        "matchTested" : 0
                }
        }
}
```