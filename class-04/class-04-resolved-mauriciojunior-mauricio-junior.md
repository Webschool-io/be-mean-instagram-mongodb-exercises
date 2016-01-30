
# MongoDB - Aula 04 - Exercício
Autor: Maurício Júnior

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

    mauriciojunior(mongod-3.0.6) be-mean-pokemons> var query = {name: /charmander/i }
    mauriciojunior(mongod-3.0.6) be-mean-pokemons> var mod = { $pushAll: { moves: [ 'Hone Claws', 'Dragon Claw' ] } }
    mauriciojunior(mongod-3.0.6) be-mean-pokemons> db.pokemons.update(query, mod)
    Updated 1 existing record(s) in 3ms
    WriteResult({
      "nMatched": 1,
      "nUpserted": 0,
      "nModified": 1
    })
    mauriciojunior(mongod-3.0.6) be-mean-pokemons> db.pokemons.find(query)
    {
      "_id": ObjectId("56ac06e7f2b3b6c73fbc00b2"),
      "name": "Charmander",
      "description": "Charmander is a bipedal, reptilian Pokémon with an orange body, though its underside and soles are cream-colored.",
      "type": "Fire",
      "attack": 52,
      "height": 0.6,
      "defense": 43,
      "moves": [
        "Hone Claws",
        "Dragon Claw"
      ]
    }
    Fetched 1 record(s) in 5ms

    mauriciojunior(mongod-3.0.6) be-mean-pokemons> var query = {name: /pikachu/i }
    mauriciojunior(mongod-3.0.6) be-mean-pokemons> var mod = { $pushAll: { moves: [ 'Feint', 'Spark' ] } }
    mauriciojunior(mongod-3.0.6) be-mean-pokemons> db.pokemons.update(query, mod)
    Updated 1 existing record(s) in 3ms
    WriteResult({
      "nMatched": 1,
      "nUpserted": 0,
      "nModified": 1
    })
    mauriciojunior(mongod-3.0.6) be-mean-pokemons> db.pokemons.find(query)
    {
      "_id": ObjectId("56a96fd5416287dcd8c67cb0"),
      "name": "Pikachu",
      "description": "Pikachu is a short, chubby rodent Pokémon. It is covered in yellow fur, and its ears are long and pointed with black tips.",
      "type": "Electric",
      "attack": 55,
      "height": 0.6,
      "moves": [
        "choque do elétrico",
        "ataque rápido",
        "bola elétrica",
        "Feint",
        "Spark"
      ]
    }
    Fetched 1 record(s) in 2ms

    mauriciojunior(mongod-3.0.6) be-mean-pokemons> var query = {name: /bulbassauro/i }
    mauriciojunior(mongod-3.0.6) be-mean-pokemons> var mod = { $pushAll: { moves: [ 'Vine Whip', 'Razor Leaf' ] } }
    mauriciojunior(mongod-3.0.6) be-mean-pokemons> db.pokemons.update(query, mod)
    Updated 1 existing record(s) in 2ms
    WriteResult({
      "nMatched": 1,
      "nUpserted": 0,
      "nModified": 1
    })
    mauriciojunior(mongod-3.0.6) be-mean-pokemons> db.pokemons.find(query)
    {
      "_id": ObjectId("56ac0663f2b3b6c73fbc00b1"),
      "name": "Bulbassauro",
      "description": "ulbasaur is a small, quadruped Pokémon with green to bluish-green skin and darker green patches.",
      "type": "Grama",
      "attack": 49,
      "height": 0.7,
      "defense": 49,
      "moves": [
        "Vine Whip",
        "Razor Leaf"
      ]
    }
    Fetched 1 record(s) in 2ms

    mauriciojunior(mongod-3.0.6) be-mean-pokemons> var query = {name: /squirtle/i }
    mauriciojunior(mongod-3.0.6) be-mean-pokemons> var mod = { $pushAll: { moves: [ 'Water Gun', 'Bubble' ] } }
    mauriciojunior(mongod-3.0.6) be-mean-pokemons> db.pokemons.update(query, mod)
    Updated 1 existing record(s) in 3ms
    WriteResult({
      "nMatched": 1,
      "nUpserted": 0,
      "nModified": 1
    })
    mauriciojunior(mongod-3.0.6) be-mean-pokemons> db.pokemons.find(query)
    {
      "_id": ObjectId("56ac059bf2b3b6c73fbc00b0"),
      "name": "Squirtle",
      "description": "Along with Bulbasaur and Charmander, Squirtle is one of three starter Pokémon of Kanto available at the beginning of Pokémon Red, Green, Blue, FireRed.",
      "type": "Água",
      "attack": 48,
      "height": 0.5,
      "defense": 65,
      "moves": [
        "Water Gun",
        "Bubble"
      ]
    }
    Fetched 1 record(s) in 2ms


