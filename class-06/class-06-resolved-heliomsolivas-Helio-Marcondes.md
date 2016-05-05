# MongoDb - Aula 06 - Exercício
Autor: Hélio Marcondes

## 1. Fazer uma query para o campo `name` utilizando `explain` para ver o resultado da busca

```
    db.pokemons.find({'name':'Pikachu'}).explain('executionStats')
    {
        "cursor" : "BasicCursor",
        "isMultiKey" : false,
        "n" : 0,
        "nscannedObjects" : 0,
        "nscanned" : 0,
        "nscannedObjectsAllPlans" : 0,
        "nscannedAllPlans" : 0,
        "scanAndOrder" : false,
        "indexOnly" : false,
        "nYields" : 0,
        "nChunkSkips" : 0,
        "millis" : 0,
        "allPlans" : [
                {
                        "cursor" : "BasicCursor",
                        "n" : 0,
                        "nscannedObjects" : 0,
                        "nscanned" : 0
                }
        ],
        "server" : "heliomsolivas-mongo-2467576:27017"
}

```

## 2. Criar um `index` um para o campo `name`

```
db.pokemons.createIndex({name:1})
{
        "createdCollectionAutomatically" : true,
        "numIndexesBefore" : 1,
        "numIndexesAfter" : 2,
        "ok" : 1
}
```

## 3. Refazer a query para o campo `name` utilizando `explain` para ver o resultado da busca

```
db.pokemons.find({'name':'Pikachu'}).explain('executionStats')
{
        "cursor" : "BtreeCursor name_1",
        "isMultiKey" : false,
        "n" : 0,
        "nscannedObjects" : 0,
        "nscanned" : 0,
        "nscannedObjectsAllPlans" : 0,
        "nscannedAllPlans" : 0,
        "scanAndOrder" : false,
        "indexOnly" : false,
        "nYields" : 0,
        "nChunkSkips" : 0,
        "millis" : 0,
        "indexBounds" : {
                "name" : [
                        [
                                "Pikachu",
                                "Pikachu"
                        ]
                ]
        },
        "allPlans" : [
                {
                        "cursor" : "BtreeCursor name_1",
                        "isMultiKey" : false,
                        "n" : 0,
                        "nscannedObjects" : 0,
                        "nscanned" : 0,
                        "scanAndOrder" : false,
                        "indexOnly" : false,
                        "nChunkSkips" : 0,
                        "indexBounds" : {
                                "name" : [
                                        [
                                                "Pikachu",
                                                "Pikachu"
                                        ]
                                ]
                        }
                }
        ],
        "server" : "heliomsolivas-mongo-2467576:27017",
        "filterSet" : false,
        "stats" : {
                "type" : "FETCH",
                "works" : 1,
                "yields" : 0,
                "unyields" : 0,
                "invalidates" : 0,
                "advanced" : 0,
                "needTime" : 0,
                "needFetch" : 0,
                "isEOF" : 1,
                "alreadyHasObj" : 0,
                "forcedFetches" : 0,
                "matchTested" : 0,
                "children" : [
                        {
                                "type" : "IXSCAN",
                                "works" : 1,
                                "yields" : 0,
                                "unyields" : 0,
                                "invalidates" : 0,
                                "advanced" : 0,
                                "needTime" : 0,
                                "needFetch" : 0,
                                "isEOF" : 1,
                                "keyPattern" : "{ name: 1.0 }",
                                "isMultiKey" : 0,
                                "boundsVerbose" : "field #0['name']: [\"Pikachu\", \"Pikachu\"]",
                                "yieldMovedCursor" : 0,
                                "dupsTested" : 0,
                                "dupsDropped" : 0,
                                "seenInvalidated" : 0,
                                "matchTested" : 0,
                                "keysExamined" : 0,
                                "children" : [ ]
                        }
                ]
        }
}
```
## 4. Fazer uma query para dois campos juntos utilizando `explain` para ver o resultado da busca

