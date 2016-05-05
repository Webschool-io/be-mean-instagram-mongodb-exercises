# Exercício 4
# Autor: Guilherme Pendezza de Sousa

# 1 - Adicionar dois ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbasaur e Charmander

var query = {name: {$in: [/pikachu/i, /bulbasaur/i, /squirtle/i, /charmander/i]}}

var mod = {
  $pushAll: {
    moves: [
      'Roundhouse Kick',
      'Kame Hame Há'
      ]
  }
}

db.pokemons.update(query, mod, {multi: true})

db.pokemons.find(query)
{
  "_id": ObjectId("56682f08eef0021d7220de4a"),
  "name": "Pikachu",
  "description": "Um rato elétrico",
  "type": "eletric",
  "attack": 30,
  "height": 0.4,
  "moves": [
    "Roundhouse Kick",
    "Kame Hame Há"
  ]
}
{
  "_id": ObjectId("56682f08eef0021d7220de4b"),
  "name": "Bulbasaur",
  "description": "Sapo zika do pântano",
  "type": "grama",
  "attack": 30,
  "height": 0.7,
  "moves": [
    "Roundhouse Kick",
    "Kame Hame Há"
  ]
}
{
  "_id": ObjectId("56682f08eef0021d7220de4c"),
  "name": "Squirtle",
  "description": "Tartaruga bombeira",
  "type": "agua",
  "attack": 30,
  "height": 0.5,
  "moves": [
    "Roundhouse Kick",
    "Kame Hame Há"
  ]
}
{
  "_id": ObjectId("56682f08eef0021d7220de4d"),
  "name": "Charmander",
  "description": "Boto fogo memo",
  "type": "fogo",
  "attack": 30,
  "height": 0.6,
  "moves": [
    "Roundhouse Kick",
    "Kame Hame Há"
  ]
}
Fetched 4 record(s) in 2ms
guilherme-notebook(mongod-3.0.7) be-mean-pokemons>


# 2 - Adicionar 1 movimento em todos os pokemons: 'desvio'

var mod = { $push: { moves: 'desvio' } }

db.pokemons.update({}, mod, {multi: true})

guilherme-notebook(mongod-3.0.7) be-mean-pokemons> db.pokemons.find({})

{
  "_id": ObjectId("5666ebdeb4f0168b575fe0af"),
  "name": "Pidgeotto",
  "description": "Um quero-quero dos pokemons",
  "type": "voador",
  "attack": 30,
  "height": 1.1,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5666ebdeb4f0168b575fe0b0"),
  "name": "Arbok",
  "description": "Cobra burra da equipe Rocket",
  "type": "venenoso",
  "attack": 40,
  "height": 3.5,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5666ebdeb4f0168b575fe0b1"),
  "name": "Jigglypuff",
  "description": "Pokemon que cau... zzzzzzzzzzz...",
  "type": "fada",
  "attack": 20,
  "height": 0.5,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5666ebdeb4f0168b575fe0b2"),
  "name": "Arcanine",
  "description": "Cachorro fofinho =)",
  "type": "fogo",
  "attack": 60,
  "height": 1.9,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5666ebdeb4f0168b575fe0b3"),
  "name": "Psyduck",
  "description": "Só tem dor de cabeça",
  "type": "água",
  "attack": 30,
  "height": 0.8,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56682f08eef0021d7220de4a"),
  "name": "Pikachu",
  "description": "Um rato elétrico",
  "type": "eletric",
  "attack": 30,
  "height": 0.4,
  "moves": [
    "Roundhouse Kick",
    "Kame Hame Há",
    "desvio"
  ]
}
{
  "_id": ObjectId("56682f08eef0021d7220de4b"),
  "name": "Bulbasaur",
  "description": "Sapo zika do pântano",
  "type": "grama",
  "attack": 30,
  "height": 0.7,
  "moves": [
    "Roundhouse Kick",
    "Kame Hame Há",
    "desvio"
  ]
}
{
  "_id": ObjectId("56682f08eef0021d7220de4c"),
  "name": "Squirtle",
  "description": "Tartaruga bombeira",
  "type": "agua",
  "attack": 30,
  "height": 0.5,
  "moves": [
    "Roundhouse Kick",
    "Kame Hame Há",
    "desvio"
  ]
}
{
  "_id": ObjectId("56682f08eef0021d7220de4d"),
  "name": "Charmander",
  "description": "Boto fogo memo",
  "type": "fogo",
  "attack": 30,
  "height": 0.6,
  "moves": [
    "Roundhouse Kick",
    "Kame Hame Há",
    "desvio"
  ]
}
Fetched 9 record(s) in 3ms
guilherme-notebook(mongod-3.0.7) be-mean-pokemons>


