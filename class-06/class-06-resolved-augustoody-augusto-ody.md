# MongoDB - Aula 06 - Exercício
autor: Augusto Ody

## 1. Query para o campo `name` **sem** índice utilizando `explain` para ver o resultado da busca
```js
var query = {name: /Golem/i};
db.pokemons.find(query).explain('executionStats')
{
	"queryPlanner" : {
		"plannerVersion" : 1,
		"namespace" : "be-mean.pokemons",
		"indexFilterSet" : false,
		"parsedQuery" : {
			"name" : /Golem/i
		},
		"winningPlan" : {
			"stage" : "COLLSCAN",
			"filter" : {
				"name" : /Golem/i
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
				"name" : /Golem/i
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
		"host" : "vagrant-ubuntu-trusty-64",
		"port" : 27017,
		"version" : "3.0.7",
		"gitVersion" : "6ce7cbe8c6b899552dadd907604559806aa2e9bd"
	},
	"ok" : 1
}
```

## 2- Criar um `índice` um para o campo `name`
```js
db.pokemons.createIndex({name: 1})
{
	"createdCollectionAutomatically" : false,
	"numIndexesBefore" : 1,
	"numIndexesAfter" : 2,
	"ok" : 1
}
```

## 3. Query para o campo `name` com `índice` utilizando `explain`
```js
var query = {name: 'Golem'};
db.pokemons.find(query).explain('executionStats')
{
	"queryPlanner" : {
		"plannerVersion" : 1,
		"namespace" : "be-mean.pokemons",
		"indexFilterSet" : false,
		"parsedQuery" : {
			"name" : {
				"$eq" : "Golem"
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
						"[\"Golem\", \"Golem\"]"
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
					"name" : 1
				},
				"indexName" : "name_1",
				"isMultiKey" : false,
				"direction" : "forward",
				"indexBounds" : {
					"name" : [
						"[\"Golem\", \"Golem\"]"
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
		"host" : "vagrant-ubuntu-trusty-64",
		"port" : 27017,
		"version" : "3.0.7",
		"gitVersion" : "6ce7cbe8c6b899552dadd907604559806aa2e9bd"
	},
	"ok" : 1
}
```

