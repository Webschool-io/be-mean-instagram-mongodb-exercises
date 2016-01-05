#MongoDB - Aula 06 - Exercícios
autor: Filipe Fernandes

##1. Fazer uma query para o campo `name` utilizando `explain` para ver o resultado da busca

```js
FilipeFernandes(C:\mongodb\bin\mongod.exe) be-mean> var query = {"name": /rattata/i}                          
FilipeFernandes(C:\mongodb\bin\mongod.exe) be-mean> db.pokemons.find(query).explain('executionStats')         
{                                                                                                                   
    "queryPlanner": {                                                                                               
        "plannerVersion": 1,                                                                                        
        "namespace": "be-mean.pokemons",                                                                            
        "indexFilterSet": false,                                                                                    
        "parsedQuery": {                                                                                            
            "name": /rattata/i                                                                                      
        },                                                                                                          
        "winningPlan": {                                                                                            
            "stage": "COLLSCAN",                                                                                    
            "filter": {                                                                                             
                "name": /rattata/i                                                                                  
            },                                                                                                      
            "direction": "forward"                                                                                  
        },                                                                                                          
        "rejectedPlans": [ ]                                                                                        
    },                                                                                                              
    "executionStats": {                                                                                             
        "executionSuccess": true,                                                                                   
        "nReturned": 1,                                                                                             
        "executionTimeMillis": 2,                                                                                   
        "totalKeysExamined": 0,                                                                                     
        "totalDocsExamined": 610,                                                                                   
        "executionStages": {                                                                                        
            "stage": "COLLSCAN",                                                                                    
            "filter": {                                                                                             
                "name": /rattata/i                                                                                  
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
        "host": "FilipeFernandes",                                                                                  
        "port": 27017,                                                                                              
        "version": "3.0.7",                                                                                         
        "gitVersion": "6ce7cbe8c6b899552dadd907604559806aa2e9bd"                                                    
    },                                                                                                              
    "ok": 1                                                                                                         
}                                                                                                                   
```

##2. Criar um `index` um para o campo `name`

```js
FilipeFernandes(C:\mongodb\bin\mongod.exe) be-mean> var index = { name: 1}
FilipeFernandes(C:\mongodb\bin\mongod.exe) be-mean> db.pokemons.createIndex(index)
{
    "createdCollectionAutomatically": false,
    "numIndexesBefore": 1,
    "numIndexesAfter": 2,
    "ok": 1
}
```

##3. Refazer a query para o campo `name` utilizando `explain` para ver o resultado da busca

> Nota: Ao utilizar um campo indexado não utilize `Regex` pois ele não terá a mesma agilidade!

```js
FilipeFernandes(C:\mongodb\bin\mongod.exe) be-mean> var query = {name: 'Rattata'}
FilipeFernandes(C:\mongodb\bin\mongod.exe) be-mean> db.pokemons.find(query).explain('executionStats')
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
        "host": "FilipeFernandes",
        "port": 27017,
        "version": "3.0.7",
        "gitVersion": "6ce7cbe8c6b899552dadd907604559806aa2e9bd"
    },
    "ok": 1
}

```

##4. Fazer uma query para dois campos juntos utilizando `explain` para ver o resultado da busca

```js

FilipeFernandes(C:\mongodb\bin\mongod.exe) be-mean> var query = {$and: [{hp: {$lte: 20}}, {speed: {$gte: 72}}]}
FilipeFernandes(C:\mongodb\bin\mongod.exe) be-mean> db.pokemons.find(query).explain('executionStats')
{
    "queryPlanner": {
        "plannerVersion": 1,
        "namespace": "be-mean.pokemons",
        "indexFilterSet": false,
        "parsedQuery": {
            "$and": [
                {
                    "hp": {
                        "$lte": 20
                    }
                },
                {
                    "speed": {
                        "$gte": 72
                    }
                }
            ]
        },
        "winningPlan": {
            "stage": "COLLSCAN",
            "filter": {
                "$and": [
                    {
                        "hp": {
                            "$lte": 20
                        }
                    },
                    {
                        "speed": {
                            "$gte": 72
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
        "nReturned": 2,
        "executionTimeMillis": 1,
        "totalKeysExamined": 0,
        "totalDocsExamined": 610,
        "executionStages": {
            "stage": "COLLSCAN",
            "filter": {
                "$and": [
                    {
                        "hp": {
                            "$lte": 20
                        }
                    },
                    {
                        "speed": {
                            "$gte": 72
                        }
                    }
                ]
            },
            "nReturned": 2,
            "executionTimeMillisEstimate": 0,
            "works": 612,
            "advanced": 2,
            "needTime": 609,
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
        "host": "FilipeFernandes",
        "port": 27017,
        "version": "3.0.7",
        "gitVersion": "6ce7cbe8c6b899552dadd907604559806aa2e9bd"
    },
    "ok": 1
}

```

