# MongoDB - Aula 04 - Exercício
autor: Diego Ferreira

##1. Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons, pikachu, squirtle, Bulbassauro e Charmander.

```
Air-de-Diego(mongod-3.0.7) be-mean-pokemons> var query = { $or: [{ name: /pikachu/i}, {name: /squirtle/i}, {name: /bulbasaur/i}, {name: /charmander/i }] }
Air-de-Diego(mongod-3.0.7) be-mean-pokemons> query
{
  "$or": [
    {
      "name": /pikachu/i
    },
    {
      "name": /squirtle/i
    },
    {
      "name": /bulbasaur/i
    },
    {
      "name": /charmander/i
    }
  ]
}

Air-de-Diego(mongod-3.0.7) be-mean-pokemons> var mod = {$set: {'moves': ['furacao 2000', 'bola de fogo']}}
Air-de-Diego(mongod-3.0.7) be-mean-pokemons> mod
{
  "$set": {
    "moves": [
      "furacao 2000",
      "bola de fogo"
    ]
  }
}

Air-de-Diego(mongod-3.0.7) be-mean-pokemons> var options = {multi: true}

Air-de-Diego(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 4 existing record(s) in 6ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})

Air-de-Diego(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5643bc001ab2c09858ea975d"),
  "name": "Pikachu",
  "description": "Pikachu usa eletricidade como forca. Amigo fiel do Ash",
  "attack": 55,
  "defense": 40,
  "height": 0.4,
  "moves": [
    "furacao 2000",
    "bola de fogo"
  ]
}
{
  "_id": ObjectId("564d1788a7190dd16904f211"),
  "name": "Squirtle",
  "description": "Squirtle's shell is not merely used for protection. The shell's rounded shape and the grooves on its surface help minimize resistance in water, enabling this Pokémon to swim at high speeds.",
  "type": "water",
  "attack": 48,
  "defense": 65,
  "height": 0.5,
  "moves": [
    "furacao 2000",
    "bola de fogo"
  ]
}
{
  "_id": ObjectId("564d17d5a7190dd16904f212"),
  "name": "Charmander",
  "description": "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokémon becomes enraged, the flame burns fiercely.",
  "type": "fire",
  "attack": 52,
  "defense": 43,
  "height": 0.6,
  "moves": [
    "furacao 2000",
    "bola de fogo"
  ]
}
{
  "_id": ObjectId("564d17efa7190dd16904f213"),
  "name": "Bulbasaur",
  "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
  "type": "grass",
  "attack": 49,
  "defense": 49,
  "height": 0.7,
  "moves": [
    "furacao 2000",
    "bola de fogo"
  ]
}
Fetched 4 record(s) in 27ms
```

##2. Adicionar 1 movimento em todos os pokemons: 'desvio'.

```
Air-de-Diego(mongod-3.0.7) be-mean-pokemons> var query = {}
Air-de-Diego(mongod-3.0.7) be-mean-pokemons> var mod = { $push: {moves:"desvio"}}
Air-de-Diego(mongod-3.0.7) be-mean-pokemons> var options = {multi: true}
Air-de-Diego(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query,mod,options)
Updated 9 existing record(s) in 10ms
WriteResult({
  "nMatched": 9,
  "nUpserted": 0,
  "nModified": 9
})
```

##3. Adicionar o pokemon 'AindaNaoExisteMon' caso ele nao exista com todos os dados com o valor 'null' e a descricao: 'Sem maiores informacoes'.
```
Air-de-Diego(mongod-3.0.7) be-mean-pokemons> var query = {name: /AindaNaoExisteMon/i}
Air-de-Diego(mongod-3.0.7) be-mean-pokemons> var mod = {
  $set: { active: true },
  $setOnInsert: {
    name: "AindaNaoExisteMon",
    attack: null,
    defense: null,
    height: null,
    moves: [],
    description: 'sem maiores informações'
  }
}
Air-de-Diego(mongod-3.0.7) be-mean-pokemons> var options = {upsert: true}
Air-de-Diego(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 8ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("564d1ff457ad618a8e0afb53")

{
  "_id": ObjectId("564d1ff457ad618a8e0afb53"),
  "active": true,
  "name": "AindaNaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "moves": [ ],
  "description": "sem maiores informações"
}

```

