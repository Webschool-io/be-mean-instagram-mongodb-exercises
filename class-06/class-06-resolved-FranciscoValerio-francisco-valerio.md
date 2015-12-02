# MongoDB - Aula 06 - Exercício
autor: Francisco Henrique Ruiz Valério

** FOI UTILIZADO A COLEÇÃO RESTAURANTES POIS A COLEÇÃO POKEMONS SÓ TEM 610 REGISTROS NÃO DANDO DIFERENÇA NAS CONSULTAS. **

## 1. Query sem indice do campo name.

> db.restaurantes.find( { name: "Wendy'S" } ).explain('executionStats')
{
        "queryPlanner" : {
                "plannerVersion" : 1,
                "namespace" : "be-mean.restaurantes",
                "indexFilterSet" : false,
                "parsedQuery" : {
                        "name" : {
                                "$eq" : "Wendy'S"
                        }
                },
                "winningPlan" : {
                        "stage" : "COLLSCAN",
                        "filter" : {
                                "name" : {
                                        "$eq" : "Wendy'S"
                                }
                        },
                        "direction" : "forward"
                },
                "rejectedPlans" : [ ]
        },
        "executionStats" : {
                "executionSuccess" : true,
                "nReturned" : 41,
                "executionTimeMillis" : 20,
                "totalKeysExamined" : 0,
                "totalDocsExamined" : 25359,
                "executionStages" : {
                        "stage" : "COLLSCAN",
                        "filter" : {
                                "name" : {
                                        "$eq" : "Wendy'S"
                                }
                        },
                        "nReturned" : 41,
                        "executionTimeMillisEstimate" : 20,
                        "works" : 25361,
                        "advanced" : 41,
                        "needTime" : 25319,
                        "needFetch" : 0,
                        "saveState" : 198,
                        "restoreState" : 198,
                        "isEOF" : 1,
                        "invalidates" : 0,
                        "direction" : "forward",
                        "docsExamined" : 25359
                }
        },
        "serverInfo" : {
                "host" : "Francisco",
                "port" : 27017,
                "version" : "3.0.7",
                "gitVersion" : "6ce7cbe8c6b899552dadd907604559806aa2e9bd"
        },
        "ok" : 1
}

## 2. Após a criação do indice.

> db.restaurantes.createIndex( { name: 1 })
{
        "createdCollectionAutomatically" : false,
        "numIndexesBefore" : 1,
        "numIndexesAfter" : 2,
        "ok" : 1
}
> db.restaurantes.find( { name: "Wendy'S" } ).explain('executionStats')
{
        "queryPlanner" : {
                "plannerVersion" : 1,
                "namespace" : "be-mean.restaurantes",
                "indexFilterSet" : false,
                "parsedQuery" : {
                        "name" : {
                                "$eq" : "Wendy'S"
                        }
                },
                "winningPlan" : {
                        "stage" : "FETCH",
                        "inputStage" : {
                                "stage" : "IXSCAN",
                                "keyPattern" : {
                                        "name" : 1
                                },
                                "indexName" : "name_1",
                                "isMultiKey" : false,
                                "direction" : "forward",
                                "indexBounds" : {
                                        "name" : [
                                                "[\"Wendy'S\", \"Wendy'S\"]"
                                        ]
                                }
                        }
                },
                "rejectedPlans" : [ ]
        },
        "executionStats" : {
                "executionSuccess" : true,
                "nReturned" : 41,
                "executionTimeMillis" : 0,
                "totalKeysExamined" : 41,
                "totalDocsExamined" : 41,
                "executionStages" : {
                        "stage" : "FETCH",
                        "nReturned" : 41,
                        "executionTimeMillisEstimate" : 0,
                        "works" : 42,
                        "advanced" : 41,
                        "needTime" : 0,
                        "needFetch" : 0,
                        "saveState" : 0,
                        "restoreState" : 0,
                        "isEOF" : 1,
                        "invalidates" : 0,
                        "docsExamined" : 41,
                        "alreadyHasObj" : 0,
                        "inputStage" : {
                                "stage" : "IXSCAN",
                                "nReturned" : 41,
                                "executionTimeMillisEstimate" : 0,
                                "works" : 42,
                                "advanced" : 41,
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
                                                "[\"Wendy'S\", \"Wendy'S\"]"
                                        ]
                                },
                                "keysExamined" : 41,
                                "dupsTested" : 0,
                                "dupsDropped" : 0,
                                "seenInvalidated" : 0,
                                "matchTested" : 0
                        }
                }
        },
        "serverInfo" : {
                "host" : "Francisco",
                "port" : 27017,
                "version" : "3.0.7",
                "gitVersion" : "6ce7cbe8c6b899552dadd907604559806aa2e9bd"
        },
        "ok" : 1
}
>

## 3. Consulta por 2 campos sem indice.

