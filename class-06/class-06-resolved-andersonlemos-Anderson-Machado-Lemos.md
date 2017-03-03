# MongoDB - Aula 06 - Exercício
Autor: Anderson Machado Lemos

# 1. Fazer uma query para o campo name utilizando explain para ver o resultado da busca
```
var query = {name:/pikachu/i}
db.pokemons.find(query).explain('executionStats')

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
"nReturned" : 1,
"executionTimeMillis" : 0,
"totalKeysExamined" : 0,
"totalDocsExamined" : 610,
"executionStages" : {
"stage" : "COLLSCAN",
"filter" : {
"name" : /pikachu/i
},
"nReturned" : 1,
"executionTimeMillisEstimate" : 0,
"works" : 612,
"advanced" : 1,
"needTime" : 610,
"needYield" : 0,
"saveState" : 4,
"restoreState" : 4,
"isEOF" : 1,
"invalidates" : 0,
"direction" : "forward",
"docsExamined" : 610
}
},
"serverInfo" : {
"host" : "AndersonTI",
"port" : 27017,
"version" : "3.2.1",
"gitVersion" : "a14d55980c2cdc565d4704a7e3ad37e4e535c1b2"
},
"ok" : 1
```
# 2. Criar um index um para o campo name
```
var index = {name: 1}
db.pokemons.createIndex(index)
{
"createdCollectionAutomatically": false,
"numIndexesBefore": 1,
"numIndexesAfter": 2,
"ok": 1
}
```
# 3. Refazer a query para o campo name utilizando explain para ver o resultado da busca

```
var query = {name : /pikachu/i}
db.pokemons.find(query).explain('executionStats')

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
"nReturned" : 1,
"executionTimeMillis" : 0,
"totalKeysExamined" : 610,
"totalDocsExamined" : 1,
"executionStages" : {
"stage" : "FETCH",
"nReturned" : 1,
"executionTimeMillisEstimate" : 0,
"works" : 611,
"advanced" : 1,
"needTime" : 609,
"needYield" : 0,
"saveState" : 4,
"restoreState" : 4,
"isEOF" : 1,
"invalidates" : 0,
"docsExamined" : 1,
"alreadyHasObj" : 0,
"inputStage" : {
"stage" : "IXSCAN",
"filter" : {
"name" : /pikachu/i
},
"nReturned" : 1,
"executionTimeMillisEstimate" : 0,
"works" : 611,
"advanced" : 1,
"needTime" : 609,
"needYield" : 0,
"saveState" : 4,
"restoreState" : 4,
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
"keysExamined" : 610,
"dupsTested" : 0,
"dupsDropped" : 0,
"seenInvalidated" : 0
}
}
},
"serverInfo" : {
"host" : "AndersonTI",
"port" : 27017,
"version" : "3.2.1",
"gitVersion" : "a14d55980c2cdc565d4704a7e3ad37e4e535c1b2"
},
"ok" : 1
```
# 4. Fazer uma query para dois campos juntos utilizando explain para ver o resultado da busca
```
> var query = {  $and: [{defense:{$gt:10}} , {attack:{$gt:40}} ] }
> db.pokemons.find(query).explain('executionStats')
{
"queryPlanner" : {
"plannerVersion" : 1,
"namespace" : "be-mean-pokemons.pokemons",
"indexFilterSet" : false,
"parsedQuery" : {
"$and" : [
{
"attack" : {
"$gt" : 40
}
},
{
"defense" : {
"$gt" : 10
}
}
]
},
"winningPlan" : {
"stage" : "COLLSCAN",
"filter" : {
"$and" : [
{
"attack" : {
"$gt" : 40
}
},
{
"defense" : {
"$gt" : 10
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
"nReturned" : 534,
"executionTimeMillis" : 1,
"totalKeysExamined" : 0,
"totalDocsExamined" : 610,
"executionStages" : {
"stage" : "COLLSCAN",
"filter" : {
"$and" : [
{
"attack" : {
"$gt" : 40
}
},
{
"defense" : {
"$gt" : 10
}
}
]
},
"nReturned" : 534,
"executionTimeMillisEstimate" : 0,
"works" : 612,
"advanced" : 534,
"needTime" : 77,
"needYield" : 0,
"saveState" : 4,
"restoreState" : 4,
"isEOF" : 1,
"invalidates" : 0,
"direction" : "forward",
"docsExamined" : 610
}
},
"serverInfo" : {
"host" : "AndersonTI",
"port" : 27017,
"version" : "3.2.1",
"gitVersion" : "a14d55980c2cdc565d4704a7e3ad37e4e535c1b2"
},
"ok" : 1
}

```
# 5. Criar um index para esses dois campos juntos

```
> var index = {defense: 1,attack :1}
> db.pokemons.createIndex(index)
{
"createdCollectionAutomatically" : false,
"numIndexesBefore" : 2,
"numIndexesAfter" : 3,
"ok" : 1
}
>
```

# 6. Refazer a query para os dois campos juntos utilizando explain para ver o resultado da busca
```
> var query = {  $and: [{defense:{$gt:10}} , {attack:{$gt:40}} ] }
> db.pokemons.find(query).explain('executionStats')
{
"queryPlanner" : {
"plannerVersion" : 1,
"namespace" : "be-mean-pokemons.pokemons",
"indexFilterSet" : false,
"parsedQuery" : {
"$and" : [
{
"attack" : {
"$gt" : 40
}
},
{
"defense" : {
"$gt" : 10
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
"isUnique" : false,
"isSparse" : false,
"isPartial" : false,
"indexVersion" : 1,
"direction" : "forward",
"indexBounds" : {
"defense" : [
"(10.0, 1.#INF]"
],
"attack" : [
"(40.0, 1.#INF]"
]
}
}
},
"rejectedPlans" : [ ]
},
"executionStats" : {
"executionSuccess" : true,
"nReturned" : 534,
"executionTimeMillis" : 49,
"totalKeysExamined" : 561,
"totalDocsExamined" : 534,
"executionStages" : {
"stage" : "FETCH",
"nReturned" : 534,
"executionTimeMillisEstimate" : 10,
"works" : 562,
"advanced" : 534,
"needTime" : 27,
"needYield" : 0,
"saveState" : 4,
"restoreState" : 4,
"isEOF" : 1,
"invalidates" : 0,
"docsExamined" : 534,
"alreadyHasObj" : 0,
"inputStage" : {
"stage" : "IXSCAN",
"nReturned" : 534,
"executionTimeMillisEstimate" : 10,
"works" : 562,
"advanced" : 534,
"needTime" : 27,
"needYield" : 0,
"saveState" : 4,
"restoreState" : 4,
"isEOF" : 1,
"invalidates" : 0,
"keyPattern" : {
"defense" : 1,
"attack" : 1
},
"indexName" : "defense_1_attack_1",
"isMultiKey" : false,
"isUnique" : false,
"isSparse" : false,
"isPartial" : false,
"indexVersion" : 1,
"direction" : "forward",
"indexBounds" : {
"defense" : [
"(10.0, 1.#INF]"
],
"attack" : [
"(40.0, 1.#INF]"
]
},
"keysExamined" : 561,
"dupsTested" : 0,
"dupsDropped" : 0,
"seenInvalidated" : 0
}
}
},
"serverInfo" : {
"host" : "AndersonTI",
"port" : 27017,
"version" : "3.2.1",
"gitVersion" : "a14d55980c2cdc565d4704a7e3ad37e4e535c1b2"
},
"ok" : 1
}
>
```