##4. Pesquisar todos os pokemons que possuam o ataque 'investida' e mais um que voce adicionou, escolha seu pokemon favorito.
```
Air-de-Diego(mongod-3.0.7) be-mean-pokemons> var query = {'moves': { $all: ['investida', 'desvio'] }}
Air-de-Diego(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5643bc5e1ab2c09858ea975e"),
  "name": "Gurdurr",
  "description": "With strengthened bodies, they skillfully wield steel beams to take down buildings. ",
  "attack": 105,
  "defense": 85,
  "height": 12,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5643bce81ab2c09858ea975f"),
  "name": "Charizard",
  "description": "Charizard flies around the sky in search of powerful opponents.",
  "attack": 84,
  "defense": 78,
  "height": 17,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("564a6cd083ff67e1fa450081"),
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "height": 2.1,
  "description": "pokemon de teste",
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5643b9421ab2c09858ea975c"),
  "name": "Charmeleon",
  "description": "Charmeleon mercilessly destroys its foes using its sharp claws. If it encounters a strong foe, it turns agressive.",
  "attack": 64,
  "defense": 58,
  "height": 11,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5643bd581ab2c09858ea9760"),
  "name": "Sawk",
  "description": "Desiring the strongest karate chop, they seclude themselves in mountains and train without sleeping.",
  "attack": 125,
  "defense": 75,
  "height": 14,
  "moves": [
    "investida",
    "desvio"
  ]
}
Fetched 5 record(s) in 3ms
```

##5. Pesquisar todos os pokemons que possuam os ataques que voce adicionou, escolha seu pokemon favorito.

```
Air-de-Diego(mongod-3.0.7) be-mean-pokemons> var query = { moves: { $all: [ 'furacao 2000','bola de fogo' ] } }
Air-de-Diego(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564d1788a7190dd16904f211"),
  "name": "Squirtle",
  "description": "Squirtle's shell is not merely used for protection. The shell's rounded shape and the grooves on its surface help minimize resistance in water, enabling this Pokémon to swim at high speeds.",
  "type": "water",
  "attack": 48,
  "defense": 65,
  "height": 0.5,
  "moves": [
    "furacao 2000",
    "bola de fogo",
    "desvio"
  ]
}
{
  "_id": ObjectId("564d17d5a7190dd16904f212"),
  "name": "Charmander",
  "description": "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokémon becomes enraged, the flame burns fiercely.",
  "type": "fire",
  "attack": 52,
  "defense": 43,
  "height": 0.6,
  "moves": [
    "furacao 2000",
    "bola de fogo",
    "desvio"
  ]
}
{
  "_id": ObjectId("564d17efa7190dd16904f213"),
  "name": "Bulbasaur",
  "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
  "type": "grass",
  "attack": 49,
  "defense": 49,
  "height": 0.7,
  "moves": [
    "furacao 2000",
    "bola de fogo",
    "desvio"
  ]
}
Fetched 3 record(s) in 3ms
```


##6. Pesquisar todos os pokemons que nao sao do tipo 'eletrico'.

```
Air-de-Diego(mongod-3.0.7) be-mean-pokemons> var query = {type : "eletric"}
Air-de-Diego(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5643bc001ab2c09858ea975d"),
  "name": "Pikachu",
  "description": "Pikachu usa eletricidade como forca. Amigo fiel do Ash",
  "attack": 55,
  "defense": 40,
  "height": 0.4,
  "moves": [
    "desvio"
  ],
  "type": "eletric"
}
{
  "_id": ObjectId("5643bd581ab2c09858ea9760"),
  "name": "Sawk",
  "description": "Desiring the strongest karate chop, they seclude themselves in mountains and train without sleeping.",
  "attack": 125,
  "defense": 75,
  "height": 14,
  "moves": [
    "investida",
    "desvio"
  ],
  "type": "eletric"
}
Fetched 2 record(s) in 5ms
```

