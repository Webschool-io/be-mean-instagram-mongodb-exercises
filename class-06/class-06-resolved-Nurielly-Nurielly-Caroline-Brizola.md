# MongoDB - Aula 06 - Exercício
autor: Nurielly Caroline Brizola


# 1. Fazer uma query para o campo name utilizando explain para ver o resultado da busca
```
var query = {name: /charmander/i }
db.pokemons.find(query).explain('executionStats')

{
    "queryPlanner" : {
        "plannerVersion" : 1,
        "namespace" : "be-mean-pokemons.pokemons",
        "indexFilterSet" : false,
        "parsedQuery" : {
            "name" : /charmander/i
        },
        "winningPlan" : {
            "stage" : "FETCH",
            "inputStage" : {
                "stage" : "IXSCAN",
                "filter" : {
                    "name" : /charmander/i
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
                        "[/charmander/i, /charmander/i]"
                    ]
                }
            }
        },
        "rejectedPlans" : []
    },
    "executionStats" : {
        "executionSuccess" : true,
        "nReturned" : 1,
        "executionTimeMillis" : 29,
        "totalKeysExamined" : 610,
        "totalDocsExamined" : 1,
        "executionStages" : {
            "stage" : "FETCH",
            "nReturned" : 1,
            "executionTimeMillisEstimate" : 0,
            "works" : 611,
            "advanced" : 1,
            "needTime" : 609,
            "needFetch" : 0,
            "saveState" : 4,
            "restoreState" : 4,
            "isEOF" : 1,
            "invalidates" : 0,
            "docsExamined" : 1,
            "alreadyHasObj" : 0,
            "inputStage" : {
                "stage" : "IXSCAN",
                "filter" : {
                    "name" : /charmander/i
                },
                "nReturned" : 1,
                "executionTimeMillisEstimate" : 0,
                "works" : 610,
                "advanced" : 1,
                "needTime" : 609,
                "needFetch" : 0,
                "saveState" : 4,
                "restoreState" : 4,
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
                        "[/charmander/i, /charmander/i]"
                    ]
                },
                "keysExamined" : 610,
                "dupsTested" : 0,
                "dupsDropped" : 0,
                "seenInvalidated" : 0,
                "matchTested" : 1
            }
        }
    },
    "serverInfo" : {
        "host" : "DESKTOP-T59I0KT",
        "port" : 27017,
        "version" : "3.0.7",
        "gitVersion" : "6ce7cbe8c6b899552dadd907604559806aa2e9bd"
    },
    "ok" : 1
}
```

# 2. Criar um index um para o campo name
```
var index = {name: 1}
db.pokemons.createIndex(index)

{
    "createdCollectionAutomatically" : false,
    "numIndexesBefore" : 1,
    "numIndexesAfter" : 2,
    "ok" : 1
}
```

# 3. Refazer a query para o campo name utilizando explain para ver o resultado da busca
```
var query = {name: /charmander/i }
db.pokemons.find(query).explain('executionStats')

{
    "queryPlanner" : {
        "plannerVersion" : 1,
        "namespace" : "be-mean-pokemons.pokemons",
        "indexFilterSet" : false,
        "parsedQuery" : {
            "name" : /charmander/i
        },
        "winningPlan" : {
            "stage" : "FETCH",
            "inputStage" : {
                "stage" : "IXSCAN",
                "filter" : {
                    "name" : /charmander/i
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
                        "[/charmander/i, /charmander/i]"
                    ]
                }
            }
        },
        "rejectedPlans" : []
    },
    "executionStats" : {
        "executionSuccess" : true,
        "nReturned" : 1,
        "executionTimeMillis" : 2,
        "totalKeysExamined" : 610,
        "totalDocsExamined" : 1,
        "executionStages" : {
            "stage" : "FETCH",
            "nReturned" : 1,
            "executionTimeMillisEstimate" : 0,
            "works" : 611,
            "advanced" : 1,
            "needTime" : 609,
            "needFetch" : 0,
            "saveState" : 4,
            "restoreState" : 4,
            "isEOF" : 1,
            "invalidates" : 0,
            "docsExamined" : 1,
            "alreadyHasObj" : 0,
            "inputStage" : {
                "stage" : "IXSCAN",
                "filter" : {
                    "name" : /charmander/i
                },
                "nReturned" : 1,
                "executionTimeMillisEstimate" : 0,
                "works" : 610,
                "advanced" : 1,
                "needTime" : 609,
                "needFetch" : 0,
                "saveState" : 4,
                "restoreState" : 4,
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
                        "[/charmander/i, /charmander/i]"
                    ]
                },
                "keysExamined" : 610,
                "dupsTested" : 0,
                "dupsDropped" : 0,
                "seenInvalidated" : 0,
                "matchTested" : 1
            }
        }
    },
    "serverInfo" : {
        "host" : "DESKTOP-T59I0KT",
        "port" : 27017,
        "version" : "3.0.7",
        "gitVersion" : "6ce7cbe8c6b899552dadd907604559806aa2e9bd"
    },
    "ok" : 1
}
```

