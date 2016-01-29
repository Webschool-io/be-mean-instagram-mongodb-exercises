# MongoDB - Aula 06 - Exercício
autor: **Igor Vidotto Felipe**

### Orientação 

Utilize o explain para verificar a melhora da busca.

**1 -** Na collection **pokemons** faça uma query com o campo `name`, logo após crie um índice para este campo e repita a query.

### Sem índice

```js
db.pokemons.find( {name: "Pikachu"} ).explain("executionStats");
```

#### Saída

```js
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
    "host": "igorpc",
    "port": 27017,
    "version": "3.0.7",
    "gitVersion": "6ce7cbe8c6b899552dadd907604559806aa2e9bd"
  },
  "ok": 1
}
```

> Tempo = 0ms

> Documentos Examinados = 610


### Com índice

#### Criação do índice

```js
db.pokemons.createIndex( {name: 1} );
```

#### Saída

```js
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}
```

#### Query

```js
db.pokemons.find( {name: "Pikachu"} ).explain("executionStats");
```

#### Saída

```js
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
            "[\"Pikachu\", \"Pikachu\"]"
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
            "[\"Pikachu\", \"Pikachu\"]"
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
    "host": "igorpc",
    "port": 27017,
    "version": "3.0.7",
    "gitVersion": "6ce7cbe8c6b899552dadd907604559806aa2e9bd"
  },
  "ok": 1
}
```

> Tempo = 0ms

> Documentos examinados = 1

**2 -** Na collection **pokemons** crie um índice para **dois campos** juntos.

#### Sem índice

```js
db.pokemons.find( { types: { $all: ["fire", "flying"] } , attack: { $gte: 100 } } );
```

#### Saída

```js
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "types": {
            "$eq": "fire"
          }
        },
        {
          "types": {
            "$eq": "flying"
          }
        },
        {
          "attack": {
            "$gte": 100
          }
        }
      ]
    },
    "winningPlan": {
      "stage": "COLLSCAN",
      "filter": {
        "$and": [
          {
            "types": {
              "$eq": "fire"
            }
          },
          {
            "types": {
              "$eq": "flying"
            }
          },
          {
            "attack": {
              "$gte": 100
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
    "nReturned": 3,
    "executionTimeMillis": 1,
    "totalKeysExamined": 0,
    "totalDocsExamined": 610,
    "executionStages": {
      "stage": "COLLSCAN",
      "filter": {
        "$and": [
          {
            "types": {
              "$eq": "fire"
            }
          },
          {
            "types": {
              "$eq": "flying"
            }
          },
          {
            "attack": {
              "$gte": 100
            }
          }
        ]
      },
      "nReturned": 3,
      "executionTimeMillisEstimate": 0,
      "works": 612,
      "advanced": 3,
      "needTime": 608,
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
    "host": "igorpc",
    "port": 27017,
    "version": "3.0.7",
    "gitVersion": "6ce7cbe8c6b899552dadd907604559806aa2e9bd"
  },
  "ok": 1
}
```

> Tempo = 1ms

> Documentos examinados = 610

#### Com índice

##### Criação do Índice

```js
db.pokemons.createIndex( { types: 1, attack: 1 } );
```

#### Saída

```js
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 2,
  "numIndexesAfter": 3,
  "ok": 1
}
```

#### Query

```js
db.pokemons.find( { types: { $all: [ "fire", "flying" ] }, attack: { $gte: 100 } } ).explain("executionStats");
```

#### Saída

```js
db.pokemons.find( { types: { $all: [ "fire", "flying" ] }, attack: { $gte: 100 } } ).explain("executionStats");
{
  "queryPlanner": {
    "plannerVersion": 1,
    "namespace": "be-mean.pokemons",
    "indexFilterSet": false,
    "parsedQuery": {
      "$and": [
        {
          "types": {
            "$eq": "fire"
          }
        },
        {
          "types": {
            "$eq": "flying"
          }
        },
        {
          "attack": {
            "$gte": 100
          }
        }
      ]
    },
    "winningPlan": {
      "stage": "KEEP_MUTATIONS",
      "inputStage": {
        "stage": "FETCH",
        "filter": {
          "types": {
            "$eq": "flying"
          }
        },
        "inputStage": {
          "stage": "IXSCAN",
          "keyPattern": {
            "types": 1,
            "attack": 1
          },
          "indexName": "types_1_attack_1",
          "isMultiKey": true,
          "direction": "forward",
          "indexBounds": {
            "types": [
              "[\"fire\", \"fire\"]"
            ],
            "attack": [
              "[100.0, inf.0]"
            ]
          }
        }
      }
    },
    "rejectedPlans": [
      {
        "stage": "KEEP_MUTATIONS",
        "inputStage": {
          "stage": "FETCH",
          "filter": {
            "types": {
              "$eq": "fire"
            }
          },
          "inputStage": {
            "stage": "IXSCAN",
            "keyPattern": {
              "types": 1,
              "attack": 1
            },
            "indexName": "types_1_attack_1",
            "isMultiKey": true,
            "direction": "forward",
            "indexBounds": {
              "types": [
                "[\"flying\", \"flying\"]"
              ],
              "attack": [
                "[100.0, inf.0]"
              ]
            }
          }
        }
      }
    ]
  },
  "executionStats": {
    "executionSuccess": true,
    "nReturned": 3,
    "executionTimeMillis": 0,
    "totalKeysExamined": 12,
    "totalDocsExamined": 12,
    "executionStages": {
      "stage": "KEEP_MUTATIONS",
      "nReturned": 3,
      "executionTimeMillisEstimate": 0,
      "works": 14,
      "advanced": 3,
      "needTime": 9,
      "needFetch": 0,
      "saveState": 0,
      "restoreState": 0,
      "isEOF": 1,
      "invalidates": 0,
      "inputStage": {
        "stage": "FETCH",
        "filter": {
          "types": {
            "$eq": "flying"
          }
        },
        "nReturned": 3,
        "executionTimeMillisEstimate": 0,
        "works": 13,
        "advanced": 3,
        "needTime": 9,
        "needFetch": 0,
        "saveState": 0,
        "restoreState": 0,
        "isEOF": 1,
        "invalidates": 0,
        "docsExamined": 12,
        "alreadyHasObj": 0,
        "inputStage": {
          "stage": "IXSCAN",
          "nReturned": 12,
          "executionTimeMillisEstimate": 0,
          "works": 13,
          "advanced": 12,
          "needTime": 0,
          "needFetch": 0,
          "saveState": 0,
          "restoreState": 0,
          "isEOF": 1,
          "invalidates": 0,
          "keyPattern": {
            "types": 1,
            "attack": 1
          },
          "indexName": "types_1_attack_1",
          "isMultiKey": true,
          "direction": "forward",
          "indexBounds": {
            "types": [
              "[\"fire\", \"fire\"]"
            ],
            "attack": [
              "[100.0, inf.0]"
            ]
          },
          "keysExamined": 12,
          "dupsTested": 12,
          "dupsDropped": 0,
          "seenInvalidated": 0,
          "matchTested": 0
        }
      }
    }
  },
  "serverInfo": {
    "host": "igorpc",
    "port": 27017,
    "version": "3.0.7",
    "gitVersion": "6ce7cbe8c6b899552dadd907604559806aa2e9bd"
  },
  "ok": 1
}
```

> Tempo = 0ms

> Documentos Examinados = 12

#### Conclusão

A melhora de tempo de resposta nesta database não foi tão evidente porque há poucos documentos, ainda assim podemos ver uma grande mudança na quantidade de documentos examinados quando criamos índices.