##7. Pesquisar todos os pokemons que tenha o ataque 'investida' E tenham a defesa nao menor ou igual a  49.

```
Air-de-Diego(mongod-3.0.7) be-mean-pokemons> var query = { $and: [ { moves: 'investida' }, { defense: { $gte: 49 } } ] }
Air-de-Diego(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5643bc5e1ab2c09858ea975e"),
  "name": "Gurdurr",
  "description": "With strengthened bodies, they skillfully wield steel beams to take down buildings. ",
  "attack": 105,
  "defense": 85,
  "height": 12,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5643bce81ab2c09858ea975f"),
  "name": "Charizard",
  "description": "Charizard flies around the sky in search of powerful opponents.",
  "attack": 84,
  "defense": 78,
  "height": 17,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("564a6cd083ff67e1fa450081"),
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "height": 2.1,
  "description": "pokemon de teste",
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5643b9421ab2c09858ea975c"),
  "name": "Charmeleon",
  "description": "Charmeleon mercilessly destroys its foes using its sharp claws. If it encounters a strong foe, it turns agressive.",
  "attack": 64,
  "defense": 58,
  "height": 11,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5643bd581ab2c09858ea9760"),
  "name": "Sawk",
  "description": "Desiring the strongest karate chop, they seclude themselves in mountains and train without sleeping.",
  "attack": 125,
  "defense": 75,
  "height": 14,
  "moves": [
    "investida",
    "desvio"
  ],
  "type": "eletric"
}
Fetched 5 record(s) in 4ms
```

##8. Remova todos os pokemons do tipo agua e com attack menor que 50.
```
Air-de-Diego(mongod-3.0.7) be-mean-pokemons> var query = { $and: [ { type: "water" }, { attack: { $lte: 50 } } ] }
Air-de-Diego(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564d1788a7190dd16904f211"),
  "name": "Squirtle",
  "description": "Squirtle's shell is not merely used for protection. The shell's rounded shape and the grooves on its surface help minimize resistance in water, enabling this Pokémon to swim at high speeds.",
  "type": "water",
  "attack": 48,
  "defense": 65,
  "height": 0.5,
  "moves": [
    "furacao 2000",
    "bola de fogo",
    "desvio"
  ]
}
Fetched 1 record(s) in 2ms

Air-de-Diego(mongod-3.0.7) be-mean-pokemons> db.pokemons.remove(query)
Removed 1 record(s) in 11ms
WriteResult({
  "nRemoved": 1
})

```
##9.9. Esse item não está no vídeo e se você fizer significa que você lê as coisas, nesse exercício demonstre qual a diferença entre os operadores `$ne` e `$not`.

$ne -> $ne é operador not equals. Este operador retorna o elemento se o valor não for igual ao valor passado.
Ex.: { type : { $ne : "fire"} } // retornara os pokemons que tiverem o campo diferente de fire.

Exemplo uso $ne:
```
ir-de-Diego(mongod-3.0.7) be-mean-pokemons> var query = { type : { $ne : "fire"} }
Air-de-Diego(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5643bc001ab2c09858ea975d"),
  "name": "Pikachu",
  "description": "Pikachu usa eletricidade como forca. Amigo fiel do Ash",
  "attack": 55,
  "defense": 40,
  "height": 0.4,
  "moves": [
    "desvio"
  ],
  "type": "eletric"
}
{
  "_id": ObjectId("5643bc5e1ab2c09858ea975e"),
  "name": "Gurdurr",
  "description": "With strengthened bodies, they skillfully wield steel beams to take down buildings. ",
  "attack": 105,
  "defense": 85,
  "height": 12,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5643bce81ab2c09858ea975f"),
  "name": "Charizard",
  "description": "Charizard flies around the sky in search of powerful opponents.",
  "attack": 84,
  "defense": 78,
  "height": 17,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("564a6cd083ff67e1fa450081"),
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "height": 2.1,
  "description": "pokemon de teste",
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5643b9421ab2c09858ea975c"),
  "name": "Charmeleon",
  "description": "Charmeleon mercilessly destroys its foes using its sharp claws. If it encounters a strong foe, it turns agressive.",
  "attack": 64,
  "defense": 58,
  "height": 11,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("564d17efa7190dd16904f213"),
  "name": "Bulbasaur",
  "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
  "type": "grass",
  "attack": 49,
  "defense": 49,
  "height": 0.7,
  "moves": [
    "furacao 2000",
    "bola de fogo",
    "desvio"
  ]
}
{
  "_id": ObjectId("5643bd581ab2c09858ea9760"),
  "name": "Sawk",
  "description": "Desiring the strongest karate chop, they seclude themselves in mountains and train without sleeping.",
  "attack": 125,
  "defense": 75,
  "height": 14,
  "moves": [
    "investida",
    "desvio"
  ],
  "type": "eletric"
}
{
  "_id": ObjectId("564d1ff457ad618a8e0afb53"),
  "active": true,
  "name": "AindaNaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "moves": [ ],
  "description": "sem maiores informações"
}
Fetched 8 record(s) in 8ms

```