## 4. Query para dois campos **sem** `índice`
```js
<<<<<<< HEAD
var query = {defense: {$gte: 20}, attack: {$gte: 100} }
=======
<<<<<<< HEAD
var query = {defense: {$gte: 20}, attack: {$gte: 100} }
=======
var query = {name: 'Golem', attack: 120 }
>>>>>>> 31c9f03c9889e4be08f0d88b04dcca98c5c02d67
>>>>>>> d360bcd8480da7ee02050d038b02780221194099
db.pokemons.find(query).explain('executionStats')
{
	"queryPlanner" : {
		"plannerVersion" : 1,
		"namespace" : "be-mean.pokemons",
		"indexFilterSet" : false,
		"parsedQuery" : {
			"$and" : [
				{
					"attack" : {
<<<<<<< HEAD
=======
<<<<<<< HEAD
>>>>>>> d360bcd8480da7ee02050d038b02780221194099
						"$gte" : 100
					}
				},
				{
					"defense" : {
						"$gte" : 20
<<<<<<< HEAD
=======
=======
						"$eq" : 120
					}
				},
				{
					"name" : {
						"$eq" : "Golem"
>>>>>>> 31c9f03c9889e4be08f0d88b04dcca98c5c02d67
>>>>>>> d360bcd8480da7ee02050d038b02780221194099
					}
				}
			]
		},
		"winningPlan" : {
<<<<<<< HEAD
=======
<<<<<<< HEAD
>>>>>>> d360bcd8480da7ee02050d038b02780221194099
			"stage" : "COLLSCAN",
			"filter" : {
				"$and" : [
					{
						"attack" : {
							"$gte" : 100
						}
					},
					{
						"defense" : {
							"$gte" : 20
						}
					}
				]
			},
			"direction" : "forward"
<<<<<<< HEAD
=======
=======
			"stage" : "KEEP_MUTATIONS",
			"inputStage" : {
				"stage" : "FETCH",
				"filter" : {
					"attack" : {
						"$eq" : 120
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
							"[\"Golem\", \"Golem\"]"
						]
					}
				}
			}
>>>>>>> 31c9f03c9889e4be08f0d88b04dcca98c5c02d67
>>>>>>> d360bcd8480da7ee02050d038b02780221194099
		},
		"rejectedPlans" : [ ]
	},
	"executionStats" : {
		"executionSuccess" : true,
<<<<<<< HEAD
=======
<<<<<<< HEAD
>>>>>>> d360bcd8480da7ee02050d038b02780221194099
		"nReturned" : 126,
		"executionTimeMillis" : 6,
		"totalKeysExamined" : 0,
		"totalDocsExamined" : 610,
		"executionStages" : {
			"stage" : "COLLSCAN",
			"filter" : {
				"$and" : [
					{
						"attack" : {
							"$gte" : 100
						}
					},
					{
						"defense" : {
							"$gte" : 20
						}
					}
				]
			},
			"nReturned" : 126,
			"executionTimeMillisEstimate" : 0,
			"works" : 613,
			"advanced" : 126,
			"needTime" : 485,
			"needFetch" : 1,
			"saveState" : 5,
			"restoreState" : 5,
			"isEOF" : 1,
			"invalidates" : 0,
			"direction" : "forward",
			"docsExamined" : 610
<<<<<<< HEAD
=======
=======
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
						"$eq" : 120
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
							"[\"Golem\", \"Golem\"]"
						]
					},
					"keysExamined" : 1,
					"dupsTested" : 0,
					"dupsDropped" : 0,
					"seenInvalidated" : 0,
					"matchTested" : 0
				}
			}
>>>>>>> 31c9f03c9889e4be08f0d88b04dcca98c5c02d67
>>>>>>> d360bcd8480da7ee02050d038b02780221194099
		}
	},
	"serverInfo" : {
		"host" : "vagrant-ubuntu-trusty-64",
		"port" : 27017,
		"version" : "3.0.7",
		"gitVersion" : "6ce7cbe8c6b899552dadd907604559806aa2e9bd"
	},
	"ok" : 1
}
```

## 5. Criar índice para `dois campos` juntos
```js
<<<<<<< HEAD
db.pokemons.createIndex({defense: 1, attack: 1})
=======
<<<<<<< HEAD
db.pokemons.createIndex({defense: 1, attack: 1})
=======
db.pokemons.createIndex({name: 1, attack: 1})
>>>>>>> 31c9f03c9889e4be08f0d88b04dcca98c5c02d67
>>>>>>> d360bcd8480da7ee02050d038b02780221194099
{
	"createdCollectionAutomatically" : false,
	"numIndexesBefore" : 2,
	"numIndexesAfter" : 3,
	"ok" : 1
}
```

