# MongoDB - Aula 06 - Exercício
autor: ANDERSON DA LUZ MORAES

## 1. Na collection Pokemons, criar um index para o campo name.

    ```
	amoraes(mongod-3.0.7) be-mean> db.pokemons.createIndex({ name: 1 })
	{
	  "createdCollectionAutomatically": false,
	  "numIndexesBefore": 1,
	  "numIndexesAfter": 2,
	  "ok": 1
	}

	amoraes(mongod-3.0.7) be-mean> db.pokemons.getIndexes()
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


    ```

## 2. Na collection Pokemons, criar um index composto para 2 campos juntos.

    ```
	amoraes(mongod-3.0.7) be-mean> db.pokemons.createIndex({ attack: 1, defense: -1 })
	{
	  "createdCollectionAutomatically": false,
	  "numIndexesBefore": 2,
	  "numIndexesAfter": 3,
	  "ok": 1
	}

	amoraes(mongod-3.0.7) be-mean> db.pokemons.getIndexes()
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
	      "defense": -1
	    },
	    "name": "attack_1_defense_-1",
	    "ns": "be-mean.pokemons"
	  }
	]

    ```


## 3. Fazer uma query sem index e uma query com o index para o name, mostrar a diferença entre os resultados com explain.

    ```
	amoraes(mongod-3.0.7) be-mean> db.pokemons.find({name: "Rattata"}).explain("executionStats")
	{
	  "queryPlanner": {
	    "plannerVersion": 1,
	    "namespace": "be-mean.pokemons",
	    "indexFilterSet": false,
	    "parsedQuery": {
	      "name": {
		"$eq": "Rattata"
	      }
	    },
	    "winningPlan": {
	      "stage": "COLLSCAN",
	      "filter": {
		"name": {
		  "$eq": "Rattata"
		}
	      },
	      "direction": "forward"
	    },
	    "rejectedPlans": [ ]
	  },
	  "executionStats": {
	    "executionSuccess": true,
	    "nReturned": 1,
	    "executionTimeMillis": 20,
	    "totalKeysExamined": 0,
	    "totalDocsExamined": 610,
	    "executionStages": {
	      "stage": "COLLSCAN",
	      "filter": {
		"name": {
		  "$eq": "Rattata"
		}
	      },
	      "nReturned": 1,
	      "executionTimeMillisEstimate": 20,
	      "works": 612,
	      "advanced": 1,
	      "needTime": 610,
	      "needFetch": 0,
	      "saveState": 5,
	      "restoreState": 5,
	      "isEOF": 1,
	      "invalidates": 0,
	      "direction": "forward",
	      "docsExamined": 610
	    }
	  },
	  "serverInfo": {
	    "host": "amoraes",
	    "port": 27017,
	    "version": "3.0.7",
	    "gitVersion": "6ce7cbe8c6b899552dadd907604559806aa2e9bd"
	  },
	  "ok": 1
	}


	amoraes(mongod-3.0.7) be-mean> db.pokemons.find({name: "Rattata"}).explain("executionStats")
	{
	  "queryPlanner": {
	    "plannerVersion": 1,
	    "namespace": "be-mean.pokemons",
	    "indexFilterSet": false,
	    "parsedQuery": {
	      "name": {
		"$eq": "Rattata"
	      }
	    },
	    "winningPlan": {
	      "stage": "FETCH",
	      "inputStage": {
		"stage": "IXSCAN",
		"keyPattern": {
		  "name": 1
		},
		"indexName": "name_1",
		"isMultiKey": false,
		"direction": "forward",
		"indexBounds": {
		  "name": [
		    "[\"Rattata\", \"Rattata\"]"
		  ]
		}
	      }
	    },
	    "rejectedPlans": [ ]
	  },
	  "executionStats": {
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
		"works": 2,
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
		    "[\"Rattata\", \"Rattata\"]"
		  ]
		},
		"keysExamined": 1,
		"dupsTested": 0,
		"dupsDropped": 0,
		"seenInvalidated": 0,
		"matchTested": 0
	      }
	    }
	  },
	  "serverInfo": {
	    "host": "amoraes",
	    "port": 27017,
	    "version": "3.0.7",
	    "gitVersion": "6ce7cbe8c6b899552dadd907604559806aa2e9bd"
	  },
	  "ok": 1
	}

    ```