Obs.: Diferente dos outros operadoes o operador $ne não aceira RegEx como valor do campo a ser pesquisado.
Ex.: { type : { $ne : /fire/i} } // retorna erro

```
Air-de-Diego(mongod-3.0.7) be-mean-pokemons> var query = { type : { $ne : /fire/i} }

Air-de-Diego(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
Error: error: {
  "$err": "Can't canonicalize query: BadValue Can't have regex as arg to $ne.",
  "code": 17287
}
```

$not -> O operador $not, por sua vez já aceira RegEx porém o mesmo trabalha retornado o objeto que não satisfaz a condição do campo.

```
Air-de-Diego(mongod-3.0.7) be-mean-pokemons> var query = {type: { $not : /fire/i } }
Air-de-Diego(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5643bc001ab2c09858ea975d"),
  "name": "Pikachu",
  "description": "Pikachu usa eletricidade como forca. Amigo fiel do Ash",
  "attack": 55,
  "defense": 40,
  "height": 0.4,
  "moves": [
    "desvio"
  ],
  "type": "eletric"
}
{
  "_id": ObjectId("5643bc5e1ab2c09858ea975e"),
  "name": "Gurdurr",
  "description": "With strengthened bodies, they skillfully wield steel beams to take down buildings. ",
  "attack": 105,
  "defense": 85,
  "height": 12,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5643bce81ab2c09858ea975f"),
  "name": "Charizard",
  "description": "Charizard flies around the sky in search of powerful opponents.",
  "attack": 84,
  "defense": 78,
  "height": 17,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("564a6cd083ff67e1fa450081"),
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "height": 2.1,
  "description": "pokemon de teste",
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5643b9421ab2c09858ea975c"),
  "name": "Charmeleon",
  "description": "Charmeleon mercilessly destroys its foes using its sharp claws. If it encounters a strong foe, it turns agressive.",
  "attack": 64,
  "defense": 58,
  "height": 11,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("564d17efa7190dd16904f213"),
  "name": "Bulbasaur",
  "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
  "type": "grass",
  "attack": 49,
  "defense": 49,
  "height": 0.7,
  "moves": [
    "furacao 2000",
    "bola de fogo",
    "desvio"
  ]
}
{
  "_id": ObjectId("5643bd581ab2c09858ea9760"),
  "name": "Sawk",
  "description": "Desiring the strongest karate chop, they seclude themselves in mountains and train without sleeping.",
  "attack": 125,
  "defense": 75,
  "height": 14,
  "moves": [
    "investida",
    "desvio"
  ],
  "type": "eletric"
}
{
  "_id": ObjectId("564d1ff457ad618a8e0afb53"),
  "active": true,
  "name": "AindaNaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "moves": [ ],
  "description": "sem maiores informações"
}
Fetched 8 record(s) in 4ms
```

Ou seja, basicamente a diferença entre eles esta no uso ou não de REGEX e o $ne retorna objetos que satisfaçam a condição e o $not objetos que não satisfaçam a condição.
