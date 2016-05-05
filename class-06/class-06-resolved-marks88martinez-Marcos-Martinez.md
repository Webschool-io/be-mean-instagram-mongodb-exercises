# MongoDB - Aula 06 - Exercícios
autor : Marcos Antonio Martinez

## 1 . Buscar antes e dopois do indexe `name`
```
> var explain = db.pokemons.explain('executionStats');
> explain.find({name: /squirtle/i})
{
	"queryPlanner" : {
		"plannerVersion" : 1,
		"namespace" : "be-mean-pokemons.pokemons",
		"indexFilterSet" : false,
		"parsedQuery" : {
			"name" : /squirtle/i
		},
		"winningPlan" : {
			"stage" : "COLLSCAN",
			"filter" : {
				"name" : /squirtle/i
			},
			"direction" : "forward"
		},
		"rejectedPlans" : [ ]
	},
	"executionStats" : {
		"executionSuccess" : true,
		"nReturned" : 1,
		"executionTimeMillis" : 39,
		"totalKeysExamined" : 0,
		"totalDocsExamined" : 8,
		"executionStages" : {
			"stage" : "COLLSCAN",
			"filter" : {
				"name" : /squirtle/i
			},
			"nReturned" : 1,
			"executionTimeMillisEstimate" : 0,
			"works" : 10,
			"advanced" : 1,
			"needTime" : 8,
			"needFetch" : 0,
			"saveState" : 0,
			"restoreState" : 0,
			"isEOF" : 1,
			"invalidates" : 0,
			"direction" : "forward",
			"docsExamined" : 8
		}
	},
	"serverInfo" : {
		"host" : "mark-HP-Pavilion-dv6-Notebook-PC",
		"port" : 27017,
		"version" : "3.0.7",
		"gitVersion" : "6ce7cbe8c6b899552dadd907604559806aa2e9bd"
	},
	"ok" : 1
}

> db.pokemons.getIndexes()
[
	{
		"v" : 1,
		"key" : {
			"_id" : 1
		},
		"name" : "_id_",
		"ns" : "be-mean-pokemons.pokemons"
	}
]

> db.pokemons.createIndex({name:1})
{
	"createdCollectionAutomatically" : false,
	"numIndexesBefore" : 1,
	"numIndexesAfter" : 2,
	"ok" : 1
}


> var explain = db.pokemons.explain('executionStats');
> explain.find({name: /squirtle/i})
{
	"queryPlanner" : {
		"plannerVersion" : 1,
		"namespace" : "be-mean-pokemons.pokemons",
		"indexFilterSet" : false,
		"parsedQuery" : {
			"name" : /squirtle/i
		},
		"winningPlan" : {
			"stage" : "FETCH",
			"inputStage" : {
				"stage" : "IXSCAN",
				"filter" : {
					"name" : /squirtle/i
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
						"[/squirtle/i, /squirtle/i]"
					]
				}
			}
		},
		"rejectedPlans" : [ ]
	},
	"executionStats" : {
		"executionSuccess" : true,
		"nReturned" : 1,
		"executionTimeMillis" : 29,
		"totalKeysExamined" : 7,
		"totalDocsExamined" : 1,
		"executionStages" : {
			"stage" : "FETCH",
			"nReturned" : 1,
			"executionTimeMillisEstimate" : 0,
			"works" : 8,
			"advanced" : 1,
			"needTime" : 6,
			"needFetch" : 0,
			"saveState" : 0,
			"restoreState" : 0,
			"isEOF" : 1,
			"invalidates" : 0,
			"docsExamined" : 1,
			"alreadyHasObj" : 0,
			"inputStage" : {
				"stage" : "IXSCAN",
				"filter" : {
					"name" : /squirtle/i
				},
				"nReturned" : 1,
				"executionTimeMillisEstimate" : 0,
				"works" : 7,
				"advanced" : 1,
				"needTime" : 6,
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
						"[\"\", {})",
						"[/squirtle/i, /squirtle/i]"
					]
				},
				"keysExamined" : 7,
				"dupsTested" : 0,
				"dupsDropped" : 0,
				"seenInvalidated" : 0,
				"matchTested" : 1
			}
		}
	},
	"serverInfo" : {
		"host" : "mark-HP-Pavilion-dv6-Notebook-PC",
		"port" : 27017,
		"version" : "3.0.7",
		"gitVersion" : "6ce7cbe8c6b899552dadd907604559806aa2e9bd"
	},
	"ok" : 1
}
> 


```

