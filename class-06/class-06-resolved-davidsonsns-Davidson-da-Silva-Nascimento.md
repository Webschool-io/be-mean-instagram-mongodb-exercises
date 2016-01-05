# MongoDB - Aula 06 - Exercício
**autor:** Davidson da Silva Nascimento
## 1. Fazer uma query para o campo `name` utilizando `explain` para ver o resultado da busca
```js
> db.pokemons.find({name: "Mewtwo"}).explain('executionStats').executionStats
{
        "executionSuccess" : true,
        "nReturned" : 1,
        "executionTimeMillis" : 0,
        "totalKeysExamined" : 0,
        "totalDocsExamined" : 610,
        "executionStages" : {
                "stage" : "COLLSCAN",
                "filter" : {
                        "name" : {
                                "$eq" : "Mewtwo"
                        }
                },
                "nReturned" : 1,
                "executionTimeMillisEstimate" : 10,
                "works" : 612,
                "advanced" : 1,
                "needTime" : 610,
                "needFetch" : 0,
                "saveState" : 4,
                "restoreState" : 4,
                "isEOF" : 1,
                "invalidates" : 0,
                "direction" : "forward",
                "docsExamined" : 610
        }
}
```
## 2. Criar um `index` um para o campo `name`
```js
> db.pokemons.createIndex({name: 1})
{
        "createdCollectionAutomatically" : false,
        "numIndexesBefore" : 1,
        "numIndexesAfter" : 2,
        "ok" : 1
}

> db.pokemons.getIndexes()
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
## 3. Refazer a query para o campo `name` utilizando `explain` para ver o resultado da busca
```js
> db.pokemons.find({name: "Mewtwo"}).explain('executionStats').executionStats
{
        "executionSuccess" : true,
        "nReturned" : 1,
        "executionTimeMillis" : 0,
        "totalKeysExamined" : 1,
        "totalDocsExamined" : 1,
        "executionStages" : {
                "stage" : "FETCH",
                "nReturned" : 1,
                "executionTimeMillisEstimate" : 0,
                "works" : 2,
                "advanced" : 1,
                "needTime" : 0,
                "needFetch" : 0,
                "saveState" : 0,
                "restoreState" : 0,
                "isEOF" : 1,
                "invalidates" : 0,
                "docsExamined" : 1,
                "alreadyHasObj" : 0,
                "inputStage" : {
                        "stage" : "IXSCAN",
                        "nReturned" : 1,
                        "executionTimeMillisEstimate" : 0,
                        "works" : 2,
                        "advanced" : 1,
                        "needTime" : 0,
                        "needFetch" : 0,
                        "saveState" : 0,
                        "restoreState" : 0,
                        "isEOF" : 1,
                        "invalidates" : 0,
                        "keyPattern" : {
                                "name" : 1
                        },
                        "indexName" : "name_1",
                        "isMultiKey" : false,
                        "direction" : "forward",
                        "indexBounds" : {
                                "name" : [
                                        "[\"Mewtwo\", \"Mewtwo\"]"
                                ]
                        },
                        "keysExamined" : 1,
                        "dupsTested" : 0,
                        "dupsDropped" : 0,
                        "seenInvalidated" : 0,
                        "matchTested" : 0
                }
        }
}
```
## 4. Fazer uma query para dois campos juntos utilizando `explain` para ver o resultado da busca
```js
> db.pokemons.find({$and : [{defense: 70}, {attack: { $gt: 110}}]}).explain('executionStats').executionStats
{
        "executionSuccess" : true,
        "nReturned" : 4,
        "executionTimeMillis" : 0,
        "totalKeysExamined" : 0,
        "totalDocsExamined" : 610,
        "executionStages" : {
                "stage" : "COLLSCAN",
                "filter" : {
                        "$and" : [
                                {
                                        "defense" : {
                                                "$eq" : 70
                                        }
                                },
                                {
                                        "attack" : {
                                                "$gt" : 110
                                        }
                                }
                        ]
                },
                "nReturned" : 4,
                "executionTimeMillisEstimate" : 0,
                "works" : 612,
                "advanced" : 4,
                "needTime" : 607,
                "needFetch" : 0,
                "saveState" : 4,
                "restoreState" : 4,
                "isEOF" : 1,
                "invalidates" : 0,
                "direction" : "forward",
                "docsExamined" : 610
        }
}
```
## 5. Criar um `index` para esses dois campos juntos
```js
> db.pokemons.createIndex({defense: 1, attack: 1})
{
        "createdCollectionAutomatically" : false,
        "numIndexesBefore" : 2,
        "numIndexesAfter" : 3,
        "ok" : 1
}

> db.pokemons.getIndexes()
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
                        "defense" : 1,
                        "attack" : 1
                },
                "name" : "defense_1_attack_1",
                "ns" : "be-mean.pokemons"
        }
]
```
## 6. Refazer a query para os dois campos juntos utilizando `explain` para ver o resultado da busca
```js
> db.pokemons.find({$and : [{defense: 70}, {attack: { $gt: 110}}]}).explain('executionStats').executionStats
{
        "executionSuccess" : true,
        "nReturned" : 4,
        "executionTimeMillis" : 0,
        "totalKeysExamined" : 4,
        "totalDocsExamined" : 4,
        "executionStages" : {
                "stage" : "FETCH",
                "nReturned" : 4,
                "executionTimeMillisEstimate" : 0,
                "works" : 5,
                "advanced" : 4,
                "needTime" : 0,
                "needFetch" : 0,
                "saveState" : 0,
                "restoreState" : 0,
                "isEOF" : 1,
                "invalidates" : 0,
                "docsExamined" : 4,
                "alreadyHasObj" : 0,
                "inputStage" : {
                        "stage" : "IXSCAN",
                        "nReturned" : 4,
                        "executionTimeMillisEstimate" : 0,
                        "works" : 5,
                        "advanced" : 4,
                        "needTime" : 0,
                        "needFetch" : 0,
                        "saveState" : 0,
                        "restoreState" : 0,
                        "isEOF" : 1,
                        "invalidates" : 0,
                        "keyPattern" : {
                                "defense" : 1,
                                "attack" : 1
                        },
                        "indexName" : "defense_1_attack_1",
                        "isMultiKey" : false,
                        "direction" : "forward",
                        "indexBounds" : {
                                "defense" : [
                                        "[70.0, 70.0]"
                                ],
                                "attack" : [
                                        "(110.0, 1.#INF]"
                                ]
                        },
                        "keysExamined" : 4,
                        "dupsTested" : 0,
                        "dupsDropped" : 0,
                        "seenInvalidated" : 0,
                        "matchTested" : 0
                }
        }
}
```