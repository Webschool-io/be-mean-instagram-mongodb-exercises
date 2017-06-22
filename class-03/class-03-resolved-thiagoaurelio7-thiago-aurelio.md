# MongoDB - Aula 03 - Exercício
autor: **Thiago Aurélio da Cunha**

## Liste todos Pokemons com a altura **menor que** 0.5;

    ```
    MacBook(mongod-3.0.7) be-mean-pokemons>  var query = {height: {$lt: 0.5}}
    MacBook(mongod-3.0.7) be-mean-pokemons> query
    {
      "height": {
        "$lt": 0.5
      }
    }
    MacBook(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
    {
      "_id": ObjectId("564bb11d564a7039fb6a3da8"),
      "name": "Weedle",
      "description": "Pokemon MACONHEIRO",
      "type": "Bug Poison",
      "attack": 20,
      "height": 0.3,
      "defense": 20
    }
    Fetched 1 record(s) in 6ms
    ```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5
    ```
    MacBook(mongod-3.0.7) be-mean-pokemons> var query = {height: {$gte: 0.5}}
    MacBook(mongod-3.0.7) be-mean-pokemons> query
    {
      "height": {
        "$gte": 0.5
      }
    }
    MacBook(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
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
    Fetched 6 record(s) in 7ms
    ```

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama
    ```
    MacBook(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{height: {$lte: 0.5}}, {type: /Grass/}]}
    MacBook(mongod-3.0.7) be-mean-pokemons> query
    {
      "$and": [
        {
          "height": {
            "$lte": 0.5
          }
        },
        {
          "type": /Grass/
        }
      ]
    }
    MacBook(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
    Fetched 0 record(s) in 9ms
    ```

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5
    ```
    MacBook(mongod-3.0.7) be-mean-pokemons> var query = {$or: [{attack: {$lte: 0.5}}, {name: /pikachu/i}]}
    MacBook(mongod-3.0.7) be-mean-pokemons> query
    {
      "$or": [
        {
          "attack": {
            "$lte": 0.5
          }
        },
        {
          "name": /pikachu/i
        }
      ]
    }
    MacBook(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
    Fetched 0 record(s) in 1ms
    ```

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5
    ```
    MacBook(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{attack: {$gte: 48}}, {height: {$lte : 0.5}}]}
    MacBook(mongod-3.0.7) be-mean-pokemons> query
    {
      "$and": [
        {
          "attack": {
            "$gte": 48
          }
        },
        {
          "height": {
            "$lte": 0.5
          }
        }
      ]
    }
    MacBook(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
    Fetched 0 record(s) in 1ms
    ```