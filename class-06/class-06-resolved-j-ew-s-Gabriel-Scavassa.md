# MongoDB - Aula 06 - Exercício
autor: Gabriel Alves Scavassa

**1** - Buscar o campo `name` sem  utilizando `explain` 
```js
 db.restaurantes.find({"name" : "Riviera Caterer"}).explain('executionStats')
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
                        "stage" : "COLLSCAN",
                        "filter" : {
                                "name" : {
                                        "$eq" : "Riviera Caterer"
                                }
                        },
                        "direction" : "forward"
                },
                "rejectedPlans" : [ ]
        },
        "executionStats" : {
                "executionSuccess" : true,
                "nReturned" : 1,
                "executionTimeMillis" : 52,
                "totalKeysExamined" : 0,
                "totalDocsExamined" : 25359,
                "executionStages" : {
                        "stage" : "COLLSCAN",
                        "filter" : {
                                "name" : {
                                        "$eq" : "Riviera Caterer"
                                }
                        },
                        "nReturned" : 1,
                        "executionTimeMillisEstimate" : 50,
                        "works" : 25369,
                        "advanced" : 1,
                        "needTime" : 25359,
                        "needFetch" : 8,
                        "saveState" : 200,
                        "restoreState" : 200,
                        "isEOF" : 1,
                        "invalidates" : 0,
                        "direction" : "forward",
                        "docsExamined" : 25359
                }
        },
        "serverInfo" : {
                "host" : "Skvassa",
                "port" : 27017,
                "version" : "3.0.7",
                "gitVersion" : "6ce7cbe8c6b899552dadd907604559806aa2e9bd"
        },
        "ok" : 1
}
```
**2** - Criar um `índice` um para o campo `name`
```js
db.restaurantes.createIndex({"name" :1})
{
        "createdCollectionAutomatically" : false,
        "numIndexesBefore" : 1,
        "numIndexesAfter" : 2,
        "ok" : 1
}
> db.restaurantes.getIndexes()
[
        {
                "v" : 1,
                "key" : {
                        "_id" : 1
                },
                "name" : "_id_",
                "ns" : "be-mean.restaurantes"
        },
        {
                "v" : 1,
                "key" : {
                        "name" : 1
                },
                "name" : "name_1",
                "ns" : "be-mean.restaurantes"
        }
]
```
**3** - Buscar o campo `name` com índice utilizando `explain`
```js
var query = {"name" : /Riviera Caterer/i}
> db.restaurantes.find(query).pretty()
{
        "_id" : ObjectId("564231b7e3b05af6b753a120"),
        "address" : {
                "building" : "2780",
                "coord" : [
                        -73.98241999999999,
                        40.579505
                ],
                "street" : "Stillwell Avenue",
                "zipcode" : "11224"
        },
        "borough" : "Brooklyn",
        "cuisine" : "American ",
        "grades" : [
                {
                        "date" : ISODate("2014-06-10T00:00:00Z"),
                        "grade" : "A",
                        "score" : 5
                },
                {
                        "date" : ISODate("2013-06-05T00:00:00Z"),
                        "grade" : "A",
                        "score" : 7
                },
                {
                        "date" : ISODate("2012-04-13T00:00:00Z"),
                        "grade" : "A",
                        "score" : 12
                },
                {
                        "date" : ISODate("2011-10-12T00:00:00Z"),
                        "grade" : "A",
                        "score" : 12
                }
        ],
        "name" : "Riviera Caterer",
        "restaurant_id" : "40356018"
}
```
**4** - Buscar dois campos sem `índice` com explain
```js
var query = {$and :[ {"borough" : "Brooklyn"}, {"cuisine" : "American "}]}
> db.restaurantes.find(query).explain('executionStats')
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
                "executionTimeMillis" : 16,
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
                        "executionTimeMillisEstimate" : 10,
                        "works" : 25361,
                        "advanced" : 1273,
                        "needTime" : 24087,
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
                "host" : "Skvassa",
                "port" : 27017,
                "version" : "3.0.7",
                "gitVersion" : "6ce7cbe8c6b899552dadd907604559806aa2e9bd"
        },
        "ok" : 1
}
```
**5** - Criar índice para `dois campos` juntos
```js
db.restaurantes.createIndex({cuisine : 1 , borough : 1})
{
        "createdCollectionAutomatically" : false,
        "numIndexesBefore" : 2,
        "numIndexesAfter" : 3,
        "ok" : 1
}
> db.restaurantes.getIndexes()
[
        {
                "v" : 1,
                "key" : {
                        "_id" : 1
                },
                "name" : "_id_",
                "ns" : "be-mean.restaurantes"
        },
        {
                "v" : 1,
                "key" : {
                        "name" : 1
                },
                "name" : "name_1",
                "ns" : "be-mean.restaurantes"
        },
        {
                "v" : 1,
                "key" : {
                        "cuisine" : 1,
                        "borough" : 1
                },
                "name" : "cuisine_1_borough_1",
                "ns" : "be-mean.restaurantes"
        }
]

```
**6** - Busca dos `dois campos` com índice usando o `explain`
```js
db.restaurantes.find(query).explain('executionStats')
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
                                        "cuisine" : 1,
                                        "borough" : 1
                                },
                                "indexName" : "cuisine_1_borough_1",
                                "isMultiKey" : false,
                                "direction" : "forward",
                                "indexBounds" : {
                                        "cuisine" : [
                                                "[\"American \", \"American \"]"
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
                "nReturned" : 1273,
                "executionTimeMillis" : 28,
                "totalKeysExamined" : 1273,
                "totalDocsExamined" : 1273,
                "executionStages" : {
                        "stage" : "FETCH",
                        "nReturned" : 1273,
                        "executionTimeMillisEstimate" : 0,
                        "works" : 1274,
                        "advanced" : 1273,
                        "needTime" : 0,
                        "needFetch" : 0,
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
                                "needFetch" : 0,
                                "saveState" : 9,
                                "restoreState" : 9,
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
                                                "[\"American \", \"American \"]"
                                        ],
                                        "borough" : [
                                                "[\"Brooklyn\", \"Brooklyn\"]"
                                        ]
                                },
                                "keysExamined" : 1273,
                                "dupsTested" : 0,
                                "dupsDropped" : 0,
                                "seenInvalidated" : 0,
                                "matchTested" : 0
                        }
                }
        },
        "serverInfo" : {
                "host" : "Skvassa",
                "port" : 27017,
                "version" : "3.0.7",
                "gitVersion" : "6ce7cbe8c6b899552dadd907604559806aa2e9bd"
        },
        "ok" : 1
}

```