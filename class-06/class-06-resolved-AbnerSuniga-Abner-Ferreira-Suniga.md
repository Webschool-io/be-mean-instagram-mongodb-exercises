#MongoDB - Aula 06 - Exercícios
autor: Abner Ferreira Suniga

##1. Fazer uma query para o campo `name` utilizando `explain` para ver o resultado da busca

```
> db.restaurantes.find({"name" : "Riviera Caterer"}).explain("executionStats")
{
        "queryPlanner" : {
                "plannerVersion" : 1,
                "namespace" : "be-mean.restaurantes",
                "indexFilterSet" : false,
                "parsedQuery" : {
                        "name" : {
                                "$eq" : "Riviera Caterer"
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
                                "isUnique" : false,
                                "isSparse" : false,
                                "isPartial" : false,
                                "indexVersion" : 1,
                                "direction" : "forward",
                                "indexBounds" : {
                                        "name" : [
                                                "[\"Riviera Caterer\", \"Riviera Caterer\"]"
                                        ]
                                }
                        }
                },
                "rejectedPlans" : [ ]
        },
        "executionStats" : {
                "executionSuccess" : true,
                "nReturned" : 1,
                "executionTimeMillis" : 80,
                "totalKeysExamined" : 1,
                "totalDocsExamined" : 1,
                "executionStages" : {
                        "stage" : "FETCH",
                        "nReturned" : 1,
                        "executionTimeMillisEstimate" : 80,
                        "works" : 2,
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
                                "executionTimeMillisEstimate" : 80,
                                "works" : 2,
                                "advanced" : 1,
                                "needTime" : 0,
                                "needYield" : 0,
                                "saveState" : 1,
                                "restoreState" : 1,
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
                                                "[\"Riviera Caterer\", \"Riviera Caterer\"]"
                                        ]
                                },
                                "keysExamined" : 1,
                                "dupsTested" : 0,
                                "dupsDropped" : 0,
                                "seenInvalidated" : 0
                        }
                }
        },
        "serverInfo" : {
                "host" : "Abner-PC",
                "port" : 27017,
                "version" : "3.2.8",
                "gitVersion" : "ed70e33130c977bda0024c125b56d159573dbaf0"
        },
        "ok" : 1
}
>
```

##2. Criar um `index` um para o campo `name`

```
> db.restaurantes.createIndex({name:1})
{
        "createdCollectionAutomatically" : false,
        "numIndexesBefore" : 2,
        "numIndexesAfter" : 2,
        "note" : "all indexes already exist",
        "ok" : 1
}
```

##3. Refazer a query para o campo `name` utilizando `explain` para ver o resultado da busca

```
> db.restaurantes.find({"name" : "Riviera Caterer"}).explain("executionStats")
{
        "queryPlanner" : {
                "plannerVersion" : 1,
                "namespace" : "be-mean.restaurantes",
                "indexFilterSet" : false,
                "parsedQuery" : {
                        "name" : {
                                "$eq" : "Riviera Caterer"
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
                                "isUnique" : false,
                                "isSparse" : false,
                                "isPartial" : false,
                                "indexVersion" : 1,
                                "direction" : "forward",
                                "indexBounds" : {
                                        "name" : [
                                                "[\"Riviera Caterer\", \"Riviera Caterer\"]"
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
                                                "[\"Riviera Caterer\", \"Riviera Caterer\"]"
                                        ]
                                },
                                "keysExamined" : 1,
                                "dupsTested" : 0,
                                "dupsDropped" : 0,
                                "seenInvalidated" : 0
                        }
                }
        },
        "serverInfo" : {
                "host" : "Abner-PC",
                "port" : 27017,
                "version" : "3.2.8",
                "gitVersion" : "ed70e33130c977bda0024c125b56d159573dbaf0"
        },
        "ok" : 1
}
>
```

##4. Fazer uma query para dois campos juntos utilizando `explain` para ver o resultado da busca

