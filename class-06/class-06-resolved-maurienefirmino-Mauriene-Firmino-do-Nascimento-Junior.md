# MongoDB - Aula 06 - Exercício
autor: Mauriene Firmino do Nascimento Júnior

#1. Fazer uma query para o campo name utilizando explain para ver o resultado da busca

```
mauriene-J1800NH(mongod-2.6.10) db-aula-06> db.pokemons.find({name:/ivysaur/i}).explain('executionStats')
{
  "cursor": "BasicCursor",
  "isMultiKey": false,
  "n": 1,
  "nscannedObjects": 620,
  "nscanned": 620,
  "nscannedObjectsAllPlans": 620,
  "nscannedAllPlans": 620,
  "scanAndOrder": false,
  "indexOnly": false,
  "nYields": 4,
  "nChunkSkips": 0,
  "millis": 2,
  "allPlans": [
    {
      "cursor": "BasicCursor",
      "isMultiKey": false,
      "n": 1,
      "nscannedObjects": 620,
      "nscanned": 620,
      "scanAndOrder": false,
      "indexOnly": false,
      "nChunkSkips": 0
    }
  ],
  "server": "mauriene-J1800NH:27017",
  "filterSet": false,
  "stats": {
    "type": "COLLSCAN",
    "works": 622,
    "yields": 4,
    "unyields": 4,
    "invalidates": 0,
    "advanced": 1,
    "needTime": 620,
    "needFetch": 0,
    "isEOF": 1,
    "docsTested": 620,
    "children": [ ]
  }
}

```

#2. Criar um index um para o campo name

```
mauriene-J1800NH(mongod-2.6.10) db-aula-06> db.createIndex({name: 1})
2016-09-03T09:06:49.391-0300 TypeError: Property 'createIndex' of object db-aula-06 is not a function
mauriene-J1800NH(mongod-2.6.10) db-aula-06> db.pokemons.createIndex({name: 1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}

```

#3. Refazer a query para o campo name utilizando explain para ver o resultado da busca

```
mauriene-J1800NH(mongod-2.6.10) db-aula-06> db.pokemons.find({name:/ivysaur/i}).explain('executionStats')
{
  "cursor": "BtreeCursor name_1",
  "isMultiKey": false,
  "n": 1,
  "nscannedObjects": 1,
  "nscanned": 620,
  "nscannedObjectsAllPlans": 1,
  "nscannedAllPlans": 620,
  "scanAndOrder": false,
  "indexOnly": false,
  "nYields": 4,
  "nChunkSkips": 0,
  "millis": 4,
  "indexBounds": {
    "name": [
      [
        "",
        {
          
        }
      ],
      [
        /ivysaur/i,
        /ivysaur/i
      ]
    ]
  },
  "allPlans": [
    {
      "cursor": "BtreeCursor name_1",
      "isMultiKey": false,
      "n": 1,
      "nscannedObjects": 1,
      "nscanned": 620,
      "scanAndOrder": false,
      "indexOnly": false,
      "nChunkSkips": 0,
      "indexBounds": {
        "name": [
          [
            "",
            {
              
            }
          ],
          [
            /ivysaur/i,
            /ivysaur/i
          ]
        ]
      }
    }
  ],
  "server": "mauriene-J1800NH:27017",
  "filterSet": false,
  "stats": {
    "type": "FETCH",
    "works": 621,
    "yields": 4,
    "unyields": 4,
    "invalidates": 0,
    "advanced": 1,
    "needTime": 619,
    "needFetch": 0,
    "isEOF": 1,
    "alreadyHasObj": 0,
    "forcedFetches": 0,
    "matchTested": 0,
    "children": [
      {
        "type": "IXSCAN",
        "works": 620,
        "yields": 4,
        "unyields": 4,
        "invalidates": 0,
        "advanced": 1,
        "needTime": 619,
        "needFetch": 0,
        "isEOF": 1,
        "keyPattern": "{ name: 1.0 }",
        "isMultiKey": 0,
        "boundsVerbose": "field #0['name']: [\"\", {}), [/ivysaur/i, /ivysaur/i]",
        "yieldMovedCursor": 0,
        "dupsTested": 0,
        "dupsDropped": 0,
        "seenInvalidated": 0,
        "matchTested": 1,
        "keysExamined": 620,
        "children": [ ]
      }
    ]
  }
}

```

