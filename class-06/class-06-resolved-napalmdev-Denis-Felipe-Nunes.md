# MongoDB - Aula 06 - Exercício
autor: Dênis Nunes


##1. Criar um índice para o campo name:

####Explain sem índice

```js
  db.pokedex.find({name: /Onix/i}).explain('executionStats').executionStats
  //result
  {
    "executionSuccess": true,
    "nReturned": 1,
    "executionTimeMillis": 0,
    "totalKeysExamined": 0,
    "totalDocsExamined": 603,
    "executionStages": {
      "stage": "COLLSCAN",
      "filter": {
        "name": /Onix/i
      },
      "nReturned": 1,
      "executionTimeMillisEstimate": 0,
      "works": 605,
      "advanced": 1,
      "needTime": 603,
      "needFetch": 0,
      "saveState": 4,
      "restoreState": 4,
      "isEOF": 1,
      "invalidates": 0,
      "direction": "forward",
      "docsExamined": 603
    }
  }
  
```

####Criando índice

```js
  db.pokedex.createIndex({name: 1});
  //result
  {
    "createdCollectionAutomatically": false,
    "numIndexesBefore": 1,
    "numIndexesAfter": 2,
    "ok": 1
  }
```

####Explain com Índice

```js
  db.pokedex.find({name: /Onix/i}).explain('executionStats').executionStats
  {
    "executionSuccess": true,
    "nReturned": 1,
    "executionTimeMillis": 0,
    "totalKeysExamined": 603,
    "totalDocsExamined": 1,
    "executionStages": {
      "stage": "FETCH",
      "nReturned": 1,
      "executionTimeMillisEstimate": 0,
      "works": 604,
      "advanced": 1,
      "needTime": 602,
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
          "name": /Onix/i
        },
        "nReturned": 1,
        "executionTimeMillisEstimate": 0,
        "works": 603,
        "advanced": 1,
        "needTime": 602,
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
            "[/Onix/i, /Onix/i]"
          ]
        },
        "keysExamined": 603,
        "dupsTested": 0,
        "dupsDropped": 0,
        "seenInvalidated": 0,
        "matchTested": 1
      }
    }
  }
```



##2. Criar um índice composto:

####Explain sem Índice

```js
  db.pokedex.find({defense: {$gte: 40}, attack: {$lt: 80}}).explain('executionStats').executionStats
  //result
  {
    "executionSuccess": true,
    "nReturned": 275,
    "executionTimeMillis": 0,
    "totalKeysExamined": 0,
    "totalDocsExamined": 603,
    "executionStages": {
      "stage": "COLLSCAN",
      "filter": {
        "$and": [
          {
            "attack": {
              "$lt": 80
            }
          },
          {
            "defense": {
              "$gte": 40
            }
          }
        ]
      },
      "nReturned": 275,
      "executionTimeMillisEstimate": 0,
      "works": 605,
      "advanced": 275,
      "needTime": 329,
      "needFetch": 0,
      "saveState": 4,
      "restoreState": 4,
      "isEOF": 1,
      "invalidates": 0,
      "direction": "forward",
      "docsExamined": 603
    }
  }
```

####Criando índice

```js
  db.pokedex.createIndex({defense: 1, attack: -1});
  //result
  {
    "createdCollectionAutomatically": false,
    "numIndexesBefore": 2,
    "numIndexesAfter": 3,
    "ok": 1
  }

```

####Explain com Índice

> ######Obs: A busca abaixo foi adaptada de acordo com o índice criado, como o attack está em
> ordem decrescente o $gt 80 examinará os primeiros registros somente, o mesmo acontece com o 
> defense $lte que busca menor que 40 em um índice em ordem crescente.

```js
  db.pokedex.find({defense: {$lte: 40}, attack: {$gt: 80}}).explain('executionStats').executionStats
  {
    "executionSuccess": true,
    "nReturned": 8,
    "executionTimeMillis": 0,
    "totalKeysExamined": 22,
    "totalDocsExamined": 8,
    "executionStages": {
      "stage": "FETCH",
      "nReturned": 8,
      "executionTimeMillisEstimate": 0,
      "works": 23,
      "advanced": 8,
      "needTime": 14,
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
        "works": 23,
        "advanced": 8,
        "needTime": 14,
        "needFetch": 0,
        "saveState": 0,
        "restoreState": 0,
        "isEOF": 1,
        "invalidates": 0,
        "keyPattern": {
          "defense": 1,
          "attack": -1
        },
        "indexName": "defense_1_attack_-1",
        "isMultiKey": false,
        "direction": "forward",
        "indexBounds": {
          "defense": [
            "[-inf.0, 40.0]"
          ],
          "attack": [
            "[inf.0, 80.0)"
          ]
        },
        "keysExamined": 22,
        "dupsTested": 0,
        "dupsDropped": 0,
        "seenInvalidated": 0,
        "matchTested": 0
      }
    }
  }
```

