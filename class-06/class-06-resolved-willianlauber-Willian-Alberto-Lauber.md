# ##MongoDB - Aula 06 - Exercícios
User: [WillianLauber](http://www.github.com/willianlauber)

Autor: Willian Lauber

## 1 Fazer uma query para o campo name utilizando `explain` para ver o resultado da busca

```sql
"cursor": "BasicCursor",
"isMultiKey": false,
"n": 1,
"nscannedObjects": 25359,
"nscanned": 25359,
"nscannedObjectsAllPlans": 25359,
"nscannedAllPlans": 25359,
"scanAndOrder": false,
"indexOnly": false,
"nYields": 198,
"nChunkSkips": 0,
"millis": 23,
"allPlans": [
  {
    "cursor": "BasicCursor",
    "isMultiKey": false,
    "n": 1,
    "nscannedObjects": 25359,
    "nscanned": 25359,
    "scanAndOrder": false,
    "indexOnly": false,
    "nChunkSkips": 0
  }
],
"server": "lubuntu:27017",
"filterSet": false,
"stats": {
  "type": "COLLSCAN",
  "works": 25361,
  "yields": 198,
  "unyields": 198,
  "invalidates": 0,
  "advanced": 1,
  "needTime": 25359,
  "needFetch": 0,
  "isEOF": 1,
  "docsTested": 25359,
  "children": [ ]
}
}
```

## Criar um `index` um para o campo `name`

```sql
be-mean> db.restaurantes.createIndex( { name: 1 } )
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}
```

## Refazer a query para o campo `name` utilizando `explain` para ver o resultado da busca

```sql
be-mean> db.restaurantes.find({ "name": "Nordic Delicacies" }).explain('executionStats')
"filterSet": false,
"stats": {
  "type": "FETCH",
  "works": 2,
  "yields": 0,
  "unyields": 0,
  "invalidates": 0,
  "advanced": 1,
  "needTime": 0,
  "needFetch": 0,
  "isEOF": 1,
  "alreadyHasObj": 0,
  "forcedFetches": 0,
  "matchTested": 0,
  "children": [
    {
      "type": "IXSCAN",
      "works": 2,
      "yields": 0,
      "unyields": 0,
      "invalidates": 0,
      "advanced": 1,
      "needTime": 0,
      "needFetch": 0,
      "isEOF": 1,
      "keyPattern": "{ name: 1.0 }",
      "isMultiKey": 0,
      "boundsVerbose": "field #0['name']: [\"Nordic Delicacies\", \"Nordic Delicacies\"]",
      "yieldMovedCursor": 0,
      "dupsTested": 0,
      "dupsDropped": 0,
      "seenInvalidated": 0,
      "matchTested": 0,
      "keysExamined": 1,
      "children": [ ]
    }
  ]
}
}
```

## Fazer uma query para dois campos juntos utilizando `explain` para ver o resultado da busca

```sql
be-mean> db.restaurantes.find({ borough: "Bronx", cuisine: "Bakery" }).explain('executionStats').executionStats
{
  "cursor": "BtreeCursor name_1",
  "isMultiKey": false,
  "n": 1,
  "nscannedObjects": 1,
  "nscanned": 1,
  "nscannedObjectsAllPlans": 1,
  "nscannedAllPlans": 1,
  "scanAndOrder": false,
  "indexOnly": false,
  "nYields": 0,
  "nChunkSkips": 0,
  "millis": 0,
  "indexBounds": {
    "name": [
      [
{       "Nordic Delicacies",
        "Nordic Delicacies"
      ]
    ]
  },
  "allPlans": [
    {
      "cursor": "BtreeCursor name_1",
      "isMultiKey": false,
      "n": 1,
      "nscannedObjects": 1,
      "nscanned": 1,
      "scanAndOrder": false,
      "indexOnly": false,
      "nChunkSkips": 0,
      "indexBounds": {
        "name": [
          [
            "Nordic Delicacies",
            "Nordic Delicacies"
          ]
        ]
      }
    }
  ],
  "server": "lubuntu:27017",
  "executionSuccess": true,
  "nReturned": 71,
  "executionTimeMillis": 61,
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
            "$eq": "Bakery"
          }
        }
      ]
    },
    "nReturned": 71,
    "executionTimeMillisEstimate": 20,
    "works": 25361,
    "advanced": 71,
    "needTime": 25289,
    "needYield": 0,
    "saveState": 198,
    "restoreState": 198,
    "isEOF": 1,
    "invalidates": 0,
    "direction": "forward",
    "docsExamined": 25359
  }
}
```

## Criar um `index` para esses dois campos juntos

```sql
lubuntu(mongod-2.6.10) be-mean> db.restaurantes.createIndex({ borough: 1, cuisine: 1 })
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 2,
  "numIndexesAfter": 3,
  "ok": 1
}
```

## Refazer a query para os dois campos juntos utilizando `explain` para ver o resultado da busca

```sql
be-mean> db.restaurantes.find({ borough: "Bronx", cuisine: "Bakery" }).explain('executionStats').executionStats
{
  "cursor": "BtreeCursor borough_1_cuisine_1",
  "isMultiKey": false,
  "n": 71,
  "nscannedObjects": 71,
  "nscanned": 71,
  "nscannedObjectsAllPlans": 71,
  "nscannedAllPlans": 71,
  "scanAndOrder": false,
  "indexOnly": false,
  "nYields": 0,
  "nChunkSkips": 0,
  "millis": 1,
  "indexBounds": {
    "borough": [
      [
        "Bronx",
        "Bronx"
      ]
      ],
   "cuisine": [
     [
       "Bakery",
       "Bakery"
     ]
   ]
 },
 "allPlans": [
   {
     "cursor": "BtreeCursor borough_1_cuisine_1",
     "isMultiKey": false,
     "n": 71,
     "nscannedObjects": 71,
     "nscanned": 71,
     "scanAndOrder": false,
     "indexOnly": false,
     "nChunkSkips": 0,
     "indexBounds": {
       "borough": [
         [
           "Bronx",
           "Bronx"
         ]
       ],
       "cuisine": [
         [
           "Bakery",
           "Bakery"
         ]
       ]
     }
   }
 ],
"server": "lubuntu:27017",
"filterSet": false,
"stats": {
  "type": "FETCH",
  "works": 72,
  "yields": 0,
  "unyields": 0,
  "invalidates": 0,
  "advanced": 71,
  "needTime": 0,
  "needFetch": 0,
  "isEOF": 1,
  "alreadyHasObj": 0,
  "forcedFetches": 0,
  "matchTested": 0,
  "children": [
    {
      "type": "IXSCAN",
      "works": 72,
      "yields": 0,
      "unyields": 0,
      "invalidates": 0,
      "advanced": 71,
      "needTime": 0,
      "needFetch": 0,
      "isEOF": 1,
      "keyPattern": "{ borough: 1.0, cuisine: 1.0 }",
      "isMultiKey": 0,
      "boundsVerbose": "field #0['borough']: [\"Bronx\", \"Bronx\"], field #1['cuisine']: [\"Bakery\", \"Bakery\"]",
      "yieldMovedCursor": 0,
      "dupsTested": 0,
      "dupsDropped": 0,
      "seenInvalidated": 0,
      "matchTested": 0,
      "keysExamined": 71,
      "children": [ ]
    }
  ]
}
}
```
