# MongoDB - Aula 06 - Exercício
autor: sirrommer - Rômulo Brasil

## 1. Fazer uma query para o campo `name` utilizando `explain` para ver o resultado da busca
```
> db.pokemons.find({ name: "Pikachu" }).explain('executionStats')
{
"queryPlanner": {
"plannerVersion": 1,
"namespace": "be-mean.pokemons",
"indexFilterSet": false,
"parsedQuery": {
"name": {
"$eq": "Pikachu"
}
},
"winningPlan": {
"stage": "COLLSCAN",
"filter": {
"name": {
"$eq": "Pikachu"
}
},
"direction": "forward"
},
"rejectedPlans": [ ]
},
"executionStats": {
"executionSuccess": true,
"nReturned": 1,
"executionTimeMillis": 0,
"totalKeysExamined": 0,
"totalDocsExamined": 610,
"executionStages": {
"stage": "COLLSCAN",
"filter": {
"name": {
"$eq": "Pikachu"
}
},
"nReturned": 1,
"executionTimeMillisEstimate": 0,
"works": 612,
"advanced": 1,
"needTime": 610,
"needFetch": 0,
"saveState": 4,
"restoreState": 4,
"isEOF": 1,
"invalidates": 0,
"direction": "forward",
"docsExamined": 610
}
},
"serverInfo": {
"host": "romulobrasil",
"port": 27017,
"version": "3.0.7",
"gitVersion": "6ce7cbe8c6b899552dadd907604559806aa2e9bd"
},
"ok": 1
}
```

## 2. Criar um `index` um para o campo `name`
```
> db.pokemons.createIndex({ name: 1 })
{
"createdCollectionAutomatically": false,
"numIndexesBefore": 1,
"numIndexesAfter": 2,
"ok": 1
}
```

## 3. Refazer a query para o campo `name` utilizando `explain` para ver o resultado da busca
```
> db.pokemons.find({ name: /rattata/i }).explain("executionStats")
{
"queryPlanner": {
"plannerVersion": 1,
"namespace": "be-mean.pokemons",
"indexFilterSet": false,
"parsedQuery": {
"name": /rattata/i
},
"winningPlan": {
"stage": "FETCH",
"inputStage": {
"stage": "IXSCAN",
"filter": {
"name": /rattata/i
},
"keyPattern": {
"name": 1
},
"indexName": "name_1",
"isMultiKey": false,
"direction": "forward",
"indexBounds": {
"name": [
"[\"\", {})",
"[/rattata/i, /rattata/i]"
]
}
}
},
"rejectedPlans": [ ]
},
"executionStats": {
"executionSuccess": true,
"nReturned": 1,
"executionTimeMillis": 1,
"totalKeysExamined": 610,
"totalDocsExamined": 1,
"executionStages": {
"stage": "FETCH",
"nReturned": 1,
"executionTimeMillisEstimate": 0,
"works": 611,
"advanced": 1,
"needTime": 609,
"needFetch": 0,
"saveState": 4,
"restoreState": 4,
"isEOF": 1,
"invalidates": 0,
"docsExamined": 1,
"alreadyHasObj": 0,
"inputStage": {
"stage": "IXSCAN",
"filter": {
"name": /rattata/i
},
"nReturned": 1,
"executionTimeMillisEstimate": 0,
"works": 610,
"advanced": 1,
"needTime": 609,
"needFetch": 0,
"saveState": 4,
"restoreState": 4,
"isEOF": 1,
"invalidates": 0,
"keyPattern": {
"name": 1
},
"indexName": "name_1",
"isMultiKey": false,
"direction": "forward",
"indexBounds": {
"name": [
"[\"\", {})",
"[/rattata/i, /rattata/i]"
]
},
"keysExamined": 610,
"dupsTested": 0,
"dupsDropped": 0,
"seenInvalidated": 0,
"matchTested": 1
}
}
},
"serverInfo": {
"host": "romulobrasil",
"port": 27017,
"version": "3.0.7",
"gitVersion": "6ce7cbe8c6b899552dadd907604559806aa2e9bd"
},
"ok": 1
}
```

# 4. Fazer uma query para dois campos juntos utilizando explain para ver o resultado da busca

