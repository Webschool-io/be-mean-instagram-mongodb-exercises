#MongoDB - Aula 06 - Exercícios
autor: Dayvson Sales  

##1. Fazer uma query para o campo `name` utilizando `explain` para ver o resultado da busca
```js
dayvs0n-notebook(mongod-2.4.9) be-mean-pokemons> db.pokemons.find({name: "Beedrill"}).explain('executionStats')
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
  "nYields": 0,
  "nChunkSkips": 0,
  "millis": 1,
  "indexBounds": {
    
  },
  "allPlans": [
    {
      "cursor": "BasicCursor",
      "n": 1,
      "nscannedObjects": 620,
      "nscanned": 620,
      "indexBounds": {
        
      }
    }
  ],
  "server": "dayvs0n-notebook:27017"
}
```

##2. Criar um `index` um para o campo `name`
```js
db.pokemons.createIndex({ name: 1})
Inserted 1 record(s) in 4ms
```

##3. Refazer a query para o campo `name` utilizando `explain` para ver o resultado da busca
```js
dayvs0n-notebook(mongod-2.4.9) be-mean-pokemons> db.pokemons.find({name: "Beedrill"}).explain('executionStats')
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
        "Beedrill",
        "Beedrill"
      ]
    ]
  },
  "allPlans": [
    {
      "cursor": "BtreeCursor name_1",
      "n": 1,
      "nscannedObjects": 1,
      "nscanned": 1,
      "indexBounds": {
        "name": [
          [
            "Beedrill",
            "Beedrill"
          ]
        ]
      }
    }
  ],
  "oldPlan": {
    "cursor": "BtreeCursor name_1",
    "indexBounds": {
      "name": [
        [
          "Beedrill",
          "Beedrill"
        ]
      ]
    }
  },
  "server": "dayvs0n-notebook:27017"
}
```

##4. Fazer uma query para dois campos juntos utilizando `explain` para ver o resultado da busca
```js
dayvs0n-notebook(mongod-2.4.9) be-mean-pokemons> db.pokemons.find({$and: [{speed: {$gt: 10}, hp: {$lt: 100}}]}).explain('executionStats')
{
  "cursor": "BasicCursor",
  "isMultiKey": false,
  "n": 542,
  "nscannedObjects": 620,
  "nscanned": 620,
  "nscannedObjectsAllPlans": 620,
  "nscannedAllPlans": 620,
  "scanAndOrder": false,
  "indexOnly": false,
  "nYields": 0,
  "nChunkSkips": 0,
  "millis": 1,
  "indexBounds": {
    
  },
  "allPlans": [
    {
      "cursor": "BasicCursor",
      "n": 542,
      "nscannedObjects": 620,
      "nscanned": 620,
      "indexBounds": {
        
      }
    }
  ],
  "server": "dayvs0n-notebook:27017"
}
```

##5. Criar um `index` para esses dois campos juntos
```js
dayvs0n-notebook(mongod-2.4.9) be-mean-pokemons> db.pokemons.createIndex({speed: 1, hp: 1})
Inserted 1 record(s) in 1ms
```

##6. Refazer a query para os dois campos juntos utilizando `explain` para ver o resultado da busca
```js
dayvs0n-notebook(mongod-2.4.9) be-mean-pokemons> db.pokemons.find({$and: [{speed: {$gt: 10}, hp: {$lt: 100}}]}).explain('executionStats')
{
  "cursor": "BtreeCursor speed_1_hp_1",
  "isMultiKey": false,
  "n": 542,
  "nscannedObjects": 463,
  "nscanned": 575,
  "nscannedObjectsAllPlans": 562,
  "nscannedAllPlans": 682,
  "scanAndOrder": false,
  "indexOnly": false,
  "nYields": 0,
  "nChunkSkips": 0,
  "millis": 3,
  "indexBounds": {
    "speed": [
      [
        10,
        1.7976931348623157e+308
      ]
    ],
    "hp": [
      [
        -1.7976931348623157e+308,
        100
      ]
    ]
  },
  "allPlans": [
    {
      "cursor": "BtreeCursor speed_1_hp_1",
      "n": 463,
      "nscannedObjects": 463,
      "nscanned": 575,
      "indexBounds": {
        "speed": [
          [
            10,
            1.7976931348623157e+308
          ]
        ],
        "hp": [
          [
            -1.7976931348623157e+308,
            100
          ]
        ]
      }
    },
    {
      "cursor": "BasicCursor",
      "n": 97,
      "nscannedObjects": 107,
      "nscanned": 107,
      "indexBounds": {
        
      }
    }
  ],
  "server": "dayvs0n-notebook:27017"
}

```
