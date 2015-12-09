# MongoDB - Aula 06 - Exercício
autor: Franklin Dias

## 1. Realizando a query pelo name sem index

```javascript
db.pokemons.find({ "name": "Zubat"}).explain('executionStats')
{
	"cursor" : "BasicCursor",
	"isMultiKey" : false,
	"n" : 1,
	"nscannedObjects" : 230,
	"nscanned" : 230,
	"nscannedObjectsAllPlans" : 230,
	"nscannedAllPlans" : 230,
	"scanAndOrder" : false,
	"indexOnly" : false,
	"nYields" : 1,
	"nChunkSkips" : 0,
	"millis" : 0,
	"allPlans" : [
		{
			"cursor" : "BasicCursor",
			"isMultiKey" : false,
			"n" : 1,
			"nscannedObjects" : 230,
			"nscanned" : 230,
			"scanAndOrder" : false,
			"indexOnly" : false,
			"nChunkSkips" : 0
		}
	],
	"server" : "localhost.localdomain:27017",
	"filterSet" : false,
	"stats" : {
		"type" : "COLLSCAN",
		"works" : 232,
		"yields" : 1,
		"unyields" : 1,
		"invalidates" : 0,
		"advanced" : 1,
		"needTime" : 230,
		"needFetch" : 0,
		"isEOF" : 1,
		"docsTested" : 230,
		"children" : [ ]
	}
}
```

## 2. Criar Index e refazer a query

#### Criando Index
```javascript
db.pokemons.createIndex({name:1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}
```

#### Listando Indexes
```javascript
db.pokemons.getIndexes()
[
	{
		"v" : 1,
		"key" : {
			"_id" : 1
		},
		"name" : "_id_",
		"ns" : "be-mean.pokemons"
	},
	{
		"v" : 1,
		"key" : {
			"name" : 1
		},
		"name" : "name_1",
		"ns" : "be-mean.pokemons"
	}
]
```
#### Refazendo Consulta com index já criado
```javascript
db.pokemons.find({ "name": "Zubat"}).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 1,
  "executionTimeMillis": 0,
  "totalKeysExamined": 1,
  "totalDocsExamined": 1,
  "executionStages": {
    "stage": "FETCH",
    "nReturned": 1,
    "executionTimeMillisEstimate": 0,
    "works": 2,
    "advanced": 1,
    "needTime": 0,
    "needFetch": 0,
    "saveState": 0,
    "restoreState": 0,
    "isEOF": 1,
    "invalidates": 0,
    "docsExamined": 1,
    "alreadyHasObj": 0,
    "inputStage": {
      "stage": "IXSCAN",
      "nReturned": 1,
      "executionTimeMillisEstimate": 0,
      "works": 1,
      "advanced": 1,
      "needTime": 0,
      "needFetch": 0,
      "saveState": 0,
      "restoreState": 0,
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
          "[\"Zubat\", \"Zubat\"]"
        ]
      },
      "keysExamined": 1,
      "dupsTested": 0,
      "dupsDropped": 0,
      "seenInvalidated": 0,
      "matchTested": 0
    }
  }
}
```

## 3. Realizando a query com dois campos juntos sem o index criado

```javascript
db.pokemons.find({$and: [{hp:55 }, {speed:35}]}).explain('executionStats')
{
	"cursor" : "BasicCursor",
	"isMultiKey" : false,
	"n" : 3,
	"nscannedObjects" : 230,
	"nscanned" : 230,
	"nscannedObjectsAllPlans" : 230,
	"nscannedAllPlans" : 230,
	"scanAndOrder" : false,
	"indexOnly" : false,
	"nYields" : 1,
	"nChunkSkips" : 0,
	"millis" : 0,
	"allPlans" : [
		{
			"cursor" : "BasicCursor",
			"isMultiKey" : false,
			"n" : 3,
			"nscannedObjects" : 230,
			"nscanned" : 230,
			"scanAndOrder" : false,
			"indexOnly" : false,
			"nChunkSkips" : 0
		}
	],
	"server" : "localhost.localdomain:27017",
	"filterSet" : false,
	"stats" : {
		"type" : "COLLSCAN",
		"works" : 232,
		"yields" : 1,
		"unyields" : 1,
		"invalidates" : 0,
		"advanced" : 3,
		"needTime" : 228,
		"needFetch" : 0,
		"isEOF" : 1,
		"docsTested" : 230,
		"children" : [ ]
	}
}

```

## 4. Criar index com os dois campos e refazer a query

#### Criando o Index
```javascript
db.pokemons.createIndex({speed:1, hp:1})
{
	"createdCollectionAutomatically" : false,
	"numIndexesBefore" : 2,
	"numIndexesAfter" : 3,
	"ok" : 1
}
``` 

#### Listando todos os Indexes
```javascript
db.pokemons.getIndexes()
[
	{
		"v" : 1,
		"key" : {
			"_id" : 1
		},
		"name" : "_id_",
		"ns" : "be-mean.pokemons"
	},
	{
		"v" : 1,
		"key" : {
			"name" : 1
		},
		"name" : "name_1",
		"ns" : "be-mean.pokemons"
	},
	{
		"v" : 1,
		"key" : {
            "speed" : 1,
			"hp" : 1
			
		},
		"name" : "hp_1_speed_1",
		"ns" : "be-mean.pokemons"
	}
]
```

#### Refazendo query
```javascript
db.pokemons.find(query).explain('executionStats').executionStats
{
  "executionSuccess": true,
  "nReturned": 4,
  "executionTimeMillis": 17,
  "totalKeysExamined": 4,
  "totalDocsExamined": 4,
  "executionStages": {
    "stage": "FETCH",
    "nReturned": 4,
    "executionTimeMillisEstimate": 0,
    "works": 5,
    "advanced": 4,
    "needTime": 0,
    "needFetch": 0,
    "saveState": 0,
    "restoreState": 0,
    "isEOF": 1,
    "invalidates": 0,
    "docsExamined": 4,
    "alreadyHasObj": 0,
    "inputStage": {
      "stage": "IXSCAN",
      "nReturned": 4,
      "executionTimeMillisEstimate": 0,
      "works": 5,
      "advanced": 4,
      "needTime": 0,
      "needFetch": 0,
      "saveState": 0,
      "restoreState": 0,
      "isEOF": 1,
      "invalidates": 0,
      "keyPattern": {
        "hp": 1,
        "speed": 1
      },
      "indexName": "hp_1_speed_1",
      "isMultiKey": false,
      "direction": "forward",
      "indexBounds": {
        "hp": [
          "[40.0, 40.0]"
        ],
        "speed": [
          "[55.0, 55.0]"
        ]
      },
      "keysExamined": 4,
      "dupsTested": 0,
      "dupsDropped": 0,
      "seenInvalidated": 0,
      "matchTested": 0
    }
  }
}
```
