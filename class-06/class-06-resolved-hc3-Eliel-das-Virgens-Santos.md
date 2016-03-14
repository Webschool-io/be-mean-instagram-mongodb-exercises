# MongoDB - Aula 06 - Exercício
User: [hc3](https://github.com/hc3)
Autor: Eliel das Virgens Santos



1#Fazer uma query para o campo name utilizando explain para ver o resultado da busca
```
darkSide(mongod-2.6.3) be-mean-pokemons> var query = {"name": "Rattata"}
darkSide(mongod-2.6.3) be-mean-pokemons> db.pokemons.find(query).explain()
{
  "cursor": "BasicCursor",
  "isMultiKey": false,
  "n": 1,
  "nscannedObjects": 610,
  "nscanned": 610,
  "nscannedObjectsAllPlans": 610,
  "nscannedAllPlans": 610,
  "scanAndOrder": false,
  "indexOnly": false,
  "nYields": 5,
  "nChunkSkips": 0,
  "millis": 43,
  "server": "darkSide:27017",
  "filterSet": false
}


darkSide(mongod-2.6.3) be-mean-pokemons> db.pokemons.find(query).explain('executionStats')
{
  "cursor": "BasicCursor",
  "isMultiKey": false,
  "n": 1,
  "nscannedObjects": 610,
  "nscanned": 610,
  "nscannedObjectsAllPlans": 610,
  "nscannedAllPlans": 610,
  "scanAndOrder": false,
  "indexOnly": false,
  "nYields": 4,
  "nChunkSkips": 0,
  "millis": 1,
  "allPlans": [
    {
      "cursor": "BasicCursor",
      "isMultiKey": false,
      "n": 1,
      "nscannedObjects": 610,
      "nscanned": 610,
      "scanAndOrder": false,
      "indexOnly": false,
      "nChunkSkips": 0
    }
  ],
  "server": "darkSide:27017",
  "filterSet": false,
  "stats": {
    "type": "COLLSCAN",
    "works": 612,
    "yields": 4,
    "unyields": 4,
    "invalidates": 0,
    "advanced": 1,
    "needTime": 610,
    "needFetch": 0,
    "isEOF": 1,
    "docsTested": 610,
    "children": [ ]
  }
}

```

2#Criar um index um para o campo name

```
darkSide(mongod-2.6.3) test> db.pokemons.createIndex({name:1})
{
  "createdCollectionAutomatically": true,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}

```



3#Refazer a query para o campo name utilizando explain para ver o resultado da busca

```
darkSide(mongod-2.6.3) test> db.pokemons.find(query).explain('executionStats')
{
  "cursor": "BtreeCursor name_1",
  "isMultiKey": false,
  "n": 0,
  "nscannedObjects": 0,
  "nscanned": 0,
  "nscannedObjectsAllPlans": 0,
  "nscannedAllPlans": 0,
  "scanAndOrder": false,
  "indexOnly": false,
  "nYields": 0,
  "nChunkSkips": 0,
  "millis": 0,
  "indexBounds": {
    "name": [
      [
        "Rattata",
        "Rattata"
      ]
    ]
  },
  "allPlans": [
    {
      "cursor": "BtreeCursor name_1",
      "isMultiKey": false,
      "n": 0,
      "nscannedObjects": 0,
      "nscanned": 0,
      "scanAndOrder": false,
      "indexOnly": false,
      "nChunkSkips": 0,
      "indexBounds": {
        "name": [
          [
            "Rattata",
            "Rattata"
          ]
        ]
      }
    }
  ],
  "server": "darkSide:27017",
  "filterSet": false,
  "stats": {
    "type": "FETCH",
    "works": 1,
    "yields": 0,
    "unyields": 0,
    "invalidates": 0,
    "advanced": 0,
    "needTime": 0,
    "needFetch": 0,
    "isEOF": 1,
    "alreadyHasObj": 0,
    "forcedFetches": 0,
    "matchTested": 0,
    "children": [
      {
        "type": "IXSCAN",
        "works": 1,
        "yields": 0,
        "unyields": 0,
        "invalidates": 0,
        "advanced": 0,
        "needTime": 0,
        "needFetch": 0,
        "isEOF": 1,
        "keyPattern": "{ name: 1.0 }",
        "boundsVerbose": "field #0['name']: [\"Rattata\", \"Rattata\"]",
        "isMultiKey": 0,
        "yieldMovedCursor": 0,
        "dupsTested": 0,
        "dupsDropped": 0,
        "seenInvalidated": 0,
        "matchTested": 0,
        "keysExamined": 0,
        "children": [ ]
      }
    ]
  }
}

```

4#Fazer uma query para dois campos juntos utilizando explain para ver o resultado da busca

```
darkSide(mongod-2.6.3) be-mean-pokemons> db.pokemons.find({$and:[{attack:{$lte:100}},{speed:{$lte:100}}]}).explain()
{
  "cursor": "BasicCursor",
  "isMultiKey": false,
  "n": 468,
  "nscannedObjects": 610,
  "nscanned": 610,
  "nscannedObjectsAllPlans": 610,
  "nscannedAllPlans": 610,
  "scanAndOrder": false,
  "indexOnly": false,
  "nYields": 4,
  "nChunkSkips": 0,
  "millis": 1,
  "server": "darkSide:27017",
  "filterSet": false
}
darkSide(mongod-2.6.3) be-mean-pokemons> db.pokemons.find({$and:[{attack:{$lte:100}},{speed:{$lte:100}}]}).explain('executionStats')
{
  "cursor": "BasicCursor",
  "isMultiKey": false,
  "n": 468,
  "nscannedObjects": 610,
  "nscanned": 610,
  "nscannedObjectsAllPlans": 610,
  "nscannedAllPlans": 610,
  "scanAndOrder": false,
  "indexOnly": false,
  "nYields": 4,
  "nChunkSkips": 0,
  "millis": 1,
  "allPlans": [
    {
      "cursor": "BasicCursor",
      "isMultiKey": false,
      "n": 468,
      "nscannedObjects": 610,
      "nscanned": 610,
      "scanAndOrder": false,
      "indexOnly": false,
      "nChunkSkips": 0
    }
  ],
  "server": "darkSide:27017",
  "filterSet": false,
  "stats": {
    "type": "COLLSCAN",
    "works": 612,
    "yields": 4,
    "unyields": 4,
    "invalidates": 0,
    "advanced": 468,
    "needTime": 143,
    "needFetch": 0,
    "isEOF": 1,
    "docsTested": 610,
    "children": [ ]
  }
}

```

5# Criar um index para esses dois campos juntos

```
darkSide(mongod-2.6.3) be-mean-pokemons> db.pokemons.createIndex({attack:1 , speed:1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}

```

6#Refazer a query para os dois campos juntos utilizando explain para ver o resultado da busca

```
darkSide(mongod-2.6.3) be-mean-pokemons> db.pokemons.find({$and:[{attack:{$lte:100}},{speed:{$lte:100}}]}).explain()
{
  "cursor": "BtreeCursor attack_1_speed_1",
  "isMultiKey": false,
  "n": 468,
  "nscannedObjects": 468,
  "nscanned": 488,
  "nscannedObjectsAllPlans": 468,
  "nscannedAllPlans": 488,
  "scanAndOrder": false,
  "indexOnly": false,
  "nYields": 3,
  "nChunkSkips": 0,
  "millis": 0,
  "indexBounds": {
    "attack": [
      [
        -Infinity,
        100
      ]
    ],
    "speed": [
      [
        -Infinity,
        100
      ]
    ]
  },
  "server": "darkSide:27017",
  "filterSet": false
}
darkSide(mongod-2.6.3) be-mean-pokemons> db.pokemons.find({$and:[{attack:{$lte:100}},{speed:{$lte:100}}]}).explain('executionStats')
{
  "cursor": "BtreeCursor attack_1_speed_1",
  "isMultiKey": false,
  "n": 468,
  "nscannedObjects": 468,
  "nscanned": 488,
  "nscannedObjectsAllPlans": 468,
  "nscannedAllPlans": 488,
  "scanAndOrder": false,
  "indexOnly": false,
  "nYields": 3,
  "nChunkSkips": 0,
  "millis": 0,
  "indexBounds": {
    "attack": [
      [
        -Infinity,
        100
      ]
    ],
    "speed": [
      [
        -Infinity,
        100
      ]
    ]
  },
  "allPlans": [
    {
      "cursor": "BtreeCursor attack_1_speed_1",
      "isMultiKey": false,
      "n": 468,
      "nscannedObjects": 468,
      "nscanned": 488,
      "scanAndOrder": false,
      "indexOnly": false,
      "nChunkSkips": 0,
      "indexBounds": {
        "attack": [
          [
            -Infinity,
            100
          ]
        ],
        "speed": [
          [
            -Infinity,
            100
          ]
        ]
      }
    }
  ],
  "server": "darkSide:27017",
  "filterSet": false,
  "stats": {
    "type": "FETCH",
    "works": 469,
    "yields": 3,
    "unyields": 3,
    "invalidates": 0,
    "advanced": 468,
    "needTime": 0,
    "needFetch": 0,
    "isEOF": 1,
    "alreadyHasObj": 0,
    "forcedFetches": 0,
    "matchTested": 0,
    "children": [
      {
        "type": "IXSCAN",
        "works": 468,
        "yields": 3,
        "unyields": 3,
        "invalidates": 0,
        "advanced": 468,
        "needTime": 0,
        "needFetch": 0,
        "isEOF": 1,
        "keyPattern": "{ attack: 1.0, speed: 1.0 }",
        "boundsVerbose": "field #0['attack']: [-inf.0, 100.0], field #1['speed']: [-inf.0, 100.0]",
        "isMultiKey": 0,
        "yieldMovedCursor": 0,
        "dupsTested": 0,
        "dupsDropped": 0,
        "seenInvalidated": 0,
        "matchTested": 0,
        "keysExamined": 488,
        "children": [ ]
      }
    ]
  }
}

```


