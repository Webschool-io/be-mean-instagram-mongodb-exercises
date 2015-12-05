# MongoDB - Aula 06 - Exercício
autor: José Ap. Silva Junior

# 1. Fazer uma query para o campo name utilizando explain para ver o resultado da busca

```javascript
> db.pokemons.find({name: /rattata/i}).explain("executionStats")
{
        "cursor" : "BasicCursor",
        "isMultiKey" : false,
        "n" : 1,
        "nscannedObjects" : 610,
        "nscanned" : 610,
        "nscannedObjectsAllPlans" : 610,
        "nscannedAllPlans" : 610,
        "scanAndOrder" : false,
        "indexOnly" : false,
        "nYields" : 4,
        "nChunkSkips" : 0,
        "millis" : 1,
        "allPlans" : [
                {
                        "cursor" : "BasicCursor",
                        "isMultiKey" : false,
                        "n" : 1,
                        "nscannedObjects" : 610,
                        "nscanned" : 610,
                        "scanAndOrder" : false,
                        "indexOnly" : false,
                        "nChunkSkips" : 0
                }
        ],
        "server" : "Junior:27017",
        "filterSet" : false,
        "stats" : {
                "type" : "COLLSCAN",
                "works" : 612,
                "yields" : 4,
                "unyields" : 4,
                "invalidates" : 0,
                "advanced" : 1,
                "needTime" : 610,
                "needFetch" : 0,
                "isEOF" : 1,
                "docsTested" : 610,
                "children" : [ ]
        }
}
```

# 2. Criar um index um para o campo name

```javascript
> db.pokemons.createIndex({name: 1})
{
        "createdCollectionAutomatically" : false,
        "numIndexesBefore" : 1,
        "numIndexesAfter" : 2,
        "ok" : 1
}
```

# 3. Refazer a query para o campo name utilizando explain para ver o resultado da busca

```javascript
> db.pokemons.find({name: /rattata/i}).explain("executionStats")
{
        "cursor" : "BtreeCursor name_1",
        "isMultiKey" : false,
        "n" : 1,
        "nscannedObjects" : 1,
        "nscanned" : 610,
        "nscannedObjectsAllPlans" : 1,
        "nscannedAllPlans" : 610,
        "scanAndOrder" : false,
        "indexOnly" : false,
        "nYields" : 5,
        "nChunkSkips" : 0,
        "millis" : 97,
        "indexBounds" : {
                "name" : [
                        [
                                "",
                                {

                                }
                        ],
                        [
                                /rattata/i,
                                /rattata/i
                        ]
                ]
        },
        "allPlans" : [
                {
                        "cursor" : "BtreeCursor name_1",
                        "isMultiKey" : false,
                        "n" : 1,
                        "nscannedObjects" : 1,
                        "nscanned" : 610,
                        "scanAndOrder" : false,
                        "indexOnly" : false,
                        "nChunkSkips" : 0,
                        "indexBounds" : {
                                "name" : [
                                        [
                                                "",
                                                {

                                                }
                                        ],
                                        [
                                                /rattata/i,
                                                /rattata/i
                                        ]
                                ]
                        }
                }
        ],
        "server" : "Junior:27017",
        "filterSet" : false,
        "stats" : {
                "type" : "FETCH",
                "works" : 611,
                "yields" : 5,
                "unyields" : 5,
                "invalidates" : 0,
                "advanced" : 1,
                "needTime" : 609,
                "needFetch" : 0,
                "isEOF" : 1,
                "alreadyHasObj" : 0,
                "forcedFetches" : 0,
                "matchTested" : 0,
                "children" : [
                        {
                                "type" : "IXSCAN",
                                "works" : 610,
                                "yields" : 5,
                                "unyields" : 5,
                                "invalidates" : 0,
                                "advanced" : 1,
                                "needTime" : 609,
                                "needFetch" : 0,
                                "isEOF" : 1,
                                "keyPattern" : "{ name: 1.0 }",
                                "isMultiKey" : 0,
                                "boundsVerbose" : "field #0['name']: [\"\", {}), [/rattata/i, /rattata/i]",
                                "yieldMovedCursor" : 0,
                                "dupsTested" : 0,
                                "dupsDropped" : 0,
                                "seenInvalidated" : 0,
                                "matchTested" : 1,
                                "keysExamined" : 610,
                                "children" : [ ]
                        }
                ]
        }
}
```

# 4. Fazer uma query para dois campos juntos utilizando explain para ver o resultado da busca