## 4. Fazer uma query sem index e uma com index para dois campos juntos, mostrar a diferença entre os resultados com explain.

    ```
	amoraes(mongod-3.0.7) be-mean> db.pokemons.find({$and: [{attack: {$gt: 55}}, {defense: {$lt: 38}}]}).explain('executionStats')
	{
	  "queryPlanner": {
	    "plannerVersion": 1,
	    "namespace": "be-mean.pokemons",
	    "indexFilterSet": false,
	    "parsedQuery": {
	      "$and": [
		{
		  "defense": {
		    "$lt": 38
		  }
		},
		{
		  "attack": {
		    "$gt": 55
		  }
		}
	      ]
	    },
	    "winningPlan": {
	      "stage": "COLLSCAN",
	      "filter": {
		"$and": [
		  {
		    "defense": {
		      "$lt": 38
		    }
		  },
		  {
		    "attack": {
		      "$gt": 55
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
	    "nReturned": 15,
	    "executionTimeMillis": 29,
	    "totalKeysExamined": 0,
	    "totalDocsExamined": 610,
	    "executionStages": {
	      "stage": "COLLSCAN",
	      "filter": {
		"$and": [
		  {
		    "defense": {
		      "$lt": 38
		    }
		  },
		  {
		    "attack": {
		      "$gt": 55
		    }
		  }
		]
	      },
	      "nReturned": 15,
	      "executionTimeMillisEstimate": 30,
	      "works": 612,
	      "advanced": 15,
	      "needTime": 596,
	      "needFetch": 0,
	      "saveState": 5,
	      "restoreState": 5,
	      "isEOF": 1,
	      "invalidates": 0,
	      "direction": "forward",
	      "docsExamined": 610
	    }
	  },
	  "serverInfo": {
	    "host": "amoraes",
	    "port": 27017,
	    "version": "3.0.7",
	    "gitVersion": "6ce7cbe8c6b899552dadd907604559806aa2e9bd"
	  },
	  "ok": 1
	}



	amoraes(mongod-3.0.7) be-mean> db.pokemons.find({$and: [{attack: {$gt: 55}}, {defense: {$lt: 38}}]}).explain('executionStats')
	{
	  "queryPlanner": {
	    "plannerVersion": 1,
	    "namespace": "be-mean.pokemons",
	    "indexFilterSet": false,
	    "parsedQuery": {
	      "$and": [
		{
		  "defense": {
		    "$lt": 38
		  }
		},
		{
		  "attack": {
		    "$gt": 55
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
		  "defense": -1
		},
		"indexName": "attack_1_defense_-1",
		"isMultiKey": false,
		"direction": "forward",
		"indexBounds": {
		  "attack": [
		    "(55.0, inf.0]"
		  ],
		  "defense": [
		    "(38.0, -inf.0]"
		  ]
		}
	      }
	    },
	    "rejectedPlans": [ ]
	  },
	  "executionStats": {
	    "executionSuccess": true,
	    "nReturned": 15,
	    "executionTimeMillis": 0,
	    "totalKeysExamined": 83,
	    "totalDocsExamined": 15,
	    "executionStages": {
	      "stage": "FETCH",
	      "nReturned": 15,
	      "executionTimeMillisEstimate": 0,
	      "works": 83,
	      "advanced": 15,
	      "needTime": 67,
	      "needFetch": 0,
	      "saveState": 0,
	      "restoreState": 0,
	      "isEOF": 1,
	      "invalidates": 0,
	      "docsExamined": 15,
	      "alreadyHasObj": 0,
	      "inputStage": {
		"stage": "IXSCAN",
		"nReturned": 15,
		"executionTimeMillisEstimate": 0,
		"works": 83,
		"advanced": 15,
		"needTime": 67,
		"needFetch": 0,
		"saveState": 0,
		"restoreState": 0,
		"isEOF": 1,
		"invalidates": 0,
		"keyPattern": {
		  "attack": 1,
		  "defense": -1
		},
		"indexName": "attack_1_defense_-1",
		"isMultiKey": false,
		"direction": "forward",
		"indexBounds": {
		  "attack": [
		    "(55.0, inf.0]"
		  ],
		  "defense": [
		    "(38.0, -inf.0]"
		  ]
		},
		"keysExamined": 83,
		"dupsTested": 0,
		"dupsDropped": 0,
		"seenInvalidated": 0,
		"matchTested": 0
	      }
	    }
	  },
	  "serverInfo": {
	    "host": "amoraes",
	    "port": 27017,
	    "version": "3.0.7",
	    "gitVersion": "6ce7cbe8c6b899552dadd907604559806aa2e9bd"
	  },
	  "ok": 1
	}

    ```
