# MongoDB - Aula 06 - Exercício
autor: Leonardo Barbosa de Oliveira


## 1. Fazer uma query para o campo name utilizando explain para ver o resultado da busca


--

	db.novospokemons.find({name:"charmeleon"}).explain("executionStats")
	{
	        "queryPlanner" : {
	                "plannerVersion" : 1,
	                "namespace" : "be-mean-pokemons.novospokemons",
	                "indexFilterSet" : false,
	                "parsedQuery" : {
	                        "name" : {
	                                "$eq" : "charmeleon"
	                        }
	                },
	                "winningPlan" : {
	                        "stage" : "COLLSCAN",
	                        "filter" : {
	                                "name" : {
	                                        "$eq" : "charmeleon"
	                                }
	                        },
	                        "direction" : "forward"
	                },
	                "rejectedPlans" : [ ]
	        },
	        "executionStats" : {
	                "executionSuccess" : true,
	                "nReturned" : 0,
	                "executionTimeMillis" : 1,
	                "totalKeysExamined" : 0,
	                "totalDocsExamined" : 610,
	                "executionStages" : {
	                        "stage" : "COLLSCAN",
	                        "filter" : {
	                                "name" : {
	                                        "$eq" : "charmeleon"
	                                }
	                        },
	                        "nReturned" : 0,
	                        "executionTimeMillisEstimate" : 0,
	                        "works" : 612,
	                        "advanced" : 0,
	                        "needTime" : 611,
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
	                "host" : "Leonardo",
	                "port" : 27017,
	                "version" : "3.0.7",
	                "gitVersion" : "6ce7cbe8c6b899552dadd907604559806aa2e9bd"
	        },
	        "ok" : 1
	}
	
## 2.  Criar um index um para o campo name

	
	db.novospokemons.createIndex({name:1})
	{
	        "createdCollectionAutomatically" : false,
	        "numIndexesBefore" : 1,
	        "numIndexesAfter" : 2,
	        "ok" : 1
	}
	

## 3. Refazer a query para o campo name utilizando explain para ver o resultado da busca

	db.novospokemons.find({name:"charmeleon"}).explain("executionStats")
	{
	        "queryPlanner" : {
	                "plannerVersion" : 1,
	                "namespace" : "be-mean-pokemons.novospokemons",
	                "indexFilterSet" : false,
	                "parsedQuery" : {
	                        "name" : {
	                                "$eq" : "charmeleon"
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
	                                                "[\"charmeleon\", \"charmeleon\"]"
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
	                                                "[\"charmeleon\", \"charmeleon\"]"
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
	                "host" : "Leonardo",
	                "port" : 27017,
	                "version" : "3.0.7",
	                "gitVersion" : "6ce7cbe8c6b899552dadd907604559806aa2e9bd"
	        },
	        "ok" : 1
	}
	>

## 4. Fazer uma query para dois campos juntos utilizando explain para ver o resultado da busca

	db.novospokemons.find({ $and:[ { height: { $gt: 10 } }, { speed: { $gt:50 } } ] }).explain('executionStats')
	{
	        "queryPlanner" : {
	                "plannerVersion" : 1,
	                "namespace" : "be-mean-pokemons.novospokemons",
	                "indexFilterSet" : false,
	                "parsedQuery" : {
	                        "$and" : [
	                                {
	                                        "height" : {
	                                                "$gt" : 10
	                                        }
	                                },
	                                {
	                                        "speed" : {
	                                                "$gt" : 50
	                                        }
	                                }
	                        ]
	                },
	                "winningPlan" : {
	                        "stage" : "COLLSCAN",
	                        "filter" : {
	                                "$and" : [
	                                        {
	                                                "height" : {
	                                                        "$gt" : 10
	                                                }
	                                        },
	                                        {
	                                                "speed" : {
	                                                        "$gt" : 50
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
	                "nReturned" : 0,
	                "executionTimeMillis" : 0,
	                "totalKeysExamined" : 0,
	                "totalDocsExamined" : 610,
	                "executionStages" : {
	                        "stage" : "COLLSCAN",
	                        "filter" : {
	                                "$and" : [
	                                        {
	                                                "height" : {
	                                                        "$gt" : 10
	                                                }
	                                        },
	                                        {
	                                                "speed" : {
	                                                        "$gt" : 50
	                                                }
	                                        }
	                                ]
	                        },
	                        "nReturned" : 0,
	                        "executionTimeMillisEstimate" : 0,
	                        "works" : 612,
	                        "advanced" : 0,
	                        "needTime" : 611,
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
	                "host" : "Leonardo",
	                "port" : 27017,
	                "version" : "3.0.7",
	                "gitVersion" : "6ce7cbe8c6b899552dadd907604559806aa2e9bd"
	        },
	        "ok" : 1
	}
	

## 5. Criar um index para esses dois campos juntos
	
	db.novos.pokemons.createIndex({height:1, speed:1})
	{
	        "createdCollectionAutomatically" : true,
	        "numIndexesBefore" : 1,
	        "numIndexesAfter" : 2,
	        "ok" : 1
	}

## 6. Refazer a query para os dois campos juntos utilizando o explain para ver o resultado da busca
	
	db.novospokemons.find({ $and:[ { height: { $gt: 10 } }, { speed: { $gt:50 } } ] }).explain('executionStats')
	{
	        "queryPlanner" : {
	                "plannerVersion" : 1,
	                "namespace" : "be-mean-pokemons.novospokemons",
	                "indexFilterSet" : false,
	                "parsedQuery" : {
	                        "$and" : [
	                                {
	                                        "height" : {
	                                                "$gt" : 10
	                                        }
	                                },
	                                {
	                                        "speed" : {
	                                                "$gt" : 50
	                                        }
	                                }
	                        ]
	                },
	                "winningPlan" : {
	                        "stage" : "COLLSCAN",
	                        "filter" : {
	                                "$and" : [
	                                        {
	                                                "height" : {
	                                                        "$gt" : 10
	                                                }
	                                        },
	                                        {
	                                                "speed" : {
	                                                        "$gt" : 50
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
	                "nReturned" : 0,
	                "executionTimeMillis" : 0,
	                "totalKeysExamined" : 0,
	                "totalDocsExamined" : 610,
	                "executionStages" : {
	                        "stage" : "COLLSCAN",
	                        "filter" : {
	                                "$and" : [
	                                        {
	                                                "height" : {
	                                                        "$gt" : 10
	                                                }
	                                        },
	                                        {
	                                                "speed" : {
	                                                        "$gt" : 50
	                                                }
	                                        }
	                                ]
	                        },
	                        "nReturned" : 0,
	                        "executionTimeMillisEstimate" : 0,
	                        "works" : 612,
	                        "advanced" : 0,
	                        "needTime" : 611,
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
	                "host" : "Leonardo",
	                "port" : 27017,
	                "version" : "3.0.7",
	                "gitVersion" : "6ce7cbe8c6b899552dadd907604559806aa2e9bd"
	        },
	        "ok" : 1
	}
