# MongoDB - Aula 06 - Exercício
autor: Gabriel Panassol


Utilizando a base pokemon e o explain

Pokemons que vou usar:
```
> db.pokemons.find().limit( 1 ).skip( _rand() * db.pokemons.count() ).pretty()
{
        "_id" : ObjectId("564b1dcb25337263280d059a"),
        "attack" : 140,
        "created" : "2013-11-03T15:05:42.097524",
        "defense" : 130,
        "height" : "24",
        "hp" : 115,
        "name" : "Rhyperior",
        "speed" : 40,
        "types" : [
                "ground",
                "rock"
        ]
}
```

## 1. Criar um index para o campo "name"

```
> db.pokemons.createIndex({name:1})
{
        "createdCollectionAutomatically" : false,
        "numIndexesBefore" : 1,
        "numIndexesAfter" : 2,
        "ok" : 1
}
```

## 2. Criar um index para dois campos juntos (qualquer campo)

```
> db.pokemons.createIndex({"defense" : 1, "height" : 1})
{
        "createdCollectionAutomatically" : false,
        "numIndexesBefore" : 2,
        "numIndexesAfter" : 3,
        "ok" : 1
}
```

Ficaram assim:

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
        },
        {
                "v" : 1,
                "key" : {
                        "defense" : 1,
                        "height" : 1
                },
                "name" : "defense_1_height_1",
                "ns" : "be-mean.pokemons"
        }
]
```

## 3. Realizar a busca com uma query sem index campo "name" e uma query com index com campo "name"

Sem index
```
> var name = {"name" : "Rhyperior"}
> db.pokemons.find(query).explain('executionStats')
{
        "queryPlanner" : {
                "plannerVersion" : 1,
                "namespace" : "be-mean.pokemons",
                "indexFilterSet" : false,
                "parsedQuery" : {
                        "name" : {
                                "$eq" : "Rhyperior"
                        }
                },
                "winningPlan" : {
                        "stage" : "COLLSCAN",
                        "filter" : {
                                "name" : {
                                        "$eq" : "Rhyperior"
                                }
                        },
                        "direction" : "forward"
                },
                "rejectedPlans" : [ ]
        },
        "executionStats" : {
                "executionSuccess" : true,
                "nReturned" : 1,
                "executionTimeMillis" : 0,
                "totalKeysExamined" : 0,
                "totalDocsExamined" : 610,
                "executionStages" : {
                        "stage" : "COLLSCAN",
                        "filter" : {
                                "name" : {
                                        "$eq" : "Rhyperior"
                                }
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
                "host" : "gabriel",
                "port" : 27017,
                "version" : "3.0.7",
                "gitVersion" : "6ce7cbe8c6b899552dadd907604559806aa2e9bd"
        },
        "ok" : 1
}
```

Com index
```
> var name = {"name" : "Rhyperior"}
> db.pokemons.find(query).explain('executionStats')
{
        "queryPlanner" : {
                "plannerVersion" : 1,
                "namespace" : "be-mean.pokemons",
                "indexFilterSet" : false,
                "parsedQuery" : {
                        "$and" : [
                                {
                                        "defense" : {
                                                "$eq" : 130
                                        }
                                },
                                {
                                        "height" : {
                                                "$eq" : "24"
                                        }
                                }
                        ]
                },
                "winningPlan" : {
                        "stage" : "FETCH",
                        "inputStage" : {
                                "stage" : "IXSCAN",
                                "keyPattern" : {
                                        "defense" : 1,
                                        "height" : 1
                                },
                                "indexName" : "defense_1_height_1",
                                "isMultiKey" : false,
                                "direction" : "forward",
                                "indexBounds" : {
                                        "defense" : [
                                                "[130.0, 130.0]"
                                        ],
                                        "height" : [
                                                "[\"24\", \"24\"]"
                                        ]
                                }
                        }
                },
                "rejectedPlans" : [ ]
        },
        "executionStats" : {
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
                        "needFetch" : 0,
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
                                "needFetch" : 0,
                                "saveState" : 0,
                                "restoreState" : 0,
                                "isEOF" : 1,
                                "invalidates" : 0,
                                "keyPattern" : {
                                        "defense" : 1,
                                        "height" : 1
                                },
                                "indexName" : "defense_1_height_1",
                                "isMultiKey" : false,
                                "direction" : "forward",
                                "indexBounds" : {
                                        "defense" : [
                                                "[130.0, 130.0]"
                                        ],
                                        "height" : [
                                                "[\"24\", \"24\"]"
                                        ]
                                },
                                "keysExamined" : 1,
                                "dupsTested" : 0,
                                "dupsDropped" : 0,
                                "seenInvalidated" : 0,
                                "matchTested" : 0
                        }
                }
        },
        "serverInfo" : {
                "host" : "gabriel",
                "port" : 27017,
                "version" : "3.0.7",
                "gitVersion" : "6ce7cbe8c6b899552dadd907604559806aa2e9bd"
        },
        "ok" : 1
}
```

## 4. Realizar a busca com uma query sem index campo para qualquer campo e uma query sem index para qualquer campo

Sem index
```
> var query = {"defense" : 130, "height" : "24"}
> db.pokemons.find(query).explain('executionStats')
{
        "queryPlanner" : {
                "plannerVersion" : 1,
                "namespace" : "be-mean.pokemons",
                "indexFilterSet" : false,
                "parsedQuery" : {
                        "$and" : [
                                {
                                        "defense" : {
                                                "$eq" : 130
                                        }
                                },
                                {
                                        "height" : {
                                                "$eq" : "24"
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
                                                        "$eq" : 130
                                                }
                                        },
                                        {
                                                "height" : {
                                                        "$eq" : "24"
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
                "nReturned" : 1,
                "executionTimeMillis" : 0,
                "totalKeysExamined" : 0,
                "totalDocsExamined" : 610,
                "executionStages" : {
                        "stage" : "COLLSCAN",
                        "filter" : {
                                "$and" : [
                                        {
                                                "defense" : {
                                                        "$eq" : 130
                                                }
                                        },
                                        {
                                                "height" : {
                                                        "$eq" : "24"
                                                }
                                        }
                                ]
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
                "host" : "gabriel",
                "port" : 27017,
                "version" : "3.0.7",
                "gitVersion" : "6ce7cbe8c6b899552dadd907604559806aa2e9bd"
        },
        "ok" : 1
}
```

Com index
```
> var query = {"defense" : 130, "height" : "24"}
> db.pokemons.find(query).explain('executionStats')
{
        "queryPlanner" : {
                "plannerVersion" : 1,
                "namespace" : "be-mean.pokemons",
                "indexFilterSet" : false,
                "parsedQuery" : {
                        "$and" : [
                                {
                                        "defense" : {
                                                "$eq" : 130
                                        }
                                },
                                {
                                        "height" : {
                                                "$eq" : "24"
                                        }
                                }
                        ]
                },
                "winningPlan" : {
                        "stage" : "FETCH",
                        "inputStage" : {
                                "stage" : "IXSCAN",
                                "keyPattern" : {
                                        "defense" : 1,
                                        "height" : 1
                                },
                                "indexName" : "defense_1_height_1",
                                "isMultiKey" : false,
                                "direction" : "forward",
                                "indexBounds" : {
                                        "defense" : [
                                                "[130.0, 130.0]"
                                        ],
                                        "height" : [
                                                "[\"24\", \"24\"]"
                                        ]
                                }
                        }
                },
                "rejectedPlans" : [ ]
        },
        "executionStats" : {
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
                        "needFetch" : 0,
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
                                "needFetch" : 0,
                                "saveState" : 0,
                                "restoreState" : 0,
                                "isEOF" : 1,
                                "invalidates" : 0,
                                "keyPattern" : {
                                        "defense" : 1,
                                        "height" : 1
                                },
                                "indexName" : "defense_1_height_1",
                                "isMultiKey" : false,
                                "direction" : "forward",
                                "indexBounds" : {
                                        "defense" : [
                                                "[130.0, 130.0]"
                                        ],
                                        "height" : [
                                                "[\"24\", \"24\"]"
                                        ]
                                },
                                "keysExamined" : 1,
                                "dupsTested" : 0,
                                "dupsDropped" : 0,
                                "seenInvalidated" : 0,
                                "matchTested" : 0
                        }
                }
        },
        "serverInfo" : {
                "host" : "gabriel",
                "port" : 27017,
                "version" : "3.0.7",
                "gitVersion" : "6ce7cbe8c6b899552dadd907604559806aa2e9bd"
        },
        "ok" : 1
}
```