## 2. Buscar antes e depois com index composto.
```
> db.pokemons.getIndexes()
[
	{
		"v" : 1,
		"key" : {
			"_id" : 1
		},
		"name" : "_id_",
		"ns" : "be-mean-pokemons.pokemons"
	},
	{
		"v" : 1,
		"key" : {
			"name" : 1
		},
		"name" : "name_1",
		"ns" : "be-mean-pokemons.pokemons"
	}
]

> explain.find({moves:'Investida',attack:{$gt:39}})
{
	"queryPlanner" : {
		"plannerVersion" : 1,
		"namespace" : "be-mean-pokemons.pokemons",
		"indexFilterSet" : false,
		"parsedQuery" : {
			"$and" : [
				{
					"moves" : {
						"$eq" : "Investida"
					}
				},
				{
					"attack" : {
						"$gt" : 39
					}
				}
			]
		},
		"winningPlan" : {
			"stage" : "COLLSCAN",
			"filter" : {
				"$and" : [
					{
						"moves" : {
							"$eq" : "Investida"
						}
					},
					{
						"attack" : {
							"$gt" : 39
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
		"nReturned" : 6,
		"executionTimeMillis" : 0,
		"totalKeysExamined" : 0,
		"totalDocsExamined" : 8,
		"executionStages" : {
			"stage" : "COLLSCAN",
			"filter" : {
				"$and" : [
					{
						"moves" : {
							"$eq" : "Investida"
						}
					},
					{
						"attack" : {
							"$gt" : 39
						}
					}
				]
			},
			"nReturned" : 6,
			"executionTimeMillisEstimate" : 0,
			"works" : 10,
			"advanced" : 6,
			"needTime" : 3,
			"needFetch" : 0,
			"saveState" : 0,
			"restoreState" : 0,
			"isEOF" : 1,
			"invalidates" : 0,
			"direction" : "forward",
			"docsExamined" : 8
		}
	},
	"serverInfo" : {
		"host" : "mark-HP-Pavilion-dv6-Notebook-PC",
		"port" : 27017,
		"version" : "3.0.7",
		"gitVersion" : "6ce7cbe8c6b899552dadd907604559806aa2e9bd"
	},
	"ok" : 1
}



> db.pokemons.createIndex({moves: 1, attack: 1})
{
	"createdCollectionAutomatically" : false,
	"numIndexesBefore" : 2,
	"numIndexesAfter" : 3,
	"ok" : 1
}
> 



> explain.find({moves:'Investida',attack:{$gt:39}})
{
	"queryPlanner" : {
		"plannerVersion" : 1,
		"namespace" : "be-mean-pokemons.pokemons",
		"indexFilterSet" : false,
		"parsedQuery" : {
			"$and" : [
				{
					"moves" : {
						"$eq" : "Investida"
					}
				},
				{
					"attack" : {
						"$gt" : 39
					}
				}
			]
		},
		"winningPlan" : {
			"stage" : "FETCH",
			"inputStage" : {
				"stage" : "IXSCAN",
				"keyPattern" : {
					"moves" : 1,
					"attack" : 1
				},
				"indexName" : "moves_1_attack_1",
				"isMultiKey" : true,
				"direction" : "forward",
				"indexBounds" : {
					"moves" : [
						"[\"Investida\", \"Investida\"]"
					],
					"attack" : [
						"(39.0, inf.0]"
					]
				}
			}
		},
		"rejectedPlans" : [ ]
	},
	"executionStats" : {
		"executionSuccess" : true,
		"nReturned" : 6,
		"executionTimeMillis" : 40,
		"totalKeysExamined" : 6,
		"totalDocsExamined" : 6,
		"executionStages" : {
			"stage" : "FETCH",
			"nReturned" : 6,
			"executionTimeMillisEstimate" : 0,
			"works" : 7,
			"advanced" : 6,
			"needTime" : 0,
			"needFetch" : 0,
			"saveState" : 0,
			"restoreState" : 0,
			"isEOF" : 1,
			"invalidates" : 0,
			"docsExamined" : 6,
			"alreadyHasObj" : 0,
			"inputStage" : {
				"stage" : "IXSCAN",
				"nReturned" : 6,
				"executionTimeMillisEstimate" : 0,
				"works" : 7,
				"advanced" : 6,
				"needTime" : 0,
				"needFetch" : 0,
				"saveState" : 0,
				"restoreState" : 0,
				"isEOF" : 1,
				"invalidates" : 0,
				"keyPattern" : {
					"moves" : 1,
					"attack" : 1
				},
				"indexName" : "moves_1_attack_1",
				"isMultiKey" : true,
				"direction" : "forward",
				"indexBounds" : {
					"moves" : [
						"[\"Investida\", \"Investida\"]"
					],
					"attack" : [
						"(39.0, inf.0]"
					]
				},
				"keysExamined" : 6,
				"dupsTested" : 6,
				"dupsDropped" : 0,
				"seenInvalidated" : 0,
				"matchTested" : 0
			}
		}
	},
	"serverInfo" : {
		"host" : "mark-HP-Pavilion-dv6-Notebook-PC",
		"port" : 27017,
		"version" : "3.0.7",
		"gitVersion" : "6ce7cbe8c6b899552dadd907604559806aa2e9bd"
	},
	"ok" : 1
}
> 

```
