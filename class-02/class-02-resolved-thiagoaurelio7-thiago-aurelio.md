# MongoDB - Aula 02 - Exercício
autor: **Thiago Aurélio da Cunha**

## Listagem das databases (passo 2)
    ```
    MacBook(mongod-3.0.7) be-mean> use be-mean-pokemons
    switched to db be-mean-pokemons
    MacBook(mongod-3.0.7) be-mean-pokemons> show dbs
    be-mean → 0.078GB
    local   → 0.078GB
    test    → 0.078GB
    MacBook(mongod-3.0.7) be-mean-pokemons> 
    
    ```
## Listagem das coleções (passo 3)
    ```
    MacBook(mongod-3.0.7) be-mean-pokemons> show collections
    pokemons       → 0.000MB / 0.008MB
    system.indexes → 0.000MB / 0.008MB
    
    ```

## Cadastro dos pokemons (passo 4)
    ```
    MacBook(mongod-3.0.7) be-mean-pokemons> var pokemon =   [{name:"Wartortle",description:"Itstailislarge",type:"Água",attack:40,height:1.0,defense:40},{name:"Blastoise",description:"Blastoise has water spouts",type:"Água",attack:40,height:1.6,defense:40},{name:"Metapod",description:"Is as hard as an iron slab",type:"Grass",attack:10,height:0.7,defense:30},{name:"Butterfree",description:"Has a superior ability",type:"Fire",attack:20,height:1.1,defense:20}, {name:"Weedle",description:"Has an extremely acute sense of smell",type:"Bug Poison",attack:20, height: 0.3, defense: 20}]
    
    MacBook(mongod-3.0.7) be-mean-pokemons> pokemon
    [
      {
        "name": "Wartortle",
        "description": "Itstailislarge",
        "type": "Água",
        "attack": 40,
        "height": 1,
        "defense": 40
      },
      {
        "name": "Blastoise",
        "description": "Blastoise has water spouts",
        "type": "Água",
        "attack": 40,
        "height": 1.6,
        "defense": 40
      },
      {
        "name": "Metapod",
        "description": "Is as hard as an iron slab",
        "type": "Grass",
        "attack": 10,
        "height": 0.7,
        "defense": 30
      },
      {
        "name": "Butterfree",
        "description": "Has a superior ability",
        "type": "Fire",
        "attack": 20,
        "height": 1.1,
        "defense": 20
      },
      {
        "name": "Weedle",
        "description": "Has an extremely acute sense of smell",
        "type": "Bug Poison",
        "attack": 20,
        "height": 0.3,
        "defense": 20
      }
    ]
    
    MacBook(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(pokemon)
    Inserted 1 record(s) in 14ms
    BulkWriteResult({
      "writeErrors": [ ],
      "writeConcernErrors": [ ],
      "nInserted": 5,
      "nUpserted": 0,
      "nMatched": 0,
      "nModified": 0,
      "nRemoved": 0,
      "upserted": [ ]
    })
    
    ```

## Lista dos pokemons (passo 5)
    ```
    MacBook(mongod-3.0.7) be-mean-pokemons> db.pokemons.find()
    {
      "_id": ObjectId("564ba6af564a7039fb6a3da1"),
      "name": "Squirtle",
      "Description": "Pokemon nadador :D",
      "type": "Água",
      "Attack": "30",
      "height": 0.5,
      "defense": 30
    }
    {
      "_id": ObjectId("564bb030564a7039fb6a3da2"),
      "name": "Wartortle",
      "description": "Itstailislarge",
      "type": "Água",
      "attack": 40,
      "height": 1,
      "defense": 40
    }
    {
      "_id": ObjectId("564bb11d564a7039fb6a3da4"),
      "name": "Wartortle",
      "description": "Itstailislarge",
      "type": "Água",
      "attack": 40,
      "height": 1,
      "defense": 40
    }
    {
      "_id": ObjectId("564bb11d564a7039fb6a3da5"),
      "name": "Blastoise",
      "description": "Blastoise has water spouts",
      "type": "Água",
      "attack": 40,
      "height": 1.6,
      "defense": 40
    }
    {
      "_id": ObjectId("564bb11d564a7039fb6a3da6"),
      "name": "Metapod",
      "description": "Is as hard as an iron slab",
      "type": "Grass",
      "attack": 10,
      "height": 0.7,
      "defense": 30
    }
    {
      "_id": ObjectId("564bb11d564a7039fb6a3da7"),
      "name": "Butterfree",
      "description": "Has a superior ability",
      "type": "Fire",
      "attack": 20,
      "height": 1.1,
      "defense": 20
    }
    {
      "_id": ObjectId("564bb11d564a7039fb6a3da8"),
      "name": "Weedle",
      "description": "Has an extremely acute sense of smell",
      "type": "Bug Poison",
      "attack": 20,
      "height": 0.3,
      "defense": 20
    }
    Fetched 7 record(s) in 15ms
    ```
## Pikachu (passo 6)
    ```
    MacBook(mongod-3.0.7) be-mean-pokemons> var query = {"name": "Weedle"}
    MacBook(mongod-3.0.7) be-mean-pokemons> query
    {
      "name": "Weedle"
    }
    MacBook(mongod-3.0.7) be-mean-pokemons> var poke = db.pokemons.findOne(query)
    MacBook(mongod-3.0.7) be-mean-pokemons> poke
    {
      "_id": ObjectId("564bb11d564a7039fb6a3da8"),
      "name": "Weedle",
      "description": "Has an extremely acute sense of smell",
      "type": "Bug Poison",
      "attack": 20,
      "height": 0.3,
      "defense": 20
    }
    ```
## Atualização do Pikachu (passo 6)
    ```
    MacBook(mongod-3.0.7) be-mean-pokemons> var query = {"name": "Weedle"}
    MacBook(mongod-3.0.7) be-mean-pokemons> query
    {
      "name": "Weedle"
    }
    MacBook(mongod-3.0.7) be-mean-pokemons> var poke = db.pokemons.findOne(query)
    MacBook(mongod-3.0.7) be-mean-pokemons> poke
    {
      "_id": ObjectId("564bb11d564a7039fb6a3da8"),
      "name": "Weedle",
      "description": "Has an extremely acute sense of smell",
      "type": "Bug Poison",
      "attack": 20,
      "height": 0.3,
      "defense": 20
    }
    MacBook(mongod-3.0.7) be-mean-pokemons> poke.description
    Has an extremely acute sense of smell
    MacBook(mongod-3.0.7) be-mean-pokemons> poke.description = "Pokemon MACONHEIRO"
    Pokemon MACONHEIRO
    MacBook(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(poke)
    Updated 1 existing record(s) in 12ms
    WriteResult({
      "nMatched": 1,
      "nUpserted": 0,
      "nModified": 1
    })
    ```