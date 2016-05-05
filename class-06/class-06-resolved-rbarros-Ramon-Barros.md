# MongoDB - Aula 06 - Exercício
autor: Ramon Barros

## Fazer um query sem index para o campo **name** utilizando o explain.
```
db.pokemons.find({name: "Taillow"}).explain('executionStats').executionStats
{
	"executionSuccess" : true,
	"nReturned" : 1,
	"executionTimeMillis" : 0,
	"totalKeysExamined" : 0,
	"totalDocsExamined" : 610,
	"executionStages" : {
		"stage" : "COLLSCAN",
		"filter" : {
			"name" : {
				"$eq" : "Taillow"
			}
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
}
```
## Criar um index para o campo **name**.
```
db.pokemons.createIndex({name: 1})
{
	"createdCollectionAutomatically" : false,
	"numIndexesBefore" : 1,
	"numIndexesAfter" : 2,
	"ok" : 1
}
```
## Fazer um query com index para o campo **name** utilizando o explain.
```
db.pokemons.find({name: "Taillow"}).explain('executionStats').executionStats
{
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
					"[\"Taillow\", \"Taillow\"]"
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
```
## Fazer uma query sem index para dois campos juntos utilizando o explain.
```
var query = {
	$and: [
		{ attack: { $gte: 50 } },
		{ defense: { $gte: 30 } }
	]
}
db.pokemons.find(query).explain('executionStats').executionStats
{
	"executionSuccess" : true,
	"nReturned" : 489,
	"executionTimeMillis" : 1,
	"totalKeysExamined" : 0,
	"totalDocsExamined" : 610,
	"executionStages" : {
		"stage" : "COLLSCAN",
		"filter" : {
			"$and" : [
				{
					"attack" : {
						"$gte" : 50
					}
				},
				{
					"defense" : {
						"$gte" : 30
					}
				}
			]
		},
		"nReturned" : 489,
		"executionTimeMillisEstimate" : 0,
		"works" : 612,
		"advanced" : 489,
		"needTime" : 122,
		"needFetch" : 0,
		"saveState" : 4,
		"restoreState" : 4,
		"isEOF" : 1,
		"invalidates" : 0,
		"direction" : "forward",
		"docsExamined" : 610
	}
}
```
## Criar um index para dois campos juntos.
```
db.pokemons.createIndex({attack: 1, defense: 1})
{
	"createdCollectionAutomatically" : false,
	"numIndexesBefore" : 2,
	"numIndexesAfter" : 3,
	"ok" : 1
}
```
## Fazer uma query com index para dois campos juntos utilizando o explain.
```
db.pokemons.find(query).explain('executionStats').executionStats
{
	"executionSuccess" : true,
	"nReturned" : 489,
	"executionTimeMillis" : 2,
	"totalKeysExamined" : 492,
	"totalDocsExamined" : 489,
	"executionStages" : {
		"stage" : "FETCH",
		"nReturned" : 489,
		"executionTimeMillisEstimate" : 0,
		"works" : 493,
		"advanced" : 489,
		"needTime" : 3,
		"needFetch" : 0,
		"saveState" : 3,
		"restoreState" : 3,
		"isEOF" : 1,
		"invalidates" : 0,
		"docsExamined" : 489,
		"alreadyHasObj" : 0,
		"inputStage" : {
			"stage" : "IXSCAN",
			"nReturned" : 489,
			"executionTimeMillisEstimate" : 0,
			"works" : 492,
			"advanced" : 489,
			"needTime" : 3,
			"needFetch" : 0,
			"saveState" : 3,
			"restoreState" : 3,
			"isEOF" : 1,
			"invalidates" : 0,
			"keyPattern" : {
				"attack" : 1,
				"defense" : 1
			},
			"indexName" : "attack_1_defense_1",
			"isMultiKey" : false,
			"direction" : "forward",
			"indexBounds" : {
				"attack" : [
					"[50.0, inf.0]"
				],
				"defense" : [
					"[30.0, inf.0]"
				]
			},
			"keysExamined" : 492,
			"dupsTested" : 0,
			"dupsDropped" : 0,
			"seenInvalidated" : 0,
			"matchTested" : 0
		}
	}
}
```