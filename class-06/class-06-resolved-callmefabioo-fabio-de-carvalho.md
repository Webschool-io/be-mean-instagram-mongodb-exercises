# MongoDB - Aula 06 - Exercício
#### Autor: Fábio de Carvalho

### 1. Query sem índice do campo *name*.

> **db.restaurantes.find({'name': 'Kosher Island'}).explain('executionStats').executionStats**

```js
{
    "executionSuccess": true,
    "nReturned": 1,
    "executionTimeMillis": 27,
    "totalKeysExamined": 0,
    "totalDocsExamined": 25359,
    "executionStages": {
        "stage": "COLLSCAN",
        "filter": {
            "name": {
                "$eq": "Kosher Island"
            }
        },
        "nReturned": 1,
        "executionTimeMillisEstimate": 10,
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
}
```

### 2. Após a criação do índice.

> **db.restaurantes.createIndex( { name: 1 })**

```js
{
    "createdCollectionAutomatically": false,
    "numIndexesBefore": 1,
    "numIndexesAfter": 2,
    "ok": 1
}
```

> **db.restaurantes.find({'name': 'Kosher Island'}).explain('executionStats').executionStats**

```js
{
    "executionSuccess": true,
    "nReturned": 1,
    "executionTimeMillis": 2,
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
                    "[\"Kosher Island\", \"Kosher Island\"]"
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

### 3. Consulta por 2 campos sem índice.

> **db.restaurantes.find( {cuisine: 'Jewish/Kosher', borough: 'Bronx'} ).explain('executionStats').executionStats**

```js
{
    "executionSuccess": true,
    "nReturned": 8,
    "executionTimeMillis": 19,
    "totalKeysExamined": 0,
    "totalDocsExamined": 25359,
    "executionStages": {
        "stage": "COLLSCAN",
        "filter": {
            "$and": [
                {
                    "borough": {
                        "$eq": "Bronx"
                    }
                },
                {
                    "cuisine": {
                        "$eq": "Jewish/Kosher"
                    }
                }
            ]
        },
        "nReturned": 8,
        "executionTimeMillisEstimate": 20,
        "works": 25361,
        "advanced": 8,
        "needTime": 25352,
        "needFetch": 0,
        "saveState": 198,
        "restoreState": 198,
        "isEOF": 1,
        "invalidates": 0,
        "direction": "forward",
        "docsExamined": 25359
    }
}
```

### 4. Após criação de índice composto.

> **db.restaurantes.createIndex( { cuisine: 1, borough: 1 })**

```js
{
    "createdCollectionAutomatically": false,
    "numIndexesBefore": 2,
    "numIndexesAfter": 3,
    "ok": 1
}
```

> **db.restaurantes.find({cuisine: 'Jewish/Kosher', borough: 'Bronx'}).explain('executionStats').executionStats**

```js
{
    "executionSuccess": true,
    "nReturned": 8,
    "executionTimeMillis": 0,
    "totalKeysExamined": 8,
    "totalDocsExamined": 8,
    "executionStages": {
        "stage": "FETCH",
        "nReturned": 8,
        "executionTimeMillisEstimate": 0,
        "works": 9,
        "advanced": 8,
        "needTime": 0,
        "needFetch": 0,
        "saveState": 0,
        "restoreState": 0,
        "isEOF": 1,
        "invalidates": 0,
        "docsExamined": 8,
        "alreadyHasObj": 0,
        "inputStage": {
            "stage": "IXSCAN",
            "nReturned": 8,
            "executionTimeMillisEstimate": 0,
            "works": 9,
            "advanced": 8,
            "needTime": 0,
            "needFetch": 0,
            "saveState": 0,
            "restoreState": 0,
            "isEOF": 1,
            "invalidates": 0,
            "keyPattern": {
                "cuisine": 1,
                "borough": 1
            },
            "indexName": "cuisine_1_borough_1",
            "isMultiKey": false,
            "direction": "forward",
            "indexBounds": {
                "cuisine": [
                    "[\"Jewish/Kosher\", \"Jewish/Kosher\"]"
                ],
                "borough": [
                    "[\"Bronx\", \"Bronx\"]"
                ]
            },
            "keysExamined": 8,
            "dupsTested": 0,
            "dupsDropped": 0,
            "seenInvalidated": 0,
            "matchTested": 0
        }
    }
}
```


