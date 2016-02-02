# MongoDB - Aula 04 - Exercício
  
  ```
  Autor: Rafael Pessoni

  ```

##Adicionar dois ataques ao mesmo tempo para os seguintes pokemons:

  1. Pikachu
  2. Squirtle
  3. Bulbassauro
  4. Charmander

  ```
  localhost(mongod-3.2.0) be-mean-pokemons> var query = { $or: [{name: /pikachu/i}, {name: /squirtle/i}, {name: /charmander/i}, {name: /bulbassauro/i}]}
  localhost(mongod-3.2.0) be-mean-pokemons> query
  {
    "$or": [
      {
        "name": /pikachu/i
      },
      {
        "name": /squirtle/i
      },
      {
        "name": /charmander/i
      },
      {
        "name": /bulbassauro/i
      }
    ]
  }

  localhost(mongod-3.2.0) be-mean-pokemons> var mod = {$set: {moves: ['fugir', 'atacar']}}
  localhost(mongod-3.2.0) be-mean-pokemons> mod
  {
    "$set": {
      "moves": [
        "fugir",
        "atacar"
      ]
    }
  }

  localhost(mongod-3.2.0) be-mean-pokemons> var options = {multi: true}
  localhost(mongod-3.2.0) be-mean-pokemons> options
  {
    "multi": true
  }

  localhost(mongod-3.2.0) be-mean-pokemons> db.pokemons.update(query, mod, options)
  Updated 4 existing record(s) in 2ms
  WriteResult({
    "nMatched": 4,
    "nUpserted": 0,
    "nModified": 4
  })

  localhost(mongod-3.2.0) be-mean-pokemons> db.pokemons.find(query)
  {
    "_id": ObjectId("56915799046a0e39d3813d54"),
    "name": "Charmander",
    "description": "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokémon becomes enraged, the flame burns fiercely.",
    "attack": 300,
    "defense": 200,
    "height": 0.6,
    "moves": [
      "fugir",
      "atacar"
    ]
  }
  {
    "_id": ObjectId("569157a4046a0e39d3813d55"),
    "name": "Squirtle",
    "description": "Squirtle's shell is not merely used for protection. The shell's rounded shape and the grooves on its surface help minimize resistance in water, enabling this Pokémon to swim at high speeds.",
    "attack": 300,
    "defense": 300,
    "height": 0.5,
    "moves": [
      "fugir",
      "atacar"
    ]
  }
  {
    "_id": ObjectId("56942cdbb9ce80f9f4e07cba"),
    "name": "Pikachu",
    "description": "Rato de esgoto",
    "attack": 300,
    "defense": 300,
    "height": 0.5,
    "moves": [
      "fugir",
      "atacar"
    ]
  }
  {
    "_id": ObjectId("56942d11b9ce80f9f4e07cbb"),
    "name": "Bulbassauro",
    "description": "coisa doente",
    "attack": 300,
    "defense": 300,
    "height": 0.5,
    "moves": [
      "fugir",
      "atacar"
    ]
  }
  Fetched 4 record(s) in 6ms

  ```

##Adicionar o movimento 'desvio' em todos os pokemons.

  ```
  localhost(mongod-3.2.0) be-mean-pokemons> var mod = {$push: {moves: 'desvio'}}
  localhost(mongod-3.2.0) be-mean-pokemons> var options = {upsert: true, multi: true}
  localhost(mongod-3.2.0) be-mean-pokemons> var query = {}
  localhost(mongod-3.2.0) be-mean-pokemons> db.pokemons.update(query, mod, options)
  Updated 7 existing record(s) in 52ms
  WriteResult({
    "nMatched": 7,
    "nUpserted": 0,
    "nModified": 7
  })

  ```

##Adicionar o pokemon ```AindaNãoExisteMon```, caso ele não exista, e inserir todos os campos como ```null```
  
  ```
  localhost(mongod-3.2.0) be-mean-pokemons> var query = {name: /AindaNaoExisteMon/i}
  localhost(mongod-3.2.0) be-mean-pokemons> var mod = {$setOnInsert: {name: "AindaNaoExisteMon", description: "Sem maiores informações", type: null, attack: null, defense: null, height: null, active: null}}
  localhost(mongod-3.2.0) be-mean-pokemons> var options = {upsert: true}
  localhost(mongod-3.2.0) be-mean-pokemons> db.pokemons.update(query, mod, options)
  Updated 1 new record(s) in 1ms
  WriteResult({
    "nMatched": 0,
    "nUpserted": 1,
    "nModified": 0,
    "_id": ObjectId("5694316e56ac88807cd6b35c")
  })

  ```

