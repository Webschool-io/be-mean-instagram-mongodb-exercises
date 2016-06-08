# MongoDB - Aula 06 - Exercício
autor: Natália Nascimento de Ávila

#1. Fazer uma query para o campo name utilizando explain para ver o resultado da busca

```
var query = {name: /pikachu/i}

db.pokemons.find(query).explain('executionStats')
{
        "queryPlanner" : {
                "plannerVersion" : 1,
                "namespace" : "be-mean-pokemons.pokemons",
                "indexFilterSet" : false,
                "parsedQuery" : {
                        "name" : /pikachu/i
                },
                "winningPlan" : {
                        "stage" : "COLLSCAN",
                        "filter" : {
                                "name" : /pikachu/i
                        },
                        "direction" : "forward"
                },
                "rejectedPlans" : [ ]
        },
        "executionStats" : {
                "executionSuccess" : true,
                "nReturned" : 3,
                "executionTimeMillis" : 42,
                "totalKeysExamined" : 0,
                "totalDocsExamined" : 643,
                "executionStages" : {
                        "stage" : "COLLSCAN",
                        "filter" : {
                                "name" : /pikachu/i
                        },
                        "nReturned" : 3,
                        "executionTimeMillisEstimate" : 10,
                        "works" : 645,
                        "advanced" : 3,
                        "needTime" : 641,
                        "needYield" : 0,
                        "saveState" : 5,
                        "restoreState" : 5,
                        "isEOF" : 1,
                        "invalidates" : 0,
                        "direction" : "forward",
                        "docsExamined" : 643
                }
        },
        "serverInfo" : {
                "host" : "web25",
                "port" : 27017,
                "version" : "3.2.4",
                "gitVersion" : "e2ee9ffcf9f5a94fad76802e28cc978718bb7a30"
        },
        "ok" : 1
}


```

#2. Criar um index um para o campo name

```
db.pokemons.createIndex({name: 1})
{
        "createdCollectionAutomatically" : false,
        "numIndexesBefore" : 1,
        "numIndexesAfter" : 2,
        "ok" : 1
}

```

#3. Refazer a query para o campo name utilizando explain para ver o resultado da busca

```
var query = {name: /pikachu/i}

db.pokemons.find(query).explain('executionStats')
{
        "queryPlanner" : {
                "plannerVersion" : 1,
                "namespace" : "be-mean-pokemons.pokemons",
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
                                "isUnique" : false,
                                "isSparse" : false,
                                "isPartial" : false,
                                "indexVersion" : 1,
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
                "nReturned" : 3,
                "executionTimeMillis" : 42,
                "totalKeysExamined" : 640,
                "totalDocsExamined" : 3,
                "executionStages" : {
                        "stage" : "FETCH",
                        "nReturned" : 3,
                        "executionTimeMillisEstimate" : 40,
                        "works" : 641,
                        "advanced" : 3,
                        "needTime" : 637,
                        "needYield" : 0,
                        "saveState" : 5,
                        "restoreState" : 5,
                        "isEOF" : 1,
                        "invalidates" : 0,
                        "docsExamined" : 3,
                        "alreadyHasObj" : 0,
                        "inputStage" : {
                                "stage" : "IXSCAN",
                                "filter" : {
                                        "name" : /pikachu/i
                                },
                                "nReturned" : 3,
                                "executionTimeMillisEstimate" : 40,
                                "works" : 641,
                                "advanced" : 3,
                                "needTime" : 637,
                                "needYield" : 0,
                                "saveState" : 5,
                                "restoreState" : 5,
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
                                                "[\"\", {})",
                                                "[/pikachu/i, /pikachu/i]"
                                        ]
                                },
                                "keysExamined" : 640,
                                "dupsTested" : 0,
                                "dupsDropped" : 0,
                                "seenInvalidated" : 0
                        }
                }
        },
        "serverInfo" : {
                "host" : "web25",
                "port" : 27017,
                "version" : "3.2.4",
                "gitVersion" : "e2ee9ffcf9f5a94fad76802e28cc978718bb7a30"
        },
        "ok" : 1
}

```

#4. Fazer uma query para dois campos juntos utilizando explain para ver o resultado da busca