## 6. Query para os `dois campos` **com** índice
```js
<<<<<<< HEAD
var query = {defense: {$gte: 20}, attack: {$gte: 100} }
=======
<<<<<<< HEAD
var query = {defense: {$gte: 20}, attack: {$gte: 100} }
=======
var query = {name: 'Golem', attack: 120 }
>>>>>>> 31c9f03c9889e4be08f0d88b04dcca98c5c02d67
>>>>>>> d360bcd8480da7ee02050d038b02780221194099
db.pokemons.find(query).explain('executionStats')
{
	"queryPlanner" : {
		"plannerVersion" : 1,
		"namespace" : "be-mean.pokemons",
		"indexFilterSet" : false,
		"parsedQuery" : {
			"$and" : [
				{
					"attack" : {
<<<<<<< HEAD
=======
<<<<<<< HEAD
>>>>>>> d360bcd8480da7ee02050d038b02780221194099
						"$gte" : 100
					}
				},
				{
					"defense" : {
						"$gte" : 20
<<<<<<< HEAD
=======
=======
						"$eq" : 120
					}
				},
				{
					"name" : {
						"$eq" : "Golem"
>>>>>>> 31c9f03c9889e4be08f0d88b04dcca98c5c02d67
>>>>>>> d360bcd8480da7ee02050d038b02780221194099
					}
				}
			]
		},
		"winningPlan" : {
			"stage" : "FETCH",
			"inputStage" : {
				"stage" : "IXSCAN",
				"keyPattern" : {
<<<<<<< HEAD
=======
<<<<<<< HEAD
>>>>>>> d360bcd8480da7ee02050d038b02780221194099
					"defense" : 1,
					"attack" : 1
				},
				"indexName" : "defense_1_attack_1",
				"isMultiKey" : false,
				"direction" : "forward",
				"indexBounds" : {
					"defense" : [
						"[20.0, inf.0]"
					],
					"attack" : [
						"[100.0, inf.0]"
<<<<<<< HEAD
=======
=======
					"name" : 1,
					"attack" : 1
				},
				"indexName" : "name_1_attack_1",
				"isMultiKey" : false,
				"direction" : "forward",
				"indexBounds" : {
					"name" : [
						"[\"Golem\", \"Golem\"]"
					],
					"attack" : [
						"[120.0, 120.0]"
>>>>>>> 31c9f03c9889e4be08f0d88b04dcca98c5c02d67
>>>>>>> d360bcd8480da7ee02050d038b02780221194099
					]
				}
			}
		},
<<<<<<< HEAD
=======
<<<<<<< HEAD
>>>>>>> d360bcd8480da7ee02050d038b02780221194099
		"rejectedPlans" : [ ]
	},
	"executionStats" : {
		"executionSuccess" : true,
		"nReturned" : 126,
		"executionTimeMillis" : 1,
		"totalKeysExamined" : 210,
		"totalDocsExamined" : 126,
		"executionStages" : {
			"stage" : "FETCH",
			"nReturned" : 126,
			"executionTimeMillisEstimate" : 0,
			"works" : 210,
			"advanced" : 126,
			"needTime" : 83,
			"needFetch" : 0,
			"saveState" : 1,
			"restoreState" : 1,
			"isEOF" : 1,
			"invalidates" : 0,
			"docsExamined" : 126,
			"alreadyHasObj" : 0,
			"inputStage" : {
				"stage" : "IXSCAN",
				"nReturned" : 126,
				"executionTimeMillisEstimate" : 0,
				"works" : 210,
				"advanced" : 126,
				"needTime" : 83,
				"needFetch" : 0,
				"saveState" : 1,
				"restoreState" : 1,
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
						"[20.0, inf.0]"
					],
					"attack" : [
						"[100.0, inf.0]"
					]
				},
				"keysExamined" : 210,
<<<<<<< HEAD
=======
=======
		"rejectedPlans" : [
			{
				"stage" : "KEEP_MUTATIONS",
				"inputStage" : {
					"stage" : "FETCH",
					"filter" : {
						"attack" : {
							"$eq" : 120
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
								"[\"Golem\", \"Golem\"]"
							]
						}
					}
				}
			}
		]
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
			"works" : 3,
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
					"name" : 1,
					"attack" : 1
				},
				"indexName" : "name_1_attack_1",
				"isMultiKey" : false,
				"direction" : "forward",
				"indexBounds" : {
					"name" : [
						"[\"Golem\", \"Golem\"]"
					],
					"attack" : [
						"[120.0, 120.0]"
					]
				},
				"keysExamined" : 1,
>>>>>>> 31c9f03c9889e4be08f0d88b04dcca98c5c02d67
>>>>>>> d360bcd8480da7ee02050d038b02780221194099
				"dupsTested" : 0,
				"dupsDropped" : 0,
				"seenInvalidated" : 0,
				"matchTested" : 0
			}
		}
	},
	"serverInfo" : {
		"host" : "vagrant-ubuntu-trusty-64",
		"port" : 27017,
		"version" : "3.0.7",
		"gitVersion" : "6ce7cbe8c6b899552dadd907604559806aa2e9bd"
	},
	"ok" : 1
}
```
