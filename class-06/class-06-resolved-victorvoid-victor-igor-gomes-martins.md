# MongoDB - Aula 06 - Exercício
**autor**: Victor Igor

# 1. Fazer uma query para o campo name utilizando explain para ver o resultado da busca
```js
db.restaurantes.find({"name": "Glorious Food"}).explain('executionStats')

{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.restaurantes",
    "indexFilterSet": false,
    "parsedQuery": {
      "name": {
        "$eq": "Glorious Food"
      }
    },
    "winningPlan": {
      "stage": "COLLSCAN",
      "filter": {
        "name": {
          "$eq": "Glorious Food"
        }
      },
      "direction": "forward"
    },
    "rejectedPlans": [ ]
  },
  "executionStats": {
    "executionSuccess": true,
    "nReturned": 1,
    "executionTimeMillis": 24,
    "totalKeysExamined": 0,
    "totalDocsExamined": 25359,
    "executionStages": {
      "stage": "COLLSCAN",
      "filter": {
        "name": {
          "$eq": "Glorious Food"
        }
      },
      "nReturned": 1,
      "executionTimeMillisEstimate": 20,
      "works": 25361,
      "advanced": 1,
      "needTime": 25359,
      "needFetch": 0,
      "saveState": 198,
      "restoreState": 198,
      "isEOF": 1,
      "invalidates": 0,
      "direction": "forward",
      "docsExamined": 25359
    }
  },
  "serverInfo": {
    "host": "victorigor",
    "port": 27017,
    "version": "3.0.8",
    "gitVersion": "83d8cc25e00e42856924d84e220fbe4a839e605d"
  },
  "ok": 1
}



```
# 2. Criar um index um para o campo name

```js

db.restaurantes.createIndex({name: 1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}

```
#3. Refazer a query para o campo name utilizando explain para ver o resultado da busca

```js
db.restaurantes.find({"name": "Glorious Food"}).explain('executionStats')

{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.restaurantes",
    "indexFilterSet": false,
    "parsedQuery": {
      "name": {
        "$eq": "Glorious Food"
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
            "[\"Glorious Food\", \"Glorious Food\"]"
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
            "[\"Glorious Food\", \"Glorious Food\"]"
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
    "host": "victorigor",
    "port": 27017,
    "version": "3.0.8",
    "gitVersion": "83d8cc25e00e42856924d84e220fbe4a839e605d"
  },
  "ok": 1
}

```
#4. Fazer uma query para dois campos juntos utilizando explain para ver o resultado da busca

```js
var query = {$and:[{borough: 'Queens'},{cuisine: 'Jewish/Kosher'}]}
db.restaurantes.find(query).explain('executionStats')

{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.restaurantes",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "borough": {
            "$eq": "Queens"
          }
        },
        {
          "cuisine": {
            "$eq": "Jewish/Kosher"
          }
        }
      ]
    },
    "winningPlan": {
      "stage": "COLLSCAN",
      "filter": {
        "$and": [
          {
            "borough": {
              "$eq": "Queens"
            }
          },
          {
            "cuisine": {
              "$eq": "Jewish/Kosher"
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
    "nReturned": 62,
    "executionTimeMillis": 180,
    "totalKeysExamined": 0,
    "totalDocsExamined": 25359,
    "executionStages": {
      "stage": "COLLSCAN",
      "filter": {
        "$and": [
          {
            "borough": {
              "$eq": "Queens"
            }
          },
          {
            "cuisine": {
              "$eq": "Jewish/Kosher"
            }
          }
        ]
      },
      "nReturned": 62,
      "executionTimeMillisEstimate": 180,
      "works": 25361,
      "advanced": 62,
      "needTime": 25298,
      "needFetch": 0,
      "saveState": 198,
      "restoreState": 198,
      "isEOF": 1,
      "invalidates": 0,
      "direction": "forward",
      "docsExamined": 25359
    }
  },
  "serverInfo": {
    "host": "victorigor",
    "port": 27017,
    "version": "3.0.8",
    "gitVersion": "83d8cc25e00e42856924d84e220fbe4a839e605d"
  },
  "ok": 1
}
```
#5. Criar um index para esses dois campos juntos

```js
{borough: 'Queens'},{cuisine: 'Jewish/Kosher'}	
	db.restaurantes.createIndex({borough: 1, cuisine: 1})

{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 2,
  "numIndexesAfter": 3,
  "ok": 1
}

```
#6. Refazer a query para os dois campos juntos utilizando explain para ver o resultado da busca
```js

db.restaurantes.find(query).explain('executionStats')

{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.restaurantes",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "borough": {
            "$eq": "Queens"
          }
        },
        {
          "cuisine": {
            "$eq": "Jewish/Kosher"
          }
        }
      ]
    },
    "winningPlan": {
      "stage": "FETCH",
      "inputStage": {
        "stage": "IXSCAN",
        "keyPattern": {
          "borough": 1,
          "cuisine": 1
        },
        "indexName": "borough_1_cuisine_1",
        "isMultiKey": false,
        "direction": "forward",
        "indexBounds": {
          "borough": [
            "[\"Queens\", \"Queens\"]"
          ],
          "cuisine": [
            "[\"Jewish/Kosher\", \"Jewish/Kosher\"]"
          ]
        }
      }
    },
    "rejectedPlans": [ ]
  },
  "executionStats": {
    "executionSuccess": true,
    "nReturned": 62,
    "executionTimeMillis": 0,
    "totalKeysExamined": 62,
    "totalDocsExamined": 62,
    "executionStages": {
      "stage": "FETCH",
      "nReturned": 62,
      "executionTimeMillisEstimate": 0,
      "works": 63,
      "advanced": 62,
      "needTime": 0,
      "needFetch": 0,
      "saveState": 0,
      "restoreState": 0,
      "isEOF": 1,
      "invalidates": 0,
      "docsExamined": 62,
      "alreadyHasObj": 0,
      "inputStage": {
        "stage": "IXSCAN",
        "nReturned": 62,
        "executionTimeMillisEstimate": 0,
        "works": 63,
        "advanced": 62,
        "needTime": 0,
        "needFetch": 0,
        "saveState": 0,
        "restoreState": 0,
        "isEOF": 1,
        "invalidates": 0,
        "keyPattern": {
          "borough": 1,
          "cuisine": 1
        },
        "indexName": "borough_1_cuisine_1",
        "isMultiKey": false,
        "direction": "forward",
        "indexBounds": {
          "borough": [
            "[\"Queens\", \"Queens\"]"
          ],
          "cuisine": [
            "[\"Jewish/Kosher\", \"Jewish/Kosher\"]"
          ]
        },
        "keysExamined": 62,
        "dupsTested": 0,
        "dupsDropped": 0,
        "seenInvalidated": 0,
        "matchTested": 0
      }
    }
  },
  "serverInfo": {
    "host": "victorigor",
    "port": 27017,
    "version": "3.0.8",
    "gitVersion": "83d8cc25e00e42856924d84e220fbe4a839e605d"
  },
  "ok": 1
}
```


