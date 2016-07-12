## MongoDb Aula - 06

Autor: Ricardo Pieroni Costa

## 1. Fazer uma query por nome sem "indexização" utilzando o explain
```
db.restaurantes.find({"name" : "Mrs. Kim'S"}).explain("executionStats")
{
        "queryPlanner" : {
                "plannerVersion" : 1,
                "namespace" : "be-mean.restaurantes",
                "indexFilterSet" : false,
                "parsedQuery" : {
                        "name" : {
                                "$eq" : "Mrs. Kim'S"
                        }
                },
                "winningPlan" : {
                        "stage" : "COLLSCAN",
                        "filter" : {
                                "name" : {
                                        "$eq" : "Mrs. Kim'S"
                                }
                        },
                        "direction" : "forward"
                },
                "rejectedPlans" : [ ]
        },
        "executionStats" : {
                "executionSuccess" : true,
                "nReturned" : 1,
                "executionTimeMillis" : 36,
                "totalKeysExamined" : 0,
                "totalDocsExamined" : 25359,
                "executionStages" : {
                        "stage" : "COLLSCAN",
                        "filter" : {
                                "name" : {
                                        "$eq" : "Mrs. Kim'S"
                                }
                        },
                        "nReturned" : 1,
                        "executionTimeMillisEstimate" : 0,
                        "works" : 25361,
                        "advanced" : 1,
                        "needTime" : 25359,
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
                "host" : "Pieroni-PC",
                "port" : 27017,
                "version" : "3.2.4",
                "gitVersion" : "e2ee9ffcf9f5a94fad76802e28cc978718bb7a30"
        },
        "ok" : 1
}

```
## 2. Criar um Index pelo nome e fazer uma query  utilzando o explain
```
 db.restaurantes.createIndex({name:1})
{
        "createdCollectionAutomatically" : false,
        "numIndexesBefore" : 1,
        "numIndexesAfter" : 2,
        "ok" : 1
}

 db.restaurantes.find({"name" : "Mrs. Kim'S"}).explain("executionStats")
{
        "queryPlanner" : {
                "plannerVersion" : 1,
                "namespace" : "be-mean.restaurantes",
                "indexFilterSet" : false,
                "parsedQuery" : {
                        "name" : {
                                "$eq" : "Mrs. Kim'S"
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
                                                "[\"Mrs. Kim'S\", \"Mrs. Kim'S\"]"
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
                                                "[\"Mrs. Kim'S\", \"Mrs. Kim'S\"]"
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
                "host" : "Pieroni-PC",
                "port" : 27017,
                "version" : "3.2.4",
                "gitVersion" : "e2ee9ffcf9f5a94fad76802e28cc978718bb7a30"
        },
        "ok" : 1
}
>
       
```
## 3. Fazer uma query de dois campos juntos sem "indexização" utilzando o explain
```
> db.restaurantes.find({"borough" : "Brooklyn",cuisine:"Korean"}).explain("executionStats")
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
                                                "$eq" : "Korean"
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
                                                        "$eq" : "Korean"
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
                "nReturned" : 16,
                "executionTimeMillis" : 37,
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
                                                        "$eq" : "Korean"
                                                }
                                        }
                                ]
                        },
                        "nReturned" : 16,
                        "executionTimeMillisEstimate" : 0,
                        "works" : 25361,
                        "advanced" : 16,
                        "needTime" : 25344,
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
                "host" : "Pieroni-PC",
                "port" : 27017,
                "version" : "3.2.4",
                "gitVersion" : "e2ee9ffcf9f5a94fad76802e28cc978718bb7a30"
        },
        "ok" : 1
}
>

```
## 4.  Fazer uma query pela index dupla criada,  utilzando o explain

```

db.restaurantes.createIndex({borough:1,cuisine:1})
{
        "createdCollectionAutomatically" : false,
        "numIndexesBefore" : 2,
        "numIndexesAfter" : 3,
        "ok" : 1
}

db.restaurantes.find({"borough" : "Brooklyn",cuisine:"Korean"}).explain("executionStats")
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
                                                "$eq" : "Korean"
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
                                                "[\"Korean\", \"Korean\"]"
                                        ]
                                }
                        }
                },
                "rejectedPlans" : [ ]
        },
        "executionStats" : {
                "executionSuccess" : true,
                "nReturned" : 16,
                "executionTimeMillis" : 0,
                "totalKeysExamined" : 16,
                "totalDocsExamined" : 16,
                "executionStages" : {
                        "stage" : "FETCH",
                        "nReturned" : 16,
                        "executionTimeMillisEstimate" : 0,
                        "works" : 17,
                        "advanced" : 16,
                        "needTime" : 0,
                        "needYield" : 0,
                        "saveState" : 0,
                        "restoreState" : 0,
                        "isEOF" : 1,
                        "invalidates" : 0,
                        "docsExamined" : 16,
                        "alreadyHasObj" : 0,
                        "inputStage" : {
                                "stage" : "IXSCAN",
                                "nReturned" : 16,
                                "executionTimeMillisEstimate" : 0,
                                "works" : 17,
                                "advanced" : 16,
                                "needTime" : 0,
                                "needYield" : 0,
                                "saveState" : 0,
                                "restoreState" : 0,
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
                                                "[\"Korean\", \"Korean\"]"
                                        ]
                                },
                                "keysExamined" : 16,
                                "dupsTested" : 0,
                                "dupsDropped" : 0,
                                "seenInvalidated" : 0
                        }
                }
        },
        "serverInfo" : {
                "host" : "Pieroni-PC",
                "port" : 27017,
                "version" : "3.2.4",
                "gitVersion" : "e2ee9ffcf9f5a94fad76802e28cc978718bb7a30"
        },
        "ok" : 1
}


```
