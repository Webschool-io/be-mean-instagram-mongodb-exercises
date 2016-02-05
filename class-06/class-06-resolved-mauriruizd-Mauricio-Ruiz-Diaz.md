# MongoDB - Aula 06 - Exercícios
autor : Mauricio Ruiz Diaz

## 1 . Buscar um registro sem e com index no campo `name`
```
> var explain = db.pokemons.explain('executionStats');
> explain.find({ name : /rattata/i });
{
        "queryPlanner" : {
                "plannerVersion" : 1,
                "namespace" : "be-mean.pokemons",
                "indexFilterSet" : false,
                "parsedQuery" : {
                        "name" : /rattata/i
                },
                "winningPlan" : {
                        "stage" : "COLLSCAN",
                        "filter" : {
                                "name" : /rattata/i
                        },
                        "direction" : "forward"
                },
                "rejectedPlans" : [ ]
        },
        "executionStats" : {
                "executionSuccess" : true,
                "nReturned" : 1,
                "executionTimeMillis" : 1,
                "totalKeysExamined" : 0,
                "totalDocsExamined" : 610,
                "executionStages" : {
                        "stage" : "COLLSCAN",
                        "filter" : {
                                "name" : /rattata/i
                        },
                        "nReturned" : 1,
                        "executionTimeMillisEstimate" : 0,
                        "works" : 612,
                        "advanced" : 1,
                        "needTime" : 610,
                        "needFetch" : 0,
                        "saveState" : 4,
                        "restoreState" : 4,
                        "isEOF" : 1,
                        "invalidates" : 0,
                        "direction" : "forward",
                        "docsExamined" : 610
                }
        },
        "serverInfo" : {
                "host" : "RUIZDIAZss",
                "port" : 27017,
                "version" : "3.0.5",
                "gitVersion" : "8bc4ae20708dbb493cb09338d9e7be6698e4a3a3"
        },
        "ok" : 1
}

> db.pokemons.createIndex({ name : 1 })
{
        "createdCollectionAutomatically" : false,
        "numIndexesBefore" : 1,
        "numIndexesAfter" : 2,
        "ok" : 1
}
```

## 2. Buscar um registro sem e com index composto.
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

> explain.find({ attack : { $gt : 30 }, defense : { $lt : 90 } })
{
        "queryPlanner" : {
                "plannerVersion" : 1,
                "namespace" : "be-mean.pokemons",
                "indexFilterSet" : false,
                "parsedQuery" : {
                        "$and" : [
                                {
                                        "defense" : {
                                                "$lt" : 90
                                        }
                                },
                                {
                                        "attack" : {
                                                "$gt" : 30
                                        }
                                }
                        ]
                },
                "winningPlan" : {
                        "stage" : "COLLSCAN",
                        "filter" : {
                                "$and" : [
                                        {
                                                "defense" : {
                                                        "$lt" : 90
                                                }
                                        },
                                        {
                                                "attack" : {
                                                        "$gt" : 30
                                                }
                                        }
                                ]
                        },
                        "direction" : "forward"
                },
                "rejectedPlans" : [ ]
        },
        "executionStats" : {
                "executionSuccess" : true,
                "nReturned" : 420,
                "executionTimeMillis" : 0,
                "totalKeysExamined" : 0,
                "totalDocsExamined" : 610,
                "executionStages" : {
                        "stage" : "COLLSCAN",
                        "filter" : {
                                "$and" : [
                                        {
                                                "defense" : {
                                                        "$lt" : 90
                                                }
                                        },
                                        {
                                                "attack" : {
                                                        "$gt" : 30
                                                }
                                        }
                                ]
                        },
                        "nReturned" : 420,
                        "executionTimeMillisEstimate" : 0,
                        "works" : 612,
                        "advanced" : 420,
                        "needTime" : 191,
                        "needFetch" : 0,
                        "saveState" : 4,
                        "restoreState" : 4,
                        "isEOF" : 1,
                        "invalidates" : 0,
                        "direction" : "forward",
                        "docsExamined" : 610
                }
        },
        "serverInfo" : {
                "host" : "RUIZDIAZss",
                "port" : 27017,
                "version" : "3.0.5",
                "gitVersion" : "8bc4ae20708dbb493cb09338d9e7be6698e4a3a3"
        },
        "ok" : 1
}

> db.pokemons.createIndex({ attack : 1, defense : 1 })
{
        "createdCollectionAutomatically" : false,
        "numIndexesBefore" : 2,
        "numIndexesAfter" : 3,
        "ok" : 1
}

> explain.find({ attack : { $gt : 30 }, defense : { $lt : 90 } })
{
        "queryPlanner" : {
                "plannerVersion" : 1,
                "namespace" : "be-mean.pokemons",
                "indexFilterSet" : false,
                "parsedQuery" : {
                        "$and" : [
                                {
                                        "defense" : {
                                                "$lt" : 90
                                        }
                                },
                                {
                                        "attack" : {
                                                "$gt" : 30
                                        }
                                }
                        ]
                },
                "winningPlan" : {
                        "stage" : "FETCH",
                        "inputStage" : {
                                "stage" : "IXSCAN",
                                "keyPattern" : {
                                        "attack" : 1,
                                        "defense" : 1
                                },
                                "indexName" : "attack_1_defense_1",
                                "isMultiKey" : false,
                                "direction" : "forward",
                                "indexBounds" : {
                                        "attack" : [
                                                "(30.0, 1.#INF]"
                                        ],
                                        "defense" : [
                                                "[-1.#INF, 90.0)"
                                        ]
                                }
                        }
                },
                "rejectedPlans" : [ ]
        },
        "executionStats" : {
                "executionSuccess" : true,
                "nReturned" : 420,
                "executionTimeMillis" : 1,
                "totalKeysExamined" : 468,
                "totalDocsExamined" : 420,
                "executionStages" : {
                        "stage" : "FETCH",
                        "nReturned" : 420,
                        "executionTimeMillisEstimate" : 0,
                        "works" : 468,
                        "advanced" : 420,
                        "needTime" : 47,
                        "needFetch" : 0,
                        "saveState" : 3,
                        "restoreState" : 3,
                        "isEOF" : 1,
                        "invalidates" : 0,
                        "docsExamined" : 420,
                        "alreadyHasObj" : 0,
                        "inputStage" : {
                                "stage" : "IXSCAN",
                                "nReturned" : 420,
                                "executionTimeMillisEstimate" : 0,
                                "works" : 468,
                                "advanced" : 420,
                                "needTime" : 47,
                                "needFetch" : 0,
                                "saveState" : 3,
                                "restoreState" : 3,
                                "isEOF" : 1,
                                "invalidates" : 0,
                                "keyPattern" : {
                                        "attack" : 1,
                                        "defense" : 1
                                },
                                "indexName" : "attack_1_defense_1",
                                "isMultiKey" : false,
                                "direction" : "forward",
                                "indexBounds" : {
                                        "attack" : [
                                                "(30.0, 1.#INF]"
                                        ],
                                        "defense" : [
                                                "[-1.#INF, 90.0)"
                                        ]
                                },
                                "keysExamined" : 468,
                                "dupsTested" : 0,
                                "dupsDropped" : 0,
                                "seenInvalidated" : 0,
                                "matchTested" : 0
                        }
                }
        },
        "serverInfo" : {
                "host" : "RUIZDIAZss",
                "port" : 27017,
                "version" : "3.0.5",
                "gitVersion" : "8bc4ae20708dbb493cb09338d9e7be6698e4a3a3"
        },
        "ok" : 1
}

```