##5. Criar um `index` para esses dois campos juntos

```js
FilipeFernandes(C:\mongodb\bin\mongod.exe) be-mean> var indexes = {hp: 1, speed:1}
FilipeFernandes(C:\mongodb\bin\mongod.exe) be-mean> db.pokemons.createIndex(indexes)  
{                                                                                           
    "createdCollectionAutomatically": false,                                                
    "numIndexesBefore": 2,                                                                  
    "numIndexesAfter": 3,                                                                   
    "ok": 1                                                                                 
}                                                                                           

//Listando os indexes

FilipeFernandes(C:\mongodb\bin\mongod.exe) be-mean> db.pokemons.getIndexes()
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
            "hp": 1,
            "speed": 1
        },
        "name": "hp_1_speed_1",
        "ns": "be-mean.pokemons"
    }
]

```

##6. Refazer a query para os dois campos juntos utilizando `explain` para ver o resultado da busca
```js

FilipeFernandes(C:\mongodb\bin\mongod.exe) be-mean> var query = {$and: [{hp: {$lte: 20}}, {speed: {$gte: 72}}]}
FilipeFernandes(C:\mongodb\bin\mongod.exe) be-mean> db.pokemons.find(query).explain('executionStats')
{
    "queryPlanner": {
        "plannerVersion": 1,
        "namespace": "be-mean.pokemons",
        "indexFilterSet": false,
        "parsedQuery": {
            "$and": [
                {
                    "hp": {
                        "$lte": 20
                    }
                },
                {
                    "speed": {
                        "$gte": 72
                    }
                }
            ]
        },
        "winningPlan": {
            "stage": "FETCH",
            "inputStage": {
                "stage": "IXSCAN",
                "keyPattern": {
                    "hp": 1,
                    "speed": 1
                },
                "indexName": "hp_1_speed_1",
                "isMultiKey": false,
                "direction": "forward",
                "indexBounds": {
                    "hp": [
                        "[-1.#INF, 20.0]"
                    ],
                    "speed": [
                        "[72.0, 1.#INF]"
                    ]
                }
            }
        },
        "rejectedPlans": [ ]
    },
    "executionStats": {
        "executionSuccess": true,
        "nReturned": 2,
        "executionTimeMillis": 0,
        "totalKeysExamined": 4,
        "totalDocsExamined": 2,
        "executionStages": {
            "stage": "FETCH",
            "nReturned": 2,
            "executionTimeMillisEstimate": 0,
            "works": 5,
            "advanced": 2,
            "needTime": 2,
            "needFetch": 0,
            "saveState": 0,
            "restoreState": 0,
            "isEOF": 1,
            "invalidates": 0,
            "docsExamined": 2,
            "alreadyHasObj": 0,
            "inputStage": {
                "stage": "IXSCAN",
                "nReturned": 2,
                "executionTimeMillisEstimate": 0,
                "works": 5,
                "advanced": 2,
                "needTime": 2,
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
                        "[-1.#INF, 20.0]"
                    ],
                    "speed": [
                        "[72.0, 1.#INF]"
                    ]
                },
                "keysExamined": 4,
                "dupsTested": 0,
                "dupsDropped": 0,
                "seenInvalidated": 0,
                "matchTested": 0
            }
        }
    },
    "serverInfo": {
        "host": "FilipeFernandes",
        "port": 27017,
        "version": "3.0.7",
        "gitVersion": "6ce7cbe8c6b899552dadd907604559806aa2e9bd"
    },
    "ok": 1
}

```