#4. Fazer uma query para dois campos juntos utilizando explain para ver o resultado da busca

```
mauriene-J1800NH(mongod-2.6.10) db-aula-06> db.pokemons.find({hp:{$gt:50},types:{$in:["poison"]}}).explain('executionStats')
{
  "cursor": "BasicCursor",
  "isMultiKey": false,
  "n": 37,
  "nscannedObjects": 620,
  "nscanned": 620,
  "nscannedObjectsAllPlans": 620,
  "nscannedAllPlans": 620,
  "scanAndOrder": false,
  "indexOnly": false,
  "nYields": 4,
  "nChunkSkips": 0,
  "millis": 3,
  "allPlans": [
    {
      "cursor": "BasicCursor",
      "isMultiKey": false,
      "n": 37,
      "nscannedObjects": 620,
      "nscanned": 620,
      "scanAndOrder": false,
      "indexOnly": false,
      "nChunkSkips": 0
    }
  ],
  "server": "mauriene-J1800NH:27017",
  "filterSet": false,
  "stats": {
    "type": "COLLSCAN",
    "works": 622,
    "yields": 4,
    "unyields": 4,
    "invalidates": 0,
    "advanced": 37,
    "needTime": 584,
    "needFetch": 0,
    "isEOF": 1,
    "docsTested": 620,
    "children": [ ]
  }
}

```

#5. Criar um index para esses dois campos juntos

```
mauriene-J1800NH(mongod-2.6.10) db-aula-06> db.pokemons.createIndex({hp: 1, types:1})
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 2,
  "numIndexesAfter": 3,
  "ok": 1
}

```

#6. Refazer a query para os dois campos juntos utilizando explain para ver o resultado da busca


```
mauriene-J1800NH(mongod-2.6.10) db-aula-06> db.pokemons.find({hp:{$gt:50},types:{$in:["poison"]}}).explain('executionStats')
{
  "cursor": "BtreeCursor hp_1_types_1",
  "isMultiKey": true,
  "n": 37,
  "nscannedObjects": 37,
  "nscanned": 141,
  "nscannedObjectsAllPlans": 37,
  "nscannedAllPlans": 141,
  "scanAndOrder": false,
  "indexOnly": false,
  "nYields": 1,
  "nChunkSkips": 0,
  "millis": 1,
  "indexBounds": {
    "hp": [
      [
        50,
        Infinity
      ]
    ],
    "types": [
      [
        "poison",
        "poison"
      ]
    ]
  },
  "allPlans": [
    {
      "cursor": "BtreeCursor hp_1_types_1",
      "isMultiKey": true,
      "n": 37,
      "nscannedObjects": 37,
      "nscanned": 141,
      "scanAndOrder": false,
      "indexOnly": false,
      "nChunkSkips": 0,
      "indexBounds": {
        "hp": [
          [
            50,
            Infinity
          ]
        ],
        "types": [
          [
            "poison",
            "poison"
          ]
        ]
      }
    }
  ],
  "server": "mauriene-J1800NH:27017",
  "filterSet": false,
  "stats": {
    "type": "FETCH",
    "works": 141,
    "yields": 1,
    "unyields": 1,
    "invalidates": 0,
    "advanced": 37,
    "needTime": 103,
    "needFetch": 0,
    "isEOF": 1,
    "alreadyHasObj": 0,
    "forcedFetches": 0,
    "matchTested": 0,
    "children": [
      {
        "type": "IXSCAN",
        "works": 141,
        "yields": 1,
        "unyields": 1,
        "invalidates": 0,
        "advanced": 37,
        "needTime": 103,
        "needFetch": 0,
        "isEOF": 1,
        "keyPattern": "{ hp: 1.0, types: 1.0 }",
        "isMultiKey": 1,
        "boundsVerbose": "field #0['hp']: (50.0, inf.0], field #1['types']: [\"poison\", \"poison\"]",
        "yieldMovedCursor": 0,
        "dupsTested": 37,
        "dupsDropped": 0,
        "seenInvalidated": 0,
        "matchTested": 0,
        "keysExamined": 141,
        "children": [ ]
      }
    ]
  }
}

```