```
db.pokemons.find({ $and:[ { attack: { $gt: 65 } }, { defense: { $gt: 50 } } ] }).explain('executionStats')
{
        "cursor" : "BasicCursor",
        "isMultiKey" : false,
        "n" : 0,
        "nscannedObjects" : 0,
        "nscanned" : 0,
        "nscannedObjectsAllPlans" : 0,
        "nscannedAllPlans" : 0,
        "scanAndOrder" : false,
        "indexOnly" : false,
        "nYields" : 0,
        "nChunkSkips" : 0,
        "millis" : 0,
        "allPlans" : [
                {
                        "cursor" : "BasicCursor",
                        "isMultiKey" : false,
                        "n" : 0,
                        "nscannedObjects" : 0,
                        "nscanned" : 0,
                        "scanAndOrder" : false,
                        "indexOnly" : false,
                        "nChunkSkips" : 0
                }
        ],
        "server" : "heliomsolivas-mongo-2467576:27017",
        "filterSet" : false,
        "stats" : {
                "type" : "COLLSCAN",
                "works" : 2,
                "yields" : 0,
                "unyields" : 0,
                "invalidates" : 0,
                "advanced" : 0,
                "needTime" : 1,
                "needFetch" : 0,
                "isEOF" : 1,
                "docsTested" : 0,
                "children" : [ ]
        }
}
```

## 5. Criar um `index` para esses dois campos juntos

```
db.pokemons.createIndex({ attack: 1, defense: 1 })
{
        "createdCollectionAutomatically" : false,
        "numIndexesBefore" : 2,
        "numIndexesAfter" : 3,
        "ok" : 1
}
```

## 6. Refazer a query para os dois campos juntos utilizando `explain` para ver o resultado da busca

```
db.pokemons.find({ $and:[ { attack: { $gt: 65 } }, { defense: { $gt: 50 } } ] }).explain('executionStats')
{
        "cursor" : "BtreeCursor attack_1_defense_1",
        "isMultiKey" : false,
        "n" : 0,
        "nscannedObjects" : 0,
        "nscanned" : 0,
        "nscannedObjectsAllPlans" : 0,
        "nscannedAllPlans" : 0,
        "scanAndOrder" : false,
        "indexOnly" : false,
        "nYields" : 0,
        "nChunkSkips" : 0,
        "millis" : 0,
        "indexBounds" : {
                "attack" : [
                        [
                                65,
                                Infinity
                        ]
                ],
                "defense" : [
                        [
                                50,
                                Infinity
                        ]
                ]
        },
        "allPlans" : [
                {
                        "cursor" : "BtreeCursor attack_1_defense_1",
                        "isMultiKey" : false,
                        "n" : 0,
                        "nscannedObjects" : 0,
                        "nscanned" : 0,
                        "scanAndOrder" : false,
                        "indexOnly" : false,
                        "nChunkSkips" : 0,
                        "indexBounds" : {
                                "attack" : [
                                        [
                                                65,
                                                Infinity
                                        ]
                                ],
                                "defense" : [
                                        [
                                                50,
                                                Infinity
                                        ]
                                ]
                        }
                }
        ],
        "server" : "heliomsolivas-mongo-2467576:27017",
        "filterSet" : false,
        "stats" : {
                "type" : "FETCH",
                "works" : 1,
                "yields" : 0,
                "unyields" : 0,
                "invalidates" : 0,
                "advanced" : 0,
                "needTime" : 0,
                "needFetch" : 0,
                "isEOF" : 1,
                "alreadyHasObj" : 0,
                "forcedFetches" : 0,
                "matchTested" : 0,
                "children" : [
                        {
                                "type" : "IXSCAN",
                                "works" : 1,
                                "yields" : 0,
                                "unyields" : 0,
                                "invalidates" : 0,
                                "advanced" : 0,
                                "needTime" : 0,
                                "needFetch" : 0,
                                "isEOF" : 1,
                                "keyPattern" : "{ attack: 1.0, defense: 1.0 }",
                                "isMultiKey" : 0,
                                "boundsVerbose" : "field #0['attack']: (65.0, inf.0], field #1['defense']: (50.0, inf.0]",
                                "yieldMovedCursor" : 0,
                                "dupsTested" : 0,
                                "dupsDropped" : 0,
                                "seenInvalidated" : 0,
                                "matchTested" : 0,
                                "keysExamined" : 0,
                                "children" : [ ]
                        }
                ]
        }
}
```