##Pesquisar todos os pokemons que possuam o ataque investida e mais um pokemon que você adicionou

  ```
  localhost(mongod-3.2.0) be-mean-pokemons> var query = {moves: {$in: ['investida']}}
  localhost(mongod-3.2.0) be-mean-pokemons> db.pokemons.find(query)
  {
    "_id": ObjectId("5691578b046a0e39d3813d53"),
    "name": "Bulbasaur",
    "description": "Bulbasaur can be seen napping in bright sunlight.",
    "attack": 300,
    "defense": 200,
    "height": 0.7,
    "moves": [
      "investida",
      "desvio"
    ]
  }
  {
    "_id": ObjectId("569157af046a0e39d3813d56"),
    "name": "Caterpie",
    "description": "Caterpie has a voracious appetite. It can devour leaves bigger than its body right before your eyes. From its antenna, this Pokémon releases a terrifically strong odor.",
    "attack": 200,
    "defense": 200,
    "height": 0.3,
    "moves": [
      "investida",
      "desvio"
    ]
  }
  {
    "_id": ObjectId("569157c7046a0e39d3813d57"),
    "name": "Butterfree",
    "description": "Butterfree has a superior ability to search for delicious honey from flowers. It can even search out, extract, and carry honey from flowers that are blooming over six miles from its nest.",
    "attack": 200,
    "defense": 200,
    "height": 1.1,
    "moves": [
      "investida",
      "desvio"
    ]
  }
  Fetched 3 record(s) in 3ms

  ```
##Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito

  ```
  localhost(mongod-3.2.0) be-mean-pokemons> var query = {moves: {$all: ['investida', 'desvio']}}
  localhost(mongod-3.2.0) be-mean-pokemons> db.pokemons.find(query)
  {
    "_id": ObjectId("5691578b046a0e39d3813d53"),
    "name": "Bulbasaur",
    "description": "Bulbasaur can be seen napping in bright sunlight.",
    "attack": 300,
    "defense": 200,
    "height": 0.7,
    "moves": [
      "investida",
      "desvio"
    ],
    "type": null
  }
  {
    "_id": ObjectId("569157af046a0e39d3813d56"),
    "name": "Caterpie",
    "description": "Caterpie has a voracious appetite. It can devour leaves bigger than its body right before your eyes. From its antenna, this Pokémon releases a terrifically strong odor.",
    "attack": 200,
    "defense": 200,
    "height": 0.3,
    "moves": [
      "investida",
      "desvio"
    ],
    "type": null
  }
  {
    "_id": ObjectId("569157c7046a0e39d3813d57"),
    "name": "Butterfree",
    "description": "Butterfree has a superior ability to search for delicious honey from flowers. It can even search out, extract, and carry honey from flowers that are blooming over six miles from its nest.",
    "attack": 200,
    "defense": 200,
    "height": 1.1,
    "moves": [
      "investida",
      "desvio"
    ],
    "type": null
  }
  Fetched 3 record(s) in 3ms

  ```

