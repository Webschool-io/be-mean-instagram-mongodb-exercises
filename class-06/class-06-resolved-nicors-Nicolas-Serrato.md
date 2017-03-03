# MongoDB - Aula 06 - Exercício
**User**: [niors](https://github.com/nicors)
**Autor**: Nicolas Serrato

## Fazer uma query para o campo name utilizando `explain` para ver o resultado da busca.

```js
db.pokemons.find({name: /pikachu/i}).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean-pokemons.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "name": /pikachu/i
    },
    "winningPlan": {
      "stage": "COLLSCAN",
      "filter": {
        "name": /pikachu/i
      },
      "direction": "forward"
    },
    "rejectedPlans": [ ]
  },
  "executionStats": {
    "executionSuccess": true,
    "nReturned": 1,
    "executionTimeMillis": 1,
    "totalKeysExamined": 0,
    "totalDocsExamined": 610,
    "executionStages": {
      "stage": "COLLSCAN",
      "filter": {
        "name": /pikachu/i
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
    "host": "nico-N53Ta",
    "port": 27017,
    "version": "3.0.14",
    "gitVersion": "08352afcca24bfc145240a0fac9d28b978ab77f3"
  },
  "ok": 1
}
```

## Criar um `index` um para o campo `name`.

```js
db.pokemons.createIndex({name: 1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}
```

## Refazer a query para o campo `name` utilizando `explain` para ver o resultado da busca.

```js
db.pokemons.find({name: /pikachu/i}).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean-pokemons.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "name": /pikachu/i
    },
    "winningPlan": {
      "stage": "FETCH",
      "inputStage": {
        "stage": "IXSCAN",
        "filter": {
          "name": /pikachu/i
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
            "[/pikachu/i, /pikachu/i]"
          ]
        }
      }
    },
    "rejectedPlans": [ ]
  },
  "executionStats": {
    "executionSuccess": true,
    "nReturned": 1,
    "executionTimeMillis": 2,
    "totalKeysExamined": 610,
    "totalDocsExamined": 1,
    "executionStages": {
      "stage": "FETCH",
      "nReturned": 1,
      "executionTimeMillisEstimate": 10,
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
          "name": /pikachu/i
        },
        "nReturned": 1,
        "executionTimeMillisEstimate": 10,
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
            "[/pikachu/i, /pikachu/i]"
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
    "host": "nico-N53Ta",
    "port": 27017,
    "version": "3.0.14",
    "gitVersion": "08352afcca24bfc145240a0fac9d28b978ab77f3"
  },
  "ok": 1
}
```
## Fazer uma query para dois campos juntos utilizando `explain` para ver o resultado da busca.
```js
var query = {
	$and: [
		{ attack: { $gte: 50 } },
		{ defense: { $gte: 30 } }
	]
}

db.pokemons.find(query).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean-pokemons.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "attack": {
            "$gte": 50
          }
        },
        {
          "defense": {
            "$gte": 30
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
              "$gte": 50
            }
          },
          {
            "defense": {
              "$gte": 30
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
    "nReturned": 489,
    "executionTimeMillis": 1,
    "totalKeysExamined": 0,
    "totalDocsExamined": 610,
    "executionStages": {
      "stage": "COLLSCAN",
      "filter": {
        "$and": [
          {
            "attack": {
              "$gte": 50
            }
          },
          {
            "defense": {
              "$gte": 30
            }
          }
        ]
      },
      "nReturned": 489,
      "executionTimeMillisEstimate": 0,
      "works": 612,
      "advanced": 489,
      "needTime": 122,
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
    "host": "nico-N53Ta",
    "port": 27017,
    "version": "3.0.14",
    "gitVersion": "08352afcca24bfc145240a0fac9d28b978ab77f3"
  },
  "ok": 1
}
```

## Criar um `index` para esses dois campos juntos.

```js
db.pokemons.createIndex({attack: 1, defense: 1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 2,
  "numIndexesAfter": 3,
  "ok": 1
}
```

## Refazer a query para os dois campos juntos utilizando `explain` para ver o resultado da busca.

```js
var query = {
	$and: [
		{ attack: { $gte: 50 } },
		{ defense: { $gte: 30 } }
	]
}

db.pokemons.find(query).explain('executionStats')
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean-pokemons.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "attack": {
            "$gte": 50
          }
        },
        {
          "defense": {
            "$gte": 30
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
            "[50.0, inf.0]"
          ],
          "defense": [
            "[30.0, inf.0]"
          ]
        }
      }
    },
    "rejectedPlans": [ ]
  },
  "executionStats": {
    "executionSuccess": true,
    "nReturned": 489,
    "executionTimeMillis": 1,
    "totalKeysExamined": 492,
    "totalDocsExamined": 489,
    "executionStages": {
      "stage": "FETCH",
      "nReturned": 489,
      "executionTimeMillisEstimate": 0,
      "works": 493,
      "advanced": 489,
      "needTime": 3,
      "needFetch": 0,
      "saveState": 3,
      "restoreState": 3,
      "isEOF": 1,
      "invalidates": 0,
      "docsExamined": 489,
      "alreadyHasObj": 0,
      "inputStage": {
        "stage": "IXSCAN",
        "nReturned": 489,
        "executionTimeMillisEstimate": 0,
        "works": 492,
        "advanced": 489,
        "needTime": 3,
        "needFetch": 0,
        "saveState": 3,
        "restoreState": 3,
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
            "[50.0, inf.0]"
          ],
          "defense": [
            "[30.0, inf.0]"
          ]
        },
        "keysExamined": 492,
        "dupsTested": 0,
        "dupsDropped": 0,
        "seenInvalidated": 0,
        "matchTested": 0
      }
    }
  },
  "serverInfo": {
    "host": "nico-N53Ta",
    "port": 27017,
    "version": "3.0.14",
    "gitVersion": "08352afcca24bfc145240a0fac9d28b978ab77f3"
  },
  "ok": 1
}

```