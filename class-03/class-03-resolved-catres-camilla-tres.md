# MongoDB - Aula 03 - Exercício
autor: Camilla Tres

## Liste todos Pokemons com a altura **menor que** 0.5;

    camilla-Mean(mongod-3.0.7) be-mean-pokemons> var query = {height: {$lt: 0.5}}
    camilla-Mean(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
    Fetched 0 record(s) in 0ms

## Liste todos Pokemons com a altura **maior ou igual que** 0.5

    camilla-Mean(mongod-3.0.7) be-mean-pokemons> var query = {height: {$gte: 0.5}}
    camilla-Mean(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
    {
      "_id": ObjectId("564bedbb4464d07588af9ef1"),
      "name": "Dragonair",
      "description": "Diz que é um dragão mas parece o Seiya de Pegaso",
      "type": "dragon",
      "attack": 40,
      "defense": 30,
      "height": 4
    }
    {
      "_id": ObjectId("564bedbb4464d07588af9ef2"),
      "name": "Mr.Mime",
      "description": "Palhaço estranho",
      "type": "psychic",
      "attack": 20,
      "defense": 30,
      "height": 1.3
    }
    {
      "_id": ObjectId("564bedbb4464d07588af9ef3"),
      "name": "Larvitar",
      "description": "tem um chifre que justifica a cara de mal",
      "type": "rock",
      "attack": 30,
      "defense": 20,
      "height": 0.6
    }
    {
      "_id": ObjectId("564bedbb4464d07588af9ef4"),
      "name": "Shelgon",
      "description": "Tatu concha",
      "type": "dragon",
      "attack": 50,
      "defense": 40,
      "height": 1.1
    }
    {
      "_id": ObjectId("564bedbb4464d07588af9ef5"),
      "name": "Gloom",
      "description": "planta babona",
      "type": "grass",
      "attack": 30,
      "defense": 30,
      "height": 0.8
    }
    {
      "_id": ObjectId("564bedbb4464d07588af9ef6"),
      "name": "Glameow",
      "description": "Um Meowth, com muito mais glamour",
      "type": "normal",
      "attack": 30,
      "defense": 20,
      "height": 0.5
    }
    Fetched 6 record(s) in 4ms

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama

    camilla-Mean(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{height: {$lte: 0.5}}, {type: "grass"}]}
    camilla-Mean(mongod-3.0.7) be-mean-pokemons> query
    {
      "$and": [
        {
          "height": {
            "$lte": 0.5
          }
        },
        {
          "type": "grass"
        }
      ]
    }
    camilla-Mean(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
    Fetched 0 record(s) in 1ms

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5

    camilla-Mean(mongod-3.0.7) be-mean-pokemons> var query = {$or: [{name: "Pikachu"}, {attack: {$lte: 0.5}}]}
    camilla-Mean(mongod-3.0.7) be-mean-pokemons> query
    {
      "$or": [
        {
          "name": "Pikachu"
        },
        {
          "attack": {
            "$lte": 0.5
          }
        }
      ]
    }
    camilla-Mean(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
    Fetched 0 record(s) in 1ms

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5

    camilla-Mean(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}
    camilla-Mean(mongod-3.0.7) be-mean-pokemons> query
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
    camilla-Mean(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
    Fetched 0 record(s) in 1ms
    
