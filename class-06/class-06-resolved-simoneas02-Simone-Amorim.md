# MongoDB - Aula 06 - Exercício
Autor: Simone Amorim

##1. Fazer uma query para o campo `name` utilizando `explain` para ver o resultado da busca.
```javascript
db.pokemons.find({"name" : "Seel"}).explain('executionStats')
{
        "queryPlanner" : {
                "plannerVersion" : 1,
                "namespace" : "be-mean-instagram.pokemons",
                "indexFilterSet" : false,
                "parsedQuery" : {
                        "name" : {
                                "$eq" : "Seel"
                        }
                },
                "winningPlan" : {
                        "stage" : "COLLSCAN",
                        "filter" : {
                                "name" : {
                                        "$eq" : "Seel"
                                }
                        },
                        "direction" : "forward"
                },
                "rejectedPlans" : [ ]
        },
        "executionStats" : {
                "executionSuccess" : true,
                "nReturned" : 1,
                "executionTimeMillis" : 44,
                "totalKeysExamined" : 0,
                "totalDocsExamined" : 610,
                "executionStages" : {
                        "stage" : "COLLSCAN",
                        "filter" : {
                                "name" : {
                                        "$eq" : "Seel"
                                }
                        },
                        "nReturned" : 1,
                        "executionTimeMillisEstimate" : 40,
                        "works" : 612,
                        "advanced" : 1,
                        "needTime" : 610,
                        "needFetch" : 0,
                        "saveState" : 5,
                        "restoreState" : 5,
                        "isEOF" : 1,
                        "invalidates" : 0,
                        "direction" : "forward",
                        "docsExamined" : 610
                }
        },
        "serverInfo" : {
                "host" : "simoneas02",
                "port" : 27017,
                "version" : "3.0.7",
                "gitVersion" : "6ce7cbe8c6b899552dadd907604559806aa2e9bd"
        },
        "ok" : 1
}
```
<br/>

##2. Criar um `index` um para o campo `name`.
```javascript
db.pokemons.createIndex({name: 1})
{
        "createdCollectionAutomatically" : false,
        "numIndexesBefore" : 1,
        "numIndexesAfter" : 2,
        "ok" : 1
}
```
<br/>

##3. Refazer a query para o campo `name` utilizando `explain` para ver o resultado da busca.
```javascript
db.pokemons.find({"name" : "Rattata", attack: {$gte: 50}}).explain('executionStats')
{
        "queryPlanner" : {
                "plannerVersion" : 1,
                "namespace" : "be-mean-instagram.pokemons",
                "indexFilterSet" : false,
                "parsedQuery" : {
                        "$and" : [
                                {
                                        "name" : {
                                                "$eq" : "Rattata"
                                        }
                                },
                                {
                                        "attack" : {
                                                "$gte" : 50
                                        }
                                }
                        ]
                },
                "winningPlan" : {
                        "stage" : "KEEP_MUTATIONS",
                        "inputStage" : {
                                "stage" : "FETCH",
                                "filter" : {
                                        "attack" : {
                                                "$gte" : 50
                                        }
                                },
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
                                                        "[\"Rattata\", \"Rattata\"]"
                                                ]
                                        }
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
                        "stage" : "KEEP_MUTATIONS",
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
                        "inputStage" : {
                                "stage" : "FETCH",
                                "filter" : {
                                        "attack" : {
                                                "$gte" : 50
                                        }
                                },
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
                                                "name" : 1
                                        },
                                        "indexName" : "name_1",
                                        "isMultiKey" : false,
                                        "direction" : "forward",
                                        "indexBounds" : {
                                                "name" : [
                                                        "[\"Rattata\", \"Rattata\"]"
                                                ]
                                        },
                                        "keysExamined" : 1,
                                        "dupsTested" : 0,
                                        "dupsDropped" : 0,
                                        "seenInvalidated" : 0,
                                        "matchTested" : 0
                                }
                        }
                }
        },
        "serverInfo" : {
                "host" : "simoneas02",
                "port" : 27017,
                "version" : "3.0.7",
                "gitVersion" : "6ce7cbe8c6b899552dadd907604559806aa2e9bd"
        },
        "ok" : 1
}
```
<br/>

