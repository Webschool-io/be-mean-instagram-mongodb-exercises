# MongoDB - Aula 06 - Exercício

Autor: Leonardo Nascimento

### 1. Fazer uma query para o campo name utilizando explain para ver o resultado da busca

> **OBS:** Minha versão do mongodb é 2.6

```JS
leonardo(mongod-2.6.11) be-mean> db.restaurantes.find({"name":"C & C Catering Service"}).explain('executionStats');
{
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
  "millis": 27,
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
  "server": "leonardo:27017",
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

### 2. Criar um index um para o campo name

```JS
leonardo(mongod-2.6.11) be-mean> db.restaurantes.createIndex({ name: 1 });
{
  "createdCollectionAutomatically": false,
  "numIndexesBefore": 1,
  "numIndexesAfter": 2,
  "ok": 1
}

leonardo(mongod-2.6.11) be-mean> db.restaurantes.getIndexes();
[
  {
    "v": 1,
    "key": {
      "_id": 1
    },
    "name": "_id_",
    "ns": "be-mean.restaurantes"
  },
  {
    "v": 1,
    "key": {
      "name": 1
    },
    "name": "name_1",
    "ns": "be-mean.restaurantes"
  }
]

```

### 3. Refazer a query para o campo name utilizando explain para ver o resultado da busca

```JS
leonardo(mongod-2.6.11) be-mean>  db.restaurantes.find({"name":"C & C Catering Service"}).explain('executionStats');
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
        "C & C Catering Service",
        "C & C Catering Service"
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
            "C & C Catering Service",
            "C & C Catering Service"
          ]
        ]
      }
    }
  ],
  "server": "leonardo:27017",
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
        "boundsVerbose": "field #0['name']: [\"C & C Catering Service\", \"C & C Catering Service\"]",
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

### 4. Fazer uma query para dois campos juntos utilizando explain para ver o resultado da busca

```JS
leonardo(mongod-2.6.11) be-mean> db.restaurantes.find({"borough":"Bronx", "cuisine": "African"}).explain('executionStats');
{
  "cursor": "BasicCursor",
  "isMultiKey": false,
  "n": 31,
  "nscannedObjects": 25359,
  "nscanned": 25359,
  "nscannedObjectsAllPlans": 25359,
  "nscannedAllPlans": 25359,
  "scanAndOrder": false,
  "indexOnly": false,
  "nYields": 198,
  "nChunkSkips": 0,
  "millis": 24,
  "allPlans": [
    {
      "cursor": "BasicCursor",
      "isMultiKey": false,
      "n": 31,
      "nscannedObjects": 25359,
      "nscanned": 25359,
      "scanAndOrder": false,
      "indexOnly": false,
      "nChunkSkips": 0
    }
  ],
  "server": "leonardo:27017",
  "filterSet": false,
  "stats": {
    "type": "COLLSCAN",
    "works": 25361,
    "yields": 198,
    "unyields": 198,
    "invalidates": 0,
    "advanced": 31,
    "needTime": 25329,
    "needFetch": 0,
    "isEOF": 1,
    "docsTested": 25359,
    "children": [ ]
  }
}

```

### 5. Criar um index para esses dois campos 

```JS
leonardo(mongod-2.6.11) be-mean> db.restaurantes.getIndexes()
[
  {
    "v": 1,
    "key": {
      "_id": 1
    },
    "name": "_id_",
    "ns": "be-mean.restaurantes"
  },
  {
    "v": 1,
    "key": {
      "name": 1
    },
    "name": "name_1",
    "ns": "be-mean.restaurantes"
  },
  {
    "v": 1,
    "key": {
      "borough": 1,
      "cuisine": 1
    },
    "name": "borough_1_cuisine_1",
    "ns": "be-mean.restaurantes"
  }
]

```

### 6. Refazer a query para os dois campos juntos utilizando explain para ver o resultado da busca

```JS
leonardo(mongod-2.6.11) be-mean> db.restaurantes.find({"borough":"Bronx", "cuisine": "African"}).explain('executionStats');
{
  "cursor": "BtreeCursor borough_1_cuisine_1",
  "isMultiKey": false,
  "n": 31,
  "nscannedObjects": 31,
  "nscanned": 31,
  "nscannedObjectsAllPlans": 31,
  "nscannedAllPlans": 31,
  "scanAndOrder": false,
  "indexOnly": false,
  "nYields": 0,
  "nChunkSkips": 0,
  "millis": 0,
  "indexBounds": {
    "borough": [
      [
        "Bronx",
        "Bronx"
      ]
    ],
    "cuisine": [
      [
        "African",
        "African"
      ]
    ]
  },
  "allPlans": [
    {
      "cursor": "BtreeCursor borough_1_cuisine_1",
      "isMultiKey": false,
      "n": 31,
      "nscannedObjects": 31,
      "nscanned": 31,
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
            "African",
            "African"
          ]
        ]
      }
    }
  ],
  "server": "leonardo:27017",
  "filterSet": false,
  "stats": {
    "type": "FETCH",
    "works": 32,
    "yields": 0,
    "unyields": 0,
    "invalidates": 0,
    "advanced": 31,
    "needTime": 0,
    "needFetch": 0,
    "isEOF": 1,
    "alreadyHasObj": 0,
    "forcedFetches": 0,
    "matchTested": 0,
    "children": [
      {
        "type": "IXSCAN",
        "works": 32,
        "yields": 0,
        "unyields": 0,
        "invalidates": 0,
        "advanced": 31,
        "needTime": 0,
        "needFetch": 0,
        "isEOF": 1,
        "keyPattern": "{ borough: 1.0, cuisine: 1.0 }",
        "isMultiKey": 0,
        "boundsVerbose": "field #0['borough']: [\"Bronx\", \"Bronx\"], field #1['cuisine']: [\"African\", \"African\"]",
        "yieldMovedCursor": 0,
        "dupsTested": 0,
        "dupsDropped": 0,
        "seenInvalidated": 0,
        "matchTested": 0,
        "keysExamined": 31,
        "children": [ ]
      }
    ]
  }
}

```