# 3 - Adicionar o pokemons 'AindaNaoExisteMon' caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações".

var query = { name: /AindaNaoExisteMon/i };
var mod = {
  $setOnInsert: {
      name: "AindaNaoExisteMon",
      description: null,
      type: null,
      attack: null,
      height: null
  }
};

db.pokemons.update(query, mod, { upsert: true })

guilherme-notebook(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, {upsert: true})
Updated 1 new record(s) in 2ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("566847a40fc3549c47c196b3")
})
guilherme-notebook(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("566847a40fc3549c47c196b3"),
  "name": "AindaNaoExisteMon",
  "description": null,
  "type": null,
  "attack": null,
  "height": null
}
Fetched 1 record(s) in 1ms
guilherme-notebook(mongod-3.0.7) be-mean-pokemons>


# 4 - Pesquisar todos os pokemons que possuam o ataque investida e mais um que vc adicionou, escolha seu Pokemon favorito.

guilherme-notebook(mongod-3.0.7) be-mean-pokemons> var query = {
...   moves: {
...     $in : [/investida/i, /programar/i]
...   }
... }
guilherme-notebook(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56682f08eef0021d7220de4a"),
  "name": "Pikachu",
  "description": "Um rato elétrico",
  "type": "eletric",
  "attack": 30,
  "height": 0.4,
  "moves": [
    "Roundhouse Kick",
    "Kame Hame Há",
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("5668495a0fc3549c47c196b4"),
  "name": "GuilhermeMon",
  "description": "Programador JS",
  "type": "nerd",
  "attack": 80,
  "height": 1.83,
  "moves": [
    "programar"
  ]
}
Fetched 2 record(s) in 3ms
guilherme-notebook(mongod-3.0.7) be-mean-pokemons>


# 5 - Pesquisar todos os pokemons que possuam os ataques que vc adicionou, escolha seu pokemon favorito

var query = {
  moves: {
    $in: [/programar/i]
  }
}

guilherme-notebook(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5668495a0fc3549c47c196b4"),
  "name": "GuilhermeMon",
  "description": "Programador JS",
  "type": "nerd",
  "attack": 80,
  "height": 1.83,
  "moves": [
    "programar"
  ]
}

# 6 - Pesquisar todos que não são do tipo eletrico

var query = { type: 'eletric' };

db.pokemons.find(query);

{
  "_id": ObjectId("56682f08eef0021d7220de4a"),
  "name": "Pikachu",
  "description": "Um rato elétrico",
  "type": "eletric",
  "attack": 30,
  "height": 0.4,
  "moves": [
    "Roundhouse Kick",
    "Kame Hame Há",
    "desvio",
    "investida"
  ]
}
Fetched 1 record(s) in 3ms
guilherme-notebook(mongod-3.0.7) be-mean-pokemons>


# 7 - Pesquisar todos os pokemons que tenham o ataque investida e tenham a defesa nao menor ou igual a 49.

var query = {
  $and: [
    {
      moves: {
        $in: [/investida/i]
      }
    },
    {
      defense: {
        $not: {
          $lte: 49
        }
      }
    }
  ]
}

guilherme-notebook(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56682f08eef0021d7220de4a"),
  "name": "Pikachu",
  "description": "Um rato elétrico",
  "type": "eletric",
  "attack": 30,
  "height": 0.4,
  "moves": [
    "Roundhouse Kick",
    "Kame Hame Há",
    "desvio",
    "investida"
  ],
  "defense": 50
}
Fetched 1 record(s) in 1ms
guilherme-notebook(mongod-3.0.7) be-mean-pokemons>

# 8 - Remova todos os pokemons do tipo agua e com ataque menor que 50

var query = {
  $and: [
    {
        type: /agua/i
    },
    {
        attack: { $lt: 50 }
    }
  ]
}

guilherme-notebook(mongod-3.0.7) be-mean-pokemons> db.pokemons.remove(query)
Removed 1 record(s) in 16ms
WriteResult({
  "nRemoved": 1
})
guilherme-notebook(mongod-3.0.7) be-mean-pokemons>
