#MongoDB - Aula 06 - Exercício

autor: Marcelo Henrique


## 1 - Fazer uma query para o campo name utilizando explain para ver o resultado da busca

MarceloLocal(mongod-2.4.9) be-mean-instagram> db.pokemons.find({ name: /pikachu/i }).explain('executionStats')
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
  "nYields": 1,
  "nChunkSkips": 0,
  "millis": 133,
  "indexBounds": {
    
  },
  "allPlans": [
    {
      "cursor": "BasicCursor",
      "n": 1,
      "nscannedObjects": 610,
      "nscanned": 610,
      "indexBounds": {
        
      }
    }
  ],
  "server": "MarceloLocal:27017"
}
MarceloLocal(mongod-2.4.9) be-mean-instagram> db.pokemons.find({ name: /pikachu/i }).explain('executionStats').nscannedObjects
610

## 2 - Criar um index um para o campo name

MarceloLocal(mongod-2.4.9) be-mean-instagram> db.pokemons.createIndex({ name: 1 })
Inserted 1 record(s) in 225ms

## 3 - Refazer a query para o campo name utilizando explain para ver o resultado da busca

MarceloLocal(mongod-2.4.9) be-mean-instagram> db.pokemons.find({ name: /pikachu/i }).explain('executionStats')
{
  "cursor": "BtreeCursor name_1 multi",
  "isMultiKey": false,
  "n": 1,
  "nscannedObjects": 1,
  "nscanned": 610,
  "nscannedObjectsAllPlans": 1,
  "nscannedAllPlans": 610,
  "scanAndOrder": false,
  "indexOnly": false,
  "nYields": 0,
  "nChunkSkips": 0,
  "millis": 1,
  "indexBounds": {
    "name": [
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
  "allPlans": [
    {
      "cursor": "BtreeCursor name_1 multi",
      "n": 1,
      "nscannedObjects": 1,
      "nscanned": 610,
      "indexBounds": {
        "name": [
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
  "server": "MarceloLocal:27017"
}

## 4 - Fazer uma query para dois campos juntos utilizando explain para ver o resultado da busca 

MarceloLocal(mongod-2.4.9) be-mean-instagram> db.pokemons.find({ $and:[ { attack: { $gt: 50 } }, { defense: { $gt: 30 } } ] }).explain('executionStats')
{
  "cursor": "BasicCursor",
  "isMultiKey": false,
  "n": 454,
  "nscannedObjects": 610,
  "nscanned": 610,
  "nscannedObjectsAllPlans": 610,
  "nscannedAllPlans": 610,
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
      "n": 454,
      "nscannedObjects": 610,
      "nscanned": 610,
      "indexBounds": {
        
      }
    }
  ],
  "server": "MarceloLocal:27017"
}

## 5 - Criar um index para esses dois campos juntos

MarceloLocal(mongod-2.4.9) be-mean-instagram> db.pokemons.createIndex({ attack: 1, defense: 1 })
Inserted 1 record(s) in 22ms


## 6 - Refazer a query para os dois campos juntos utilizando explain para ver o resultado da busca

MarceloLocal(mongod-2.4.9) be-mean-instagram> db.pokemons.find({ $and:[ { attack: { $gt: 50 } }, { defense: { $gt: 30 } } ] }).explain('executionStats').nscannedObjects
400

MarceloLocal(mongod-2.4.9) be-mean-instagram> db.pokemons.find({ $and:[ { attack: { $gt: 50 } }, { defense: { $gt: 30 } } ] }).explain('executionStats').millis
3