```
var query = {$or: [{name:/Beedrill/i}, {type: "fire"}]}

db.pokemons.find(query).explain('executionStats')
{
        "queryPlanner" : {
                "plannerVersion" : 1,
                "namespace" : "be-mean-pokemons.pokemons",
                "indexFilterSet" : false,
                "parsedQuery" : {
                        "$or" : [
                                {
                                        "type" : {
                                                "$eq" : "fire"
                                        }
                                },
                                {
                                        "name" : /Beedrill/i
                                }
                        ]
                },
                "winningPlan" : {
                        "stage" : "SUBPLAN",
                        "inputStage" : {
                                "stage" : "COLLSCAN",
                                "filter" : {
                                        "$or" : [
                                                {
                                                        "type" : {
                                                                "$eq" : "fire"
                                                        }
                                                },
                                                {
                                                        "name" : /Beedrill/i
                                                }
                                        ]
                                },
                                "direction" : "forward"
                        }
                },
                "rejectedPlans" : [ ]
        },
        "executionStats" : {
                "executionSuccess" : true,
                "nReturned" : 8,
                "executionTimeMillis" : 21,
                "totalKeysExamined" : 0,
                "totalDocsExamined" : 643,
                "executionStages" : {
                        "stage" : "SUBPLAN",
                        "nReturned" : 8,
                        "executionTimeMillisEstimate" : 20,
                        "works" : 645,
                        "advanced" : 8,
                        "needTime" : 636,
                        "needYield" : 0,
                        "saveState" : 6,
                        "restoreState" : 6,
                        "isEOF" : 1,
                        "invalidates" : 0,
                        "inputStage" : {
                                "stage" : "COLLSCAN",
                                "filter" : {
                                        "$or" : [
                                                {
                                                        "type" : {
                                                                "$eq" : "fire"
                                                        }
                                                },
                                                {
                                                        "name" : /Beedrill/i
                                                }
                                        ]
                                },
                                "nReturned" : 8,
                                "executionTimeMillisEstimate" : 0,
                                "works" : 645,
                                "advanced" : 8,
                                "needTime" : 636,
                                "needYield" : 0,
                                "saveState" : 6,
                                "restoreState" : 6,
                                "isEOF" : 1,
                                "invalidates" : 0,
                                "direction" : "forward",
                                "docsExamined" : 643
                        }
                }
        },
        "serverInfo" : {
                "host" : "web25",
                "port" : 27017,
                "version" : "3.2.4",
                "gitVersion" : "e2ee9ffcf9f5a94fad76802e28cc978718bb7a30"
        },
        "ok" : 1
}

```

#5. Criar um index para esses dois campos juntos

```
db.pokemons.createIndex({name: 1, type: 1})
{
        "createdCollectionAutomatically" : false,
        "numIndexesBefore" : 2,
        "numIndexesAfter" : 3,
        "ok" : 1
}

```

#6. Refazer a query para os dois campos juntos utilizando explain para ver o resultado da busca

```
var query = {$or: [{name:/Beedrill/i}, {type: "fire"}]}

db.pokemons.find(query).explain('executionStats')
{
        "queryPlanner" : {
                "plannerVersion" : 1,
                "namespace" : "be-mean-pokemons.pokemons",
                "indexFilterSet" : false,
                "parsedQuery" : {
                        "$or" : [
                                {
                                        "type" : {
                                                "$eq" : "fire"
                                        }
                                },
                                {
                                        "name" : /Beedrill/i
                                }
                        ]
                },
                "winningPlan" : {
                        "stage" : "SUBPLAN",
                        "inputStage" : {
                                "stage" : "COLLSCAN",
                                "filter" : {
                                        "$or" : [
                                                {
                                                        "type" : {
                                                                "$eq" : "fire"
                                                        }
                                                },
                                                {
                                                        "name" : /Beedrill/i
                                                }
                                        ]
                                },
                                "direction" : "forward"
                        }
                },
                "rejectedPlans" : [ ]
        },
        "executionStats" : {
                "executionSuccess" : true,
                "nReturned" : 8,
                "executionTimeMillis" : 1,
                "totalKeysExamined" : 0,
                "totalDocsExamined" : 643,
                "executionStages" : {
                        "stage" : "SUBPLAN",
                        "nReturned" : 8,
                        "executionTimeMillisEstimate" : 0,
                        "works" : 645,
                        "advanced" : 8,
                        "needTime" : 636,
                        "needYield" : 0,
                        "saveState" : 5,
                        "restoreState" : 5,
                        "isEOF" : 1,
                        "invalidates" : 0,
                        "inputStage" : {
                                "stage" : "COLLSCAN",
                                "filter" : {
                                        "$or" : [
                                                {
                                                        "type" : {
                                                                "$eq" : "fire"
                                                        }
                                                },
                                                {
                                                        "name" : /Beedrill/i
                                                }
                                        ]
                                },
                                "nReturned" : 8,
                                "executionTimeMillisEstimate" : 0,
                                "works" : 645,
                                "advanced" : 8,
                                "needTime" : 636,
                                "needYield" : 0,
                                "saveState" : 5,
                                "restoreState" : 5,
                                "isEOF" : 1,
                                "invalidates" : 0,
                                "direction" : "forward",
                                "docsExamined" : 643
                        }
                }
        },
        "serverInfo" : {
                "host" : "web25",
                "port" : 27017,
                "version" : "3.2.4",
                "gitVersion" : "e2ee9ffcf9f5a94fad76802e28cc978718bb7a30"
        },
        "ok" : 1
}


```
