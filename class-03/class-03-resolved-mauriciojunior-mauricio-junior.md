
# MongoDB - Aula 03 - Exercício
autor: Maurício Júnior

## Pokemons com altura **menor que** 0.5 (passo 1)
    mauriciojunior(mongod-3.0.6) be-mean-pokemons> query
    {
      "height": {
        "$lt": 0.5
      }
    }
    mauriciojunior(mongod-3.0.6) be-mean-pokemons> db.pokemons.find(query)
    {
      "_id": ObjectId("56a831d6b2fc786bc75bc6dc"),
      "name": "Oddish",
      "description": "Oddish resembles a blue plant bulb with a round body, beady red eyes, and oval, foot-like roots.",
      "attack": 75,
      "defense": 65,
      "height": 0.4
    }
    {
      "_id": ObjectId("56a831d6b2fc786bc75bc6e0"),
      "name": "Vileplume",
      "description": "Vileplume is a blue, bipedal Pokémon with rudimentary hands and feet.",
      "attack": 5,
      "defense": 4,
      "height": 0.4
    }
    Fetched 2 record(s) in 1ms




## Pokemons com altura **maior ou igual que** 0.5 (passo 2)
    mauriciojunior(mongod-3.0.6) be-mean-pokemons> query
    {
      "height": {
        "$gte": 0.5
      }
    }
    mauriciojunior(mongod-3.0.6) be-mean-pokemons> db.pokemons.find(query)
    {
      "_id": ObjectId("56a831d6b2fc786bc75bc6dd"),
      "name": "Arbok",
      "description": "It has a large hood just below its head.",
      "attack": 65,
      "defense": 79,
      "height": 35
    }
    {
      "_id": ObjectId("56a831d6b2fc786bc75bc6de"),
      "name": "Krabby",
      "description": "As a crustacean, Krabby has a strong outer shell protecting its small body.",
      "attack": 105,
      "defense": 90,
      "height": 4
    }
    {
      "_id": ObjectId("56a831d6b2fc786bc75bc6df"),
      "name": "Koffing",
      "description": "Koffing is a spherical Pokémon filled with toxic gasses.",
      "attack": 65,
      "defense": 95,
      "height": 6
    }
    {
      "_id": ObjectId("56a831d6b2fc786bc75bc6e1"),
      "name": "Venomoth",
      "description": "Venomoth is an insectoid creature with a light purple body.",
      "attack": 65,
      "defense": 60,
      "height": 15
    }
    Fetched 4 record(s) in 2ms




## Pokemons com altura **menor ou igual que** 0.5* **E** do tipo grama (passo 3)
    mauriciojunior(mongod-3.0.6) be-mean-pokemons> query
    {
      "$and": [
        {
          "height": {
            "$lte": 0.5
          }
        },
        {
          "type": /grama/i
        }
      ]
    }
    mauriciojunior(mongod-3.0.6) be-mean-pokemons> db.pokemons.find(query)
    {
      "_id": ObjectId("56a831d6b2fc786bc75bc6e0"),
      "name": "Vileplume",
      "description": "Vileplume is a blue, bipedal Pokémon with rudimentary hands and feet.",
      "attack": 5,
      "defense": 4,
      "height": 0.4,
      "type": "grama"
    }
    Fetched 1 record(s) in 1ms

## Pokemons com nome `Pikachu` **OU** com attack **menor ou igual que** 0.5 (passo 4)
    mauriciojunior(mongod-3.0.6) be-mean-pokemons> query
    {
      "$or": [
        {
          "name": /pikachu/i
        },
        {
          "attack": {
            "$lte": 0.5
          }
        }
      ]
    }
    mauriciojunior(mongod-3.0.6) be-mean-pokemons> db.pokemons.find(query)
    {
      "_id": ObjectId("56a96fd5416287dcd8c67cb0"),
      "name": "Pikachu",
      "description": "Pikachu is a short, chubby rodent Pokémon. It is covered in yellow fur, and its ears are long and pointed with black tips.",
      "type": "Electric",
      "attack": 55,
      "height": 0.6
    }
    Fetched 1 record(s) in 1ms

## Pokemons com attack **MAIOR OU IGUAL QUE** 48 **E** com height **menor ou igual que** 0.5 (passo 5) 
    mauriciojunior(mongod-3.0.6) be-mean-pokemons> query
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
    mauriciojunior(mongod-3.0.6) be-mean-pokemons> db.pokemons.find(query)
    {
      "_id": ObjectId("56a831d6b2fc786bc75bc6dc"),
      "name": "Oddish",
      "description": "Oddish resembles a blue plant bulb with a round body, beady red eyes, and oval, foot-like roots.",
      "attack": 75,
      "defense": 65,
      "height": 0.4
    }
    Fetched 1 record(s) in 1ms
    
