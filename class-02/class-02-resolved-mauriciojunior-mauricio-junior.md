
# MongoDB - Aula 02 - Exercício
autor: Maurício Júnior

## Listagem das databases (passo 2)
    use be-mean-pokemons
    switched to db be-mean-pokemons
        
    show dbs
    be-mean           → 0.078GB
    be-mean-instagram → 0.078GB
    grocery           → 0.078GB
    local             → 0.078GB



## Listagem das coleções (passo 3)
    show collections
    mauriciojunior(mongod-3.0.6) be-mean-pokemons> 



## Cadastro dos pokemons (passo 4)

    var pokemons=[{  "name": "Oddish",  "description": "Oddish resembles a blue plant bulb with a round body, beady red eyes, and oval, foot-like roots.",  "attack": 75,  "defense": 65, "height": 0.4},{  "name": "Arbok",  "description": "Arbok is a serpent like Pokémon with purple scales all over its body.",  "attack": 65,  "defense": 79,  "height": 35},
    {  "name": "Krabby",  "description": "As a crustacean, Krabby has a strong outer shell protecting its small body.",  "attack": 105,  "defense": 90,  "height": 4},
    {  "name": "Koffing",  "description": "Koffing is a spherical Pokémon filled with toxic gasses.",  "attack": 65,  "defense": 95,  "height": 6},
    {  "name": "Vileplume",  "description": "Vileplume is a blue, bipedal Pokémon with rudimentary hands and feet.",  "attack": 5,  "defense": 4,  "height": 0.4},
    {  "name" : "Venomoth", "description" : "Venomoth is an insectoid creature with a light purple body.", "attack" : 65, "defense" : 60, "height" : 15 }]

    db.pokemons.insert(pokemons)
    Inserted 1 record(s) in 460ms
    BulkWriteResult({
    "writeErrors": [ ],
    "writeConcernErrors": [ ],
    "nInserted": 6,
    "nUpserted": 0,
    "nMatched": 0,
    "nModified": 0,
    "nRemoved": 0,
    "upserted": [ ]
    })
    


## Lista dos pokemons (passo 5)
    db.pokemons.find()
    {
      "_id": ObjectId("56a831d6b2fc786bc75bc6dc"),
      "name": "Oddish",
      "description": "Oddish resembles a blue plant bulb with a round body, beady red eyes, and oval, foot-like roots.",
      "attack": 75,
      "defense": 65,
      "height": 0.4
    }
    {
      "_id": ObjectId("56a831d6b2fc786bc75bc6dd"),
      "name": "Arbok",
      "description": "Arbok is a serpent like Pokémon with purple scales all over its body.",
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
      "_id": ObjectId("56a831d6b2fc786bc75bc6e0"),
      "name": "Vileplume",
      "description": "Vileplume is a blue, bipedal Pokémon with rudimentary hands and feet.",
      "attack": 5,
      "defense": 4,
      "height": 0.4
    }
    {
      "_id": ObjectId("56a831d6b2fc786bc75bc6e1"),
      "name": "Venomoth",
      "description": "Venomoth is an insectoid creature with a light purple body.",
      "attack": 65,
      "defense": 60,
      "height": 15
    }
    Fetched 6 record(s) in 4ms

## Pokemon (passo 6)
    mauriciojunior(mongod-3.0.6) be-mean-pokemons> var query = {"name": "Arbok"}
    mauriciojunior(mongod-3.0.6) be-mean-pokemons> var poke = db.pokemons.findOne(query)
    mauriciojunior(mongod-3.0.6) be-mean-pokemons> poke
    {
      "_id": ObjectId("56a831d6b2fc786bc75bc6dd"),
      "name": "Arbok",
      "description": "Arbok is a serpent like Pokémon with purple scales all over its body.",
      "attack": 65,
      "defense": 79,
      "height": 35
    }


## Atualização do Pokemon (passo 6)
    mauriciojunior(mongod-3.0.6) be-mean-pokemons> poke.description = 'It has a large hood just below its head.'
    It has a large hood just below its head.
    mauriciojunior(mongod-3.0.6) be-mean-pokemons> poke
    {
      "_id": ObjectId("56a831d6b2fc786bc75bc6dd"),
      "name": "Arbok",
      "description": "It has a large hood just below its head.",
      "attack": 65,
      "defense": 79,
      "height": 35
    }
    mauriciojunior(mongod-3.0.6) be-mean-pokemons> db.pokemons.save(poke)
    Updated 1 existing record(s) in 2ms
    WriteResult({
      "nMatched": 1,
      "nUpserted": 0,
      "nModified": 1
    })
    mauriciojunior(mongod-3.0.6) be-mean-pokemons> db.pokemons.findOne(query)
    {
      "_id": ObjectId("56a831d6b2fc786bc75bc6dd"),
      "name": "Arbok",
      "description": "It has a large hood just below its head.",
      "attack": 65,
      "defense": 79,
      "height": 35
    }