> db.restaurantes.find( {cuisine: "Hamburgers", borough: "Brooklyn"} ).explain('executionStats')
{
        "queryPlanner" : {
                "plannerVersion" : 1,
                "namespace" : "be-mean.restaurantes",
                "indexFilterSet" : false,
                "parsedQuery" : {
                        "$and" : [
                                {
                                        "borough" : {
                                                "$eq" : "Brooklyn"
                                        }
                                },
                                {
                                        "cuisine" : {
                                                "$eq" : "Hamburgers"
                                        }
                                }
                        ]
                },
                "winningPlan" : {
                        "stage" : "COLLSCAN",
                        "filter" : {
                                "$and" : [
                                        {
                                                "borough" : {
                                                        "$eq" : "Brooklyn"
                                                }
                                        },
                                        {
                                                "cuisine" : {
                                                        "$eq" : "Hamburgers"
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
                "nReturned" : 102,
                "executionTimeMillis" : 20,
                "totalKeysExamined" : 0,
                "totalDocsExamined" : 25359,
                "executionStages" : {
                        "stage" : "COLLSCAN",
                        "filter" : {
                                "$and" : [
                                        {
                                                "borough" : {
                                                        "$eq" : "Brooklyn"
                                                }
                                        },
                                        {
                                                "cuisine" : {
                                                        "$eq" : "Hamburgers"
                                                }
                                        }
                                ]
                        },
                        "nReturned" : 102,
                        "executionTimeMillisEstimate" : 20,
                        "works" : 25361,
                        "advanced" : 102,
                        "needTime" : 25258,
                        "needFetch" : 0,
                        "saveState" : 198,
                        "restoreState" : 198,
                        "isEOF" : 1,
                        "invalidates" : 0,
                        "direction" : "forward",
                        "docsExamined" : 25359
                }
        },
        "serverInfo" : {
                "host" : "Francisco",
                "port" : 27017,
                "version" : "3.0.7",
                "gitVersion" : "6ce7cbe8c6b899552dadd907604559806aa2e9bd"
        },
        "ok" : 1
}
>


## 4. Após criação de indice composto.

> db.restaurantes.createIndex( { cuisine: 1, borough: 1 })
{
        "createdCollectionAutomatically" : false,
        "numIndexesBefore" : 2,
        "numIndexesAfter" : 3,
        "ok" : 1
}
> db.restaurantes.find( {cuisine: "Hamburgers", borough: "Brooklyn"} ).explain('executionStats')
{
        "queryPlanner" : {
                "plannerVersion" : 1,
                "namespace" : "be-mean.restaurantes",
                "indexFilterSet" : false,
                "parsedQuery" : {
                        "$and" : [
                                {
                                        "borough" : {
                                                "$eq" : "Brooklyn"
                                        }
                                },
                                {
                                        "cuisine" : {
                                                "$eq" : "Hamburgers"
                                        }
                                }
                        ]
                },
                "winningPlan" : {
                        "stage" : "FETCH",
                        "inputStage" : {
                                "stage" : "IXSCAN",
                                "keyPattern" : {
                                        "cuisine" : 1,
                                        "borough" : 1
                                },
                                "indexName" : "cuisine_1_borough_1",
                                "isMultiKey" : false,
                                "direction" : "forward",
                                "indexBounds" : {
                                        "cuisine" : [
                                                "[\"Hamburgers\", \"Hamburgers\"]"
                                        ],
                                        "borough" : [
                                                "[\"Brooklyn\", \"Brooklyn\"]"
                                        ]
                                }
                        }
                },
                "rejectedPlans" : [ ]
        },
        "executionStats" : {
                "executionSuccess" : true,
                "nReturned" : 102,
                "executionTimeMillis" : 0,
                "totalKeysExamined" : 102,
                "totalDocsExamined" : 102,
                "executionStages" : {
                        "stage" : "FETCH",
                        "nReturned" : 102,
                        "executionTimeMillisEstimate" : 0,
                        "works" : 103,
                        "advanced" : 102,
                        "needTime" : 0,
                        "needFetch" : 0,
                        "saveState" : 0,
                        "restoreState" : 0,
                        "isEOF" : 1,
                        "invalidates" : 0,
                        "docsExamined" : 102,
                        "alreadyHasObj" : 0,
                        "inputStage" : {
                                "stage" : "IXSCAN",
                                "nReturned" : 102,
                                "executionTimeMillisEstimate" : 0,
                                "works" : 103,
                                "advanced" : 102,
                                "needTime" : 0,
                                "needFetch" : 0,
                                "saveState" : 0,
                                "restoreState" : 0,
                                "isEOF" : 1,
                                "invalidates" : 0,
                                "keyPattern" : {
                                        "cuisine" : 1,
                                        "borough" : 1
                                },
                                "indexName" : "cuisine_1_borough_1",
                                "isMultiKey" : false,
                                "direction" : "forward",
                                "indexBounds" : {
                                        "cuisine" : [
                                                "[\"Hamburgers\", \"Hamburgers\"]"
                                        ],
                                        "borough" : [
                                                "[\"Brooklyn\", \"Brooklyn\"]"
                                        ]
                                },
                                "keysExamined" : 102,
                                "dupsTested" : 0,
                                "dupsDropped" : 0,
                                "seenInvalidated" : 0,
                                "matchTested" : 0
                        }
                }
        },
        "serverInfo" : {
                "host" : "Francisco",
                "port" : 27017,
                "version" : "3.0.7",
                "gitVersion" : "6ce7cbe8c6b899552dadd907604559806aa2e9bd"
        },
        "ok" : 1
}
>