##Pesquisar todos os pokemons que não são do tipo 'eletric'

  ```
  localhost(mongod-3.2.0) be-mean-pokemons> var query = {type: {$not: /eletrico/i}}
  localhost(mongod-3.2.0) be-mean-pokemons> db.pokemons.find(query)
  {
    "_id": ObjectId("5691578b046a0e39d3813d53"),
    "name": "Bulbasaur",
    "description": "Bulbasaur can be seen napping in bright sunlight.",
    "attack": 300,
    "defense": 200,
    "height": 0.7,
    "moves": [
      "investida",
      "desvio"
    ],
    "type": null
  }
  {
    "_id": ObjectId("56915799046a0e39d3813d54"),
    "name": "Charmander",
    "description": "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokémon becomes enraged, the flame burns fiercely.",
    "attack": 300,
    "defense": 200,
    "height": 0.6,
    "moves": [
      "fugir",
      "atacar",
      "desvio"
    ],
    "type": null
  }
  {
    "_id": ObjectId("569157a4046a0e39d3813d55"),
    "name": "Squirtle",
    "description": "Squirtle's shell is not merely used for protection. The shell's rounded shape and the grooves on its surface help minimize resistance in water, enabling this Pokémon to swim at high speeds.",
    "attack": 300,
    "defense": 300,
    "height": 0.5,
    "moves": [
      "fugir",
      "atacar",
      "desvio"
    ],
    "type": null
  }
  {
    "_id": ObjectId("569157af046a0e39d3813d56"),
    "name": "Caterpie",
    "description": "Caterpie has a voracious appetite. It can devour leaves bigger than its body right before your eyes. From its antenna, this Pokémon releases a terrifically strong odor.",
    "attack": 200,
    "defense": 200,
    "height": 0.3,
    "moves": [
      "investida",
      "desvio"
    ],
    "type": null
  }
  {
    "_id": ObjectId("569157c7046a0e39d3813d57"),
    "name": "Butterfree",
    "description": "Butterfree has a superior ability to search for delicious honey from flowers. It can even search out, extract, and carry honey from flowers that are blooming over six miles from its nest.",
    "attack": 200,
    "defense": 200,
    "height": 1.1,
    "moves": [
      "investida",
      "desvio"
    ],
    "type": null
  }
  {
    "_id": ObjectId("56942d11b9ce80f9f4e07cbb"),
    "name": "Bulbassauro",
    "description": "coisa doente",
    "attack": 300,
    "defense": 300,
    "height": 0.5,
    "moves": [
      "fugir",
      "atacar",
      "desvio"
    ],
    "type": null
  }
  {
    "_id": ObjectId("5694316e56ac88807cd6b35c"),
    "name": "AindaNaoExisteMon",
    "description": "Sem maiores informações",
    "type": null,
    "attack": null,
    "defense": null,
    "height": null,
    "active": null
  }
  Fetched 7 record(s) in 8ms

  ```

##Pesquisar todos os pokemons que tenham o ataque 'investida' **E** a defesa não menor ou igual que 49.

  ```
  localhost(mongod-3.2.0) be-mean-pokemons> var query = {$and: [{attack: {$gt: 49}}, {moves: {$in: ['investida']}}]}
  localhost(mongod-3.2.0) be-mean-pokemons> db.pokemons.find(query)
  {
    "_id": ObjectId("5691578b046a0e39d3813d53"),
    "name": "Bulbasaur",
    "description": "Bulbasaur can be seen napping in bright sunlight.",
    "attack": 300,
    "defense": 200,
    "height": 0.7,
    "moves": [
      "investida",
      "desvio"
    ],
    "type": null
  }
  {
    "_id": ObjectId("569157af046a0e39d3813d56"),
    "name": "Caterpie",
    "description": "Caterpie has a voracious appetite. It can devour leaves bigger than its body right before your eyes. From its antenna, this Pokémon releases a terrifically strong odor.",
    "attack": 200,
    "defense": 200,
    "height": 0.3,
    "moves": [
      "investida",
      "desvio"
    ],
    "type": null
  }
  {
    "_id": ObjectId("569157c7046a0e39d3813d57"),
    "name": "Butterfree",
    "description": "Butterfree has a superior ability to search for delicious honey from flowers. It can even search out, extract, and carry honey from flowers that are blooming over six miles from its nest.",
    "attack": 200,
    "defense": 200,
    "height": 1.1,
    "moves": [
      "investida",
      "desvio"
    ],
    "type": null
  }
  Fetched 3 record(s) in 1ms


  ```

 ##Remova todos os pokemons do tipo 'água' e com ataque menor que 50.

  ```
  localhost(mongod-3.2.0) be-mean-pokemons> var query = {$and: [{ attack: {$lt: 50}}, {type: /agua/i}]}
  localhost(mongod-3.2.0) be-mean-pokemons> db.pokemons.remove(query)
  Removed 1 record(s) in 2ms
  WriteResult({
    "nRemoved": 1
  })

  ```

## Demonstre qual a diferença entre os operadores $ne e $not