##4. Fazer uma query para dois campos juntos utilizando `explain` para ver o resultado da busca.
```javascript
var query = {$and: [{defense: {$lte: 50}}, {attack: {$gte: 100}}]}
db.pokemons.find(query).explain('executionStats')
{
        "queryPlanner" : {
                "plannerVersion" : 1,
                "namespace" : "be-mean-instagram.pokemons",
                "indexFilterSet" : false,
                "parsedQuery" : {
                        "$and" : [
                                {
                                        "defense" : {
                                                "$lte" : 50
                                        }
                                },
                                {
                                        "attack" : {
                                                "$gte" : 100
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
                                                        "$lte" : 50
                                                }
                                        },
                                        {
                                                "attack" : {
                                                        "$gte" : 100
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
                "nReturned" : 4,
                "executionTimeMillis" : 0,
                "totalKeysExamined" : 0,
                "totalDocsExamined" : 610,
                "executionStages" : {
                        "stage" : "COLLSCAN",
                        "filter" : {
                                "$and" : [
                                        {
                                                "defense" : {
                                                        "$lte" : 50
                                                }
                                        },
                                        {
                                                "attack" : {
                                                        "$gte" : 100
                                                }
                                        }
                                ]
                        },
                        "nReturned" : 4,
                        "executionTimeMillisEstimate" : 0,
                        "works" : 612,
                        "advanced" : 4,
                        "needTime" : 607,
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
                "host" : "simoneas02",
                "port" : 27017,
                "version" : "3.0.7",
                "gitVersion" : "6ce7cbe8c6b899552dadd907604559806aa2e9bd"
        },
        "ok" : 1
}
```
<br/>

##5. Criar um `index` para esses dois campos juntos.
```javascript
db.pokemons.createIndex({defense: 1, attack: 1})
{
        "createdCollectionAutomatically" : false,
        "numIndexesBefore" : 2,
        "numIndexesAfter" : 3,
        "ok" : 1
}
```
<br/>

##6. Refazer a query para os dois campos juntos utilizando `explain` para ver o resultado da busca.
```javascript
  db.pokemons.find(query).explain('executionStats')
{
        "queryPlanner" : {
                "plannerVersion" : 1,
                "namespace" : "be-mean-instagram.pokemons",
                "indexFilterSet" : false,
                "parsedQuery" : {
                        "$and" : [
                                {
                                        "defense" : {
                                                "$lte" : 50
                                        }
                                },
                                {
                                        "attack" : {
                                                "$gte" : 100
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
                                        "attack" : 1
                                },
                                "indexName" : "defense_1_attack_1",
                                "isMultiKey" : false,
                                "direction" : "forward",
                                "indexBounds" : {
                                        "defense" : [
                                                "[-1.#INF, 50.0]"
                                        ],
                                        "attack" : [
                                                "[100.0, 1.#INF]"
                                        ]
                                }
                        }
                },
                "rejectedPlans" : [ ]
        },
        "executionStats" : {
                "executionSuccess" : true,
                "nReturned" : 4,
                "executionTimeMillis" : 28,
                "totalKeysExamined" : 28,
                "totalDocsExamined" : 4,
                "executionStages" : {
                        "stage" : "FETCH",
                        "nReturned" : 4,
                        "executionTimeMillisEstimate" : 0,
                        "works" : 29,
                        "advanced" : 4,
                        "needTime" : 24,
                        "needFetch" : 0,
                        "saveState" : 0,
                        "restoreState" : 0,
                        "isEOF" : 1,
                        "invalidates" : 0,
                        "docsExamined" : 4,
                        "alreadyHasObj" : 0,
                        "inputStage" : {
                                "stage" : "IXSCAN",
                                "nReturned" : 4,
                                "executionTimeMillisEstimate" : 0,
                                "works" : 29,
                                "advanced" : 4,
                                "needTime" : 24,
                                "needFetch" : 0,
                                "saveState" : 0,
                                "restoreState" : 0,
                                "isEOF" : 1,
                                "invalidates" : 0,
                                "keyPattern" : {
                                        "defense" : 1,
                                        "attack" : 1
                                },
                                "indexName" : "defense_1_attack_1",
                                "isMultiKey" : false,
                                "direction" : "forward",
                                "indexBounds" : {
                                        "defense" : [
                                                "[-1.#INF, 50.0]"
                                        ],
                                        "attack" : [
                                                "[100.0, 1.#INF]"
                                        ]
                                },
                                "keysExamined" : 28,
                                "dupsTested" : 0,
                                "dupsDropped" : 0,
                                "seenInvalidated" : 0,
                                "matchTested" : 0
                        }
                }
        },
        "serverInfo" : {
                "host" : "simoneas02",
                "port" : 27017,
                "version" : "3.0.7",
                "gitVersion" : "6ce7cbe8c6b899552dadd907604559806aa2e9bd"
        },
        "ok" : 1
}
```