# 4. Fazer uma query para dois campos juntos utilizando explain para ver o resultado da busca
```
var query = { $or: [{name: /charmander/i }, {attack: { $lte: 50 }}]}
db.pokemons.find(query).explain('executionStats')

{
    "queryPlanner" : {
        "plannerVersion" : 1,
        "namespace" : "be-mean-pokemons.pokemons",
        "indexFilterSet" : false,
        "parsedQuery" : {
            "$or" : [ 
                {
                    "attack" : {
                        "$lte" : 50
                    }
                }, 
                {
                    "name" : /charmander/i
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
                            "attack" : {
                                "$lte" : 50
                            }
                        }, 
                        {
                            "name" : /charmander/i
                        }
                    ]
                },
                "direction" : "forward"
            }
        },
        "rejectedPlans" : []
    },
    "executionStats" : {
        "executionSuccess" : true,
        "nReturned" : 149,
        "executionTimeMillis" : 2,
        "totalKeysExamined" : 0,
        "totalDocsExamined" : 610,
        "executionStages" : {
            "stage" : "SUBPLAN",
            "nReturned" : 149,
            "executionTimeMillisEstimate" : 0,
            "works" : 612,
            "advanced" : 149,
            "needTime" : 462,
            "needFetch" : 0,
            "saveState" : 4,
            "restoreState" : 4,
            "isEOF" : 1,
            "invalidates" : 0,
            "inputStage" : {
                "stage" : "COLLSCAN",
                "filter" : {
                    "$or" : [ 
                        {
                            "attack" : {
                                "$lte" : 50
                            }
                        }, 
                        {
                            "name" : /charmander/i
                        }
                    ]
                },
                "nReturned" : 149,
                "executionTimeMillisEstimate" : 0,
                "works" : 611,
                "advanced" : 149,
                "needTime" : 462,
                "needFetch" : 0,
                "saveState" : 4,
                "restoreState" : 4,
                "isEOF" : 1,
                "invalidates" : 0,
                "direction" : "forward",
                "docsExamined" : 610
            }
        }
    },
    "serverInfo" : {
        "host" : "DESKTOP-T59I0KT",
        "port" : 27017,
        "version" : "3.0.7",
        "gitVersion" : "6ce7cbe8c6b899552dadd907604559806aa2e9bd"
    },
    "ok" : 1
}
```

# 5. Criar um index para esses dois campos juntos
```
var index = {name: 1, attack: 1}
db.pokemons.createIndex(index)

{
    "createdCollectionAutomatically" : false,
    "numIndexesBefore" : 1,
    "numIndexesAfter" : 2,
    "ok" : 1
}
```

# 6. Refazer a query para os dois campos juntos utilizando explain para ver o resultado da busca
```
var query = { $or: [{name: /charmander/i }, {attack: { $lte: 50 }}]}
db.pokemons.find(query).explain('executionStats')

{
    "queryPlanner" : {
        "plannerVersion" : 1,
        "namespace" : "be-mean-pokemons.pokemons",
        "indexFilterSet" : false,
        "parsedQuery" : {
            "$or" : [ 
                {
                    "attack" : {
                        "$lte" : 50
                    }
                }, 
                {
                    "name" : /charmander/i
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
                            "attack" : {
                                "$lte" : 50
                            }
                        }, 
                        {
                            "name" : /charmander/i
                        }
                    ]
                },
                "direction" : "forward"
            }
        },
        "rejectedPlans" : []
    },
    "executionStats" : {
        "executionSuccess" : true,
        "nReturned" : 149,
        "executionTimeMillis" : 0,
        "totalKeysExamined" : 0,
        "totalDocsExamined" : 610,
        "executionStages" : {
            "stage" : "SUBPLAN",
            "nReturned" : 149,
            "executionTimeMillisEstimate" : 0,
            "works" : 612,
            "advanced" : 149,
            "needTime" : 462,
            "needFetch" : 0,
            "saveState" : 4,
            "restoreState" : 4,
            "isEOF" : 1,
            "invalidates" : 0,
            "inputStage" : {
                "stage" : "COLLSCAN",
                "filter" : {
                    "$or" : [ 
                        {
                            "attack" : {
                                "$lte" : 50
                            }
                        }, 
                        {
                            "name" : /charmander/i
                        }
                    ]
                },
                "nReturned" : 149,
                "executionTimeMillisEstimate" : 0,
                "works" : 611,
                "advanced" : 149,
                "needTime" : 462,
                "needFetch" : 0,
                "saveState" : 4,
                "restoreState" : 4,
                "isEOF" : 1,
                "invalidates" : 0,
                "direction" : "forward",
                "docsExamined" : 610
            }
        }
    },
    "serverInfo" : {
        "host" : "DESKTOP-T59I0KT",
        "port" : 27017,
        "version" : "3.0.7",
        "gitVersion" : "6ce7cbe8c6b899552dadd907604559806aa2e9bd"
    },
    "ok" : 1
}
```