```
> db.restaurantes.find({$and: [{borough:"Brooklyn"},{cuisine:"American "}]}).explain("e
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
                                                "$eq" : "American "
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
                                                        "$eq" : "American "
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
                "nReturned" : 1273,
                "executionTimeMillis" : 38,
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
                                                        "$eq" : "American "
                                                }
                                        }
                                ]
                        },
                        "nReturned" : 1273,
                        "executionTimeMillisEstimate" : 40,
                        "works" : 25361,
                        "advanced" : 1273,
                        "needTime" : 24087,
                        "needYield" : 0,
                        "saveState" : 198,
                        "restoreState" : 198,
                        "isEOF" : 1,
                        "invalidates" : 0,
                        "direction" : "forward",
                        "docsExamined" : 25359
                }
        },
        "serverInfo" : {
                "host" : "Abner-PC",
                "port" : 27017,
                "version" : "3.2.8",
                "gitVersion" : "ed70e33130c977bda0024c125b56d159573dbaf0"
        },
        "ok" : 1
}
>
```

##5. Criar um `index` para esses dois campos juntos

```
> db.restaurantes.createIndex({borough: 1,cuisine: 1})
{
        "createdCollectionAutomatically" : false,
        "numIndexesBefore" : 2,
        "numIndexesAfter" : 3,
        "ok" : 1
}
>
```

##6. Refazer a query para os dois campos juntos utilizando `explain` para ver o resultado da busca

```
> db.restaurantes.find({$and: [{borough:"Brooklyn"},{cuisine:"American "}]}).explain("executionStats")
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
                                                "$eq" : "American "
                                        }
                                }
                        ]
                },
                "winningPlan" : {
                        "stage" : "FETCH",
                        "inputStage" : {
                                "stage" : "IXSCAN",
                                "keyPattern" : {
                                        "borough" : 1,
                                        "cuisine" : 1
                                },
                                "indexName" : "borough_1_cuisine_1",
                                "isMultiKey" : false,
                                "isUnique" : false,
                                "isSparse" : false,
                                "isPartial" : false,
                                "indexVersion" : 1,
                                "direction" : "forward",
                                "indexBounds" : {
                                        "borough" : [
                                                "[\"Brooklyn\", \"Brooklyn\"]"
                                        ],
                                        "cuisine" : [
                                                "[\"American \", \"American \"]"
                                        ]
                                }
                        }
                },
                "rejectedPlans" : [ ]
        },
        "executionStats" : {
                "executionSuccess" : true,
                "nReturned" : 1273,
                "executionTimeMillis" : 10,
                "totalKeysExamined" : 1273,
                "totalDocsExamined" : 1273,
                "executionStages" : {
                        "stage" : "FETCH",
                        "nReturned" : 1273,
                        "executionTimeMillisEstimate" : 10,
                        "works" : 1274,
                        "advanced" : 1273,
                        "needTime" : 0,
                        "needYield" : 0,
                        "saveState" : 9,
                        "restoreState" : 9,
                        "isEOF" : 1,
                        "invalidates" : 0,
                        "docsExamined" : 1273,
                        "alreadyHasObj" : 0,
                        "inputStage" : {
                                "stage" : "IXSCAN",
                                "nReturned" : 1273,
                                "executionTimeMillisEstimate" : 0,
                                "works" : 1274,
                                "advanced" : 1273,
                                "needTime" : 0,
                                "needYield" : 0,
                                "saveState" : 9,
                                "restoreState" : 9,
                                "isEOF" : 1,
                                "invalidates" : 0,
                                "keyPattern" : {
                                        "borough" : 1,
                                        "cuisine" : 1
                                },
                                "indexName" : "borough_1_cuisine_1",
                                "isMultiKey" : false,
                                "isUnique" : false,
                                "isSparse" : false,
                                "isPartial" : false,
                                "indexVersion" : 1,
                                "direction" : "forward",
                                "indexBounds" : {
                                        "borough" : [
                                                "[\"Brooklyn\", \"Brooklyn\"]"
                                        ],
                                        "cuisine" : [
                                                "[\"American \", \"American \"]"
                                        ]
                                },
                                "keysExamined" : 1273,
                                "dupsTested" : 0,
                                "dupsDropped" : 0,
                                "seenInvalidated" : 0
                        }
                }
        },
        "serverInfo" : {
                "host" : "Abner-PC",
                "port" : 27017,
                "version" : "3.2.8",
                "gitVersion" : "ed70e33130c977bda0024c125b56d159573dbaf0"
        },
        "ok" : 1
```
