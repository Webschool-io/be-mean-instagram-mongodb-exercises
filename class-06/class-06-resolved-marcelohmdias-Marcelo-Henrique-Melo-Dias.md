# MongoDB - Aula 06 - Exercício

**autor**: Marcelo H M Dias


## 1. Query pelo campo `name` sem índice.

```bash
MH-Note(mongod-3.0.7) be-mean> var poke = { name: /bulbasauro/i }
MH-Note(mongod-3.0.7) be-mean> db.pokemons.find(poke).explain('executionStats').executionStats
	{
		"executionSuccess": true,
		"nReturned": 0,
		"executionTimeMillis": 3,
		"totalKeysExamined": 0,
		"totalDocsExamined": 610,
		"executionStages": {
			"stage": "COLLSCAN",
			"filter": {
				"name": /bulbasauro/i
			},
			"nReturned": 0,
			"executionTimeMillisEstimate": 0,
			"works": 612,
			"advanced": 0,
			"needTime": 611,
			"needFetch": 0,
			"saveState": 4,
			"restoreState": 4,
			"isEOF": 1,
			"invalidates": 0,
			"direction": "forward",
			"docsExamined": 610
		}
	}
MH-Note(mongod-3.0.7) be-mean> 
```

## 2. Criar índice para o campo `name`.

```bash
MH-Note(mongod-3.0.7) be-mean> db.pokemons.createIndex({ name: 1 })
	{
		"createdCollectionAutomatically": false,
		"numIndexesBefore": 1,
		"numIndexesAfter": 2,
		"ok": 1
	}
MH-Note(mongod-3.0.7) be-mean> db.pokemons.getIndexes()
	[
		{
			"v": 1,
			"key": {
				"_id": 1
			},
			"name": "_id_",
			"ns": "be-mean.pokemons"
		},
		{
			"v": 1,
			"key": {
				"name": 1
			},
			"name": "name_1",
			"ns": "be-mean.pokemons"
		}
	]
MH-Note(mongod-3.0.7) be-mean> 
```


## 3. Query pelo campo `name` com índice.

```bash
MH-Note(mongod-3.0.7) be-mean> var poke = { name: /bulbasauro/i }
MH-Note(mongod-3.0.7) be-mean> db.pokemons.find(poke).explain('executionStats').executionStats
	{
		"executionSuccess": true,
		"nReturned": 0,
		"executionTimeMillis": 1,
		"totalKeysExamined": 610,
		"totalDocsExamined": 0,
		"executionStages": {
			"stage": "FETCH",
			"nReturned": 0,
			"executionTimeMillisEstimate": 10,
			"works": 611,
			"advanced": 0,
			"needTime": 610,
			"needFetch": 0,
			"saveState": 4,
			"restoreState": 4,
			"isEOF": 1,
			"invalidates": 0,
			"docsExamined": 0,
			"alreadyHasObj": 0,
			"inputStage": {
				"stage": "IXSCAN",
				"filter": {
					"name": /bulbasauro/i
				},
				"nReturned": 0,
				"executionTimeMillisEstimate": 0,
				"works": 610,
				"advanced": 0,
				"needTime": 610,
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
						"[/bulbasauro/i, /bulbasauro/i]"
					]
				},
				"keysExamined": 610,
				"dupsTested": 0,
				"dupsDropped": 0,
				"seenInvalidated": 0,
				"matchTested": 0
			}
		}
	}
MH-Note(mongod-3.0.7) be-mean>
```

## 4. Query por 2 campos não indexados.

```bash
MH-Note(mongod-3.0.7) be-mean> var query = { $and: [{ defense: { $gte: 70 } }, { attack: { $gte: 65  } }] }
MH-Note(mongod-3.0.7) be-mean> db.pokemons.find(query).explain('executionStats').executionStats
	{
		"executionSuccess": true,
		"nReturned": 236,
		"executionTimeMillis": 50,
		"totalKeysExamined": 0,
		"totalDocsExamined": 610,
		"executionStages": {
			"stage": "COLLSCAN",
			"filter": {
				"$and": [
					{
						"attack": {
							"$gte": 65
						}
					},
					{
						"defense": {
							"$gte": 70
						}
					}
				]
			},
			"nReturned": 236,
			"executionTimeMillisEstimate": 20,
			"works": 612,
			"advanced": 236,
			"needTime": 375,
			"needFetch": 0,
			"saveState": 5,
			"restoreState": 5,
			"isEOF": 1,
			"invalidates": 0,
			"direction": "forward",
			"docsExamined": 610
		}
	}
MH-Note(mongod-3.0.7) be-mean>
```

## 5. Criar index composto para dois campos.

```bash
MH-Note(mongod-3.0.7) be-mean> db.pokemons.createIndex({ attack: 1, defense: 1 })
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 2,
  "numIndexesAfter": 3,
  "ok": 1
}
MH-Note(mongod-3.0.7) be-mean> db.pokemons.getIndexes()
	[
		{
			"v": 1,
			"key": {
				"_id": 1
			},
			"name": "_id_",
			"ns": "be-mean.pokemons"
		},
		{
			"v": 1,
			"key": {
				"name": 1
			},
			"name": "name_1",
			"ns": "be-mean.pokemons"
		},
		{
			"v": 1,
			"key": {
				"attack": 1,
				"defense": 1
			},
			"name": "attack_1_defense_1",
			"ns": "be-mean.pokemons"
		}
	]
MH-Note(mongod-3.0.7) be-mean>
```

## 6. Query pelos dois campos agora indexados.

```bash
MH-Note(mongod-3.0.7) be-mean> var query = { $and: [{ defense: { $gte: 70 } }, { attack: { $gte: 65  } }] }
MH-Note(mongod-3.0.7) be-mean> db.pokemons.find(query).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 236,
  "executionTimeMillis": 2,
  "totalKeysExamined": 275,
  "totalDocsExamined": 236,
  "executionStages": {
    "stage": "FETCH",
    "nReturned": 236,
    "executionTimeMillisEstimate": 0,
    "works": 276,
    "advanced": 236,
    "needTime": 39,
    "needFetch": 0,
    "saveState": 2,
    "restoreState": 2,
    "isEOF": 1,
    "invalidates": 0,
    "docsExamined": 236,
    "alreadyHasObj": 0,
    "inputStage": {
      "stage": "IXSCAN",
      "nReturned": 236,
      "executionTimeMillisEstimate": 0,
      "works": 275,
      "advanced": 236,
      "needTime": 39,
      "needFetch": 0,
      "saveState": 2,
      "restoreState": 2,
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
          "[65.0, inf.0]"
        ],
        "defense": [
          "[70.0, inf.0]"
        ]
      },
      "keysExamined": 275,
      "dupsTested": 0,
      "dupsDropped": 0,
      "seenInvalidated": 0,
      "matchTested": 0
    }
  }
}
MH-Note(mongod-3.0.7) be-mean>
```