```
> db.pokemons.find({ $and:[ { attack: { $gt: 20 } }, { defense: { $gt: 10 } } ] }).explain('executionStats')
{
"queryPlanner": {
"plannerVersion": 1,
"namespace": "be-mean.pokemons",
"indexFilterSet": false,
"parsedQuery": {
"$and": [
{
"attack": {
"$gt": 20
}
},
{
"defense": {
"$gt": 10
}
}
]
},
"winningPlan": {
"stage": "COLLSCAN",
"filter": {
"$and": [
{
"attack": {
"$gt": 20
}
},
{
"defense": {
"$gt": 10
}
}
]
},
"direction": "forward"
},
"rejectedPlans": [ ]
},
"executionStats": {
"executionSuccess": true,
"nReturned": 597,
"executionTimeMillis": 0,
"totalKeysExamined": 0,
"totalDocsExamined": 610,
"executionStages": {
"stage": "COLLSCAN",
"filter": {
"$and": [
{
"attack": {
"$gt": 20
}
},
{
"defense": {
"$gt": 10
}
}
]
},
"nReturned": 597,
"executionTimeMillisEstimate": 0,
"works": 612,
"advanced": 597,
"needTime": 14,
"needFetch": 0,
"saveState": 4,
"restoreState": 4,
"isEOF": 1,
"invalidates": 0,
"direction": "forward",
"docsExamined": 610
}
},
"serverInfo": {
"host": "romulobrasil",
"port": 27017,
"version": "3.0.7",
"gitVersion": "6ce7cbe8c6b899552dadd907604559806aa2e9bd"
},
"ok": 1
}
```

# 5. Criar um index para esses dois campos juntos

```
> db.pokemons.createIndex({attack: 1, defense: 1})
{
"createdCollectionAutomatically": false,
"numIndexesBefore": 2,
"numIndexesAfter": 3,
"ok": 1
}
```

# 6. Refazer a query para os dois campos juntos utilizando explain para ver o resultado da busca

```
> db.pokemons.find({ $and:[ { attack: { $gt: 20 } }, { defense: { $gt: 10 } } ] }).explain('executionStats')
{
"queryPlanner": {
"plannerVersion": 1,
"namespace": "be-mean.pokemons",
"indexFilterSet": false,
"parsedQuery": {
"$and": [
{
"attack": {
"$gt": 20
}
},
{
"defense": {
"$gt": 10
}
}
]
},
"winningPlan": {
"stage": "FETCH",
"inputStage": {
"stage": "IXSCAN",
"keyPattern": {
"attack": 1,
"defense": 1
},
"indexName": "attack_1_defense_1",
"isMultiKey": false,
"direction": "forward",
"indexBounds": {
"attack": [
"(20.0, inf.0]"
],
"defense": [
"(10.0, inf.0]"
]
}
}
},
"rejectedPlans": [ ]
},
"executionStats": {
"executionSuccess": true,
"nReturned": 597,
"executionTimeMillis": 1,
"totalKeysExamined": 597,
"totalDocsExamined": 597,
"executionStages": {
"stage": "FETCH",
"nReturned": 597,
"executionTimeMillisEstimate": 0,
"works": 598,
"advanced": 597,
"needTime": 0,
"needFetch": 0,
"saveState": 4,
"restoreState": 4,
"isEOF": 1,
"invalidates": 0,
"docsExamined": 597,
"alreadyHasObj": 0,
"inputStage": {
"stage": "IXSCAN",
"nReturned": 597,
"executionTimeMillisEstimate": 0,
"works": 597,
"advanced": 597,
"needTime": 0,
"needFetch": 0,
"saveState": 4,
"restoreState": 4,
"isEOF": 1,
"invalidates": 0,
"keyPattern": {
"attack": 1,
"defense": 1
},
"indexName": "attack_1_defense_1",
"isMultiKey": false,
"direction": "forward",
"indexBounds": {
"attack": [
"(20.0, inf.0]"
],
"defense": [
"(10.0, inf.0]"
]
},
"keysExamined": 597,
"dupsTested": 0,
"dupsDropped": 0,
"seenInvalidated": 0,
"matchTested": 0
}
}
},
"serverInfo": {
"host": "romulobrasil",
"port": 27017,
"version": "3.0.7",
"gitVersion": "6ce7cbe8c6b899552dadd907604559806aa2e9bd"
},
"ok": 1
}


```