## **Adicionar** 1 movimento em todos os pokemons: `desvio`.
    mauriciojunior(mongod-3.0.6) be-mean-pokemons> var query = {}
    mauriciojunior(mongod-3.0.6) be-mean-pokemons> var mod = { $push: { moves: 'desviation' } }
    mauriciojunior(mongod-3.0.6) be-mean-pokemons> var options = { multi: true }
    mauriciojunior(mongod-3.0.6) be-mean-pokemons> db.pokemons.update(query, mod, options)
    Updated 10 existing record(s) in 2ms
    WriteResult({
      "nMatched": 10,
      "nUpserted": 0,
      "nModified": 10
    })



## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".

    mauriciojunior(mongod-3.0.6) be-mean-pokemons> var query = {name: 'AindaNaoExisteMon'}
    mauriciojunior(mongod-3.0.6) be-mean-pokemons> var mod = {
    ... $setOnInsert: {
    ...     attack: null,
    ...     defense: null,
    ...     height: null, 
    ...     description: "Sem maiores informações"    
    ...   }
    ... }
    mauriciojunior(mongod-3.0.6) be-mean-pokemons> db.pokemons.update(query, mod, options)
    
    Updated 1 new record(s) in 2ms
    WriteResult({
      "nMatched": 0,
      "nUpserted": 1,
      "nModified": 0,
      "_id": ObjectId("56ac0f8751009dcb41b29dbd")
    })
    
    mauriciojunior(mongod-3.0.6) be-mean-pokemons> db.pokemons.find(query)
    {
      "_id": ObjectId("56ac0f8751009dcb41b29dbd"),
      "name": "AindaNaoExisteMon",
      "attack": null,
      "defense": null,
      "height": null,
      "description": "Sem maiores informações"
    }
    Fetched 1 record(s) in 2ms


## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.
    mauriciojunior(mongod-3.0.6) be-mean-pokemons> var query = { moves: { $in: [ /investida/i, /Feint/i] } }
    mauriciojunior(mongod-3.0.6) be-mean-pokemons> db.pokemons.find(query)
    {
      "_id": ObjectId("56a96fd5416287dcd8c67cb0"),
      "name": "Pikachu",
      "description": "Pikachu is a short, chubby rodent Pokémon. It is covered in yellow fur, and its ears are long and pointed with black tips.",
      "type": "Electric",
      "attack": 55,
      "height": 0.6,
      "moves": [
        "choque do elétrico",
        "ataque rápido",
        "bola elétrica",
        "Feint",
        "Spark",
        "deviation"
      ]
    }
    Fetched 1 record(s) in 1ms


## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.
    mauriciojunior(mongod-3.0.6) be-mean-pokemons> var query = { moves: { $all: [ /Water Gun/i, /deviation/i] } }
    mauriciojunior(mongod-3.0.6) be-mean-pokemons> db.pokemons.find(query)
    {
      "_id": ObjectId("56ac059bf2b3b6c73fbc00b0"),
      "name": "Squirtle",
      "description": "Along with Bulbasaur and Charmander, Squirtle is one of three starter Pokémon of Kanto available at the beginning of Pokémon Red, Green, Blue, FireRed.",
      "type": "Água",
      "attack": 48,
      "height": 0.5,
      "defense": 65,
      "moves": [
        "Water Gun",
        "Bubble",
        "deviation"
      ]
    }
    Fetched 1 record(s) in 2ms


## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.
    mauriciojunior(mongod-3.0.6) be-mean-pokemons> var query = { type: { $not: /elétrico/i } }
    mauriciojunior(mongod-3.0.6) be-mean-pokemons> db.pokemons.find(query)
    
    Fetched 11 record(s) in 7ms


## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.
    mauriciojunior(mongod-3.0.6) be-mean-pokemons> query
    {
      "$and": [
        {
          "moves": {
            "$in": [
              /investida/i
            ]
          }
        },
        {
          "defense": {
            "$not": {
              "$lte": 49
            }
          }
        }
      ]
    }
    mauriciojunior(mongod-3.0.6) be-mean-pokemons> db.pokemons.find(query)
    Fetched 0 record(s) in 0ms


## Remova **todos** os pokemons do tipo água E com attack menor que 50.
    mauriciojunior(mongod-3.0.6) be-mean-pokemons> query
    {
      "$and": [
        {
          "type": /water/i
        },
        {
          "attack": {
            "$lt": 50
          }
        }
      ]
    }
    mauriciojunior(mongod-3.0.6) be-mean-pokemons> db.pokemons.remove(query)
    Removed 1 record(s) in 3ms
    WriteResult({
      "nRemoved": 1
    })