```javascript
> db.pokemons.find({$and: [{name: /pikachu/i},{defense: 40}]}).explain("executionStats")
{
        "cursor" : "BtreeCursor name_1",
        "isMultiKey" : false,
        "n" : 1,
        "nscannedObjects" : 1,
        "nscanned" : 610,
        "nscannedObjectsAllPlans" : 1,
        "nscannedAllPlans" : 610,
        "scanAndOrder" : false,
        "indexOnly" : false,
        "nYields" : 4,
        "nChunkSkips" : 0,
        "millis" : 2,
        "indexBounds" : {
                "name" : [
                        [
                                "",
                                {

                                }
                        ],
                        [
                                /pikachu/i,
                                /pikachu/i
                        ]
                ]
        },
        "allPlans" : [
                {
                        "cursor" : "BtreeCursor name_1",
                        "isMultiKey" : false,
                        "n" : 1,
                        "nscannedObjects" : 1,
                        "nscanned" : 610,
                        "scanAndOrder" : false,
                        "indexOnly" : false,
                        "nChunkSkips" : 0,
                        "indexBounds" : {
                                "name" : [
                                        [
                                                "",
                                                {

                                                }
                                        ],
                                        [
                                                /pikachu/i,
                                                /pikachu/i
                                        ]
                                ]
                        }
                }
        ],
        "server" : "Junior:27017",
        "filterSet" : false,
        "stats" : {
                "type" : "KEEP_MUTATIONS",
                "works" : 611,
                "yields" : 4,
                "unyields" : 4,
                "invalidates" : 0,
                "advanced" : 1,
                "needTime" : 609,
                "needFetch" : 0,
                "isEOF" : 1,
                "children" : [
                        {
                                "type" : "FETCH",
                                "works" : 611,
                                "yields" : 4,
                                "unyields" : 4,
                                "invalidates" : 0,
                                "advanced" : 1,
                                "needTime" : 609,
                                "needFetch" : 0,
                                "isEOF" : 1,
                                "alreadyHasObj" : 0,
                                "forcedFetches" : 0,
                                "matchTested" : 1,
                                "children" : [
                                        {
                                                "type" : "IXSCAN",
                                                "works" : 610,
                                                "yields" : 4,
                                                "unyields" : 4,
                                                "invalidates" : 0,
                                                "advanced" : 1,
                                                "needTime" : 609,
                                                "needFetch" : 0,
                                                "isEOF" : 1,
                                                "keyPattern" : "{ name: 1.0 }",
                                                "isMultiKey" : 0,
                                                "boundsVerbose" : "field #0['name']: [\"\", {}), [/pikachu/i, /pikachu/i]",
                                                "yieldMovedCursor" : 0,
                                                "dupsTested" : 0,
                                                "dupsDropped" : 0,
                                                "seenInvalidated" : 0,
                                                "matchTested" : 1,
                                                "keysExamined" : 610,
                                                "children" : [ ]
                                        }
                                ]
                        }
                ]
        }
}
```

# 5. Criar um index para esses dois campos juntos

```javascript
> db.pokemons.createIndex({name: 1, defense: 1})
{
        "createdCollectionAutomatically" : false,
        "numIndexesBefore" : 2,
        "numIndexesAfter" : 3,
        "ok" : 1
}
```

# 6. Refazer a query para os dois campos juntos utilizando explain para ver o resultado da busca

```javascript
> db.pokemons.find({$and: [{name: /pikachu/i},{defense: 40}]}).explain("executionStats")
{
        "cursor" : "BtreeCursor name_1_defense_1",
        "isMultiKey" : false,
        "n" : 1,
        "nscannedObjects" : 1,
        "nscanned" : 610,
        "nscannedObjectsAllPlans" : 2,
        "nscannedAllPlans" : 1220,
        "scanAndOrder" : false,
        "indexOnly" : false,
        "nYields" : 9,
        "nChunkSkips" : 0,
        "millis" : 56,
        "indexBounds" : {
                "name" : [
                        [
                                "",
                                {

                                }
                        ],
                        [
                                /pikachu/i,
                                /pikachu/i
                        ]
                ],
                "defense" : [
                        [
                                40,
                                40
                        ]
                ]
        },
        "allPlans" : [
                {
                        "cursor" : "BtreeCursor name_1_defense_1",
                        "isMultiKey" : false,
                        "n" : 1,
                        "nscannedObjects" : 1,
                        "nscanned" : 610,
                        "scanAndOrder" : false,
                        "indexOnly" : false,
                        "nChunkSkips" : 0,
                        "indexBounds" : {
                                "name" : [
                                        [
                                                "",
                                                {

                                                }
                                        ],
                                        [
                                                /pikachu/i,
                                                /pikachu/i
                                        ]
                                ],
                                "defense" : [
                                        [
                                                40,
                                                40
                                        ]
                                ]
                        }
                },
                {
                        "cursor" : "BtreeCursor name_1",
                        "isMultiKey" : false,
                        "n" : 1,
                        "nscannedObjects" : 1,
                        "nscanned" : 610,
                        "scanAndOrder" : false,
                        "indexOnly" : false,
                        "nChunkSkips" : 0,
                        "indexBounds" : {
                                "name" : [
                                        [
                                                "",
                                                {

                                                }
                                        ],
                                        [
                                                /pikachu/i,
                                                /pikachu/i
                                        ]
                                ]
                        }
                }
        ],
        "server" : "Junior:27017",
        "filterSet" : false,
        "stats" : {
                "type" : "FETCH",
                "works" : 611,
                "yields" : 9,
                "unyields" : 9,
                "invalidates" : 0,
                "advanced" : 1,
                "needTime" : 608,
                "needFetch" : 0,
                "isEOF" : 1,
                "alreadyHasObj" : 0,
                "forcedFetches" : 0,
                "matchTested" : 0,
                "children" : [
                        {
                                "type" : "IXSCAN",
                                "works" : 610,
                                "yields" : 9,
                                "unyields" : 9,
                                "invalidates" : 0,
                                "advanced" : 1,
                                "needTime" : 608,
                                "needFetch" : 0,
                                "isEOF" : 1,
                                "keyPattern" : "{ name: 1.0, defense: 1.0 }",
                                "isMultiKey" : 0,
                                "boundsVerbose" : "field #0['name']: [\"\", {}), [/pikachu/i, /pikachu/i], field #1['defense']: [40.0, 40.0]",
                                "yieldMovedCursor" : 0,
                                "dupsTested" : 0,
                                "dupsDropped" : 0,
                                "seenInvalidated" : 0,
                                "matchTested" : 1,
                                "keysExamined" : 610,
                                "children" : [ ]
                        }
                ]
        }
}
```
