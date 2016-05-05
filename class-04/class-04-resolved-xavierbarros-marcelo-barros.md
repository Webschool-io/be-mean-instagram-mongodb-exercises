# MongoDB - Aula 04 - Exercício

autor: Marcelo Barros

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
maba(mongod-3.0.7) be-mean-pokemons> var query = {name: "Pikachu"}
maba(mongod-3.0.7) be-mean-pokemons> var mod = {$pushAll: {moves: ['static', 'lightning rod']}}

maba(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod)

Updated 1 existing record(s) in 2ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})


maba(mongod-3.0.7) be-mean-pokemons> var query = {name: "Squirtle"}

maba(mongod-3.0.7) be-mean-pokemons> var mod = {$pushAll: {moves: ['torrent', 'rain dash']}}

maba(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 2ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})


maba(mongod-3.0.7) be-mean-pokemons> var query = {name: "Bulbasaur"}

maba(mongod-3.0.7) be-mean-pokemons> var mod = {$pushAll: {moves: ['chlorophyll']}}

maba(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 1ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})


maba(mongod-3.0.7) be-mean-pokemons> var query = {name: "Charmander"}

maba(mongod-3.0.7) be-mean-pokemons> var mod = {$pushAll: {moves: ['blaze', 'solar power']}}

maba(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 1ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})



## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##
maba(mongod-3.0.7) be-mean-pokemons> var query = {}

maba(mongod-3.0.7) be-mean-pokemons> var mod = { $push: { moves: 'desvio' } }

maba(mongod-3.0.7) be-mean-pokemons> var options = { multi: true }

maba(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 20 existing record(s) in 1ms
WriteResult({
  "nMatched": 20,
  "nUpserted": 0,
  "nModified": 20
})



## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##

maba(mongod-3.0.7) be-mean-pokemons> var query = { name: 'AindaNaoExisteMon' }

maba(mongod-3.0.7) be-mean-pokemons> var mod = { $setOnInsert: { name: 'AindaNaoExisteMon', type: null, attack: null, defense: null, height: null, description: 'Sem maiores informações' } }

maba(mongod-3.0.7) be-mean-pokemons> var options = { upsert: true }

maba(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 1ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("56535d75265a0972139880c2")
})



## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
maba(mongod-3.0.7) be-mean-pokemons> var query = { moves: { $in: ['investida', 'inner focus'] } }

maba(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)

{
  "_id": ObjectId("56491fe1d6663c31c553381c"),
  "name": "Venonat",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Inseto",
  "attack": 55,
  "defense": 50,
  "height": 0.99,
  "active": false,
  "moves": [
    "investida",
    "compound eyes",
    "desvio"
  ],
  "type": "inseto"
}

{
  "_id": ObjectId("56491fabd6663c31c553381b"),
  "name": "Paras",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Cogumelo",
  "attack": 70,
  "defense": 55,
  "height": 0.3,
  "active": false,
  "moves": [
    "investida",
    "effect spore",
    "desvio"
  ],
  "type": "inseto"
}

{
  "_id": ObjectId("56491f6bd6663c31c553381a"),
  "name": "Oddish",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Erva-Daninha",
  "attack": 50,
  "defense": 55,
  "height": 0.51,
  "active": false,
  "moves": [
    "investida",
    "chlorophyll",
    "desvio"
  ],
  "type": "grama"
}

{
  "_id": ObjectId("56491f1cd6663c31c5533819"),
  "name": "Zubat",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Morcego",
  "attack": 45,
  "defense": 35,
  "height": 0.79,
  "active": false,
  "moves": [
    "investida",
    "inner focus",
    "desvio"
  ],
  "type": "voador"
}

{
  "_id": ObjectId("56491ec2d6663c31c5533818"),
  "name": "Jigglypuff",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Balão",
  "attack": 45,
  "defense": 20,
  "height": 0.51,
  "active": false,
  "moves": [
    "investida",
    "cute charm",
    "desvio"
  ],
  "type": "normal"
}

{
  "_id": ObjectId("56491e0ad6663c31c5533815"),
  "name": "Nidoran",
  "description": "Introduzido na Geração 1, é conhecido como Pokemón Venenoso",
  "attack": 47,
  "defense": 52,
  "height": 0.41,
  "active": false,
  "moves": [
    "investida",
    "poison point",
    "desvio"
  ],
  "type": "veneno"
}

{
  "_id": ObjectId("56491cadd6663c31c5533811"),
  "name": "Spearow",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Passarinho",
  "attack": 60,
  "defense": 30,
  "height": 0.3,
  "active": false,
  "moves": [
    "investida",
    "keen eye",
    "desvio"
  ],
  "type": "voador"
}

{
  "_id": ObjectId("56491c19d6663c31c553380f"),
  "name": "Pidgey",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Passarinho",
  "attack": 45,
  "defense": 40,
  "height": 0.3,
  "active": false,
  "moves": [
    "investida",
    "keen eye",
    "desvio"
  ],
  "type": "voador"
}

{
  "_id": ObjectId("56491b8bd6663c31c553380e"),
  "name": "Weedle",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Inseto Peludo",
  "attack": 35,
  "defense": 30,
  "height": 0.3,
  "active": false,
  "moves": [
    "investida",
    "shield dust",
    "desvio"
  ],
  "type": "inseto"
}

{
  "_id": ObjectId("56491afdd6663c31c553380d"),
  "name": "Caterpie",
  "description": "Introduzido na Geração 1, é conhecido como Verme Pokémon",
  "attack": 30,
  "defense": 35,
  "height": 0.3,
  "active": false,
  "moves": [
    "investida",
    "shield dust",
    "desvio"
  ],
  "type": "inseto"
}

{
  "_id": ObjectId("56491aa0d6663c31c553380c"),
  "name": "Squirtle",
  "description": "Introduzido na Geração 1, é conhecido como Pequena Tartaruga Pokémon",
  "attack": 48,
  "defense": 65,
  "height": 0.51,
  "active": false,
  "moves": [
    "investida",
    "torrent",
    "torrent",
    "rain dash",
    "desvio"
  ],
  "type": "agua"
}

{
  "_id": ObjectId("56534747265a0972139880c1"),
  "name": "Bulbasaur",
  "type": "grama",
  "description": "Introduzido na Geração 1, é conhecido como Pokemón Semente",
  "attack": 49,
  "defense": 49,
  "height": 0.7,
  "active": false,
  "moves": [
    "investida",
    "overgrow",
    "Chlorophyll",
    "desvio"
  ]
}

{
  "_id": ObjectId("56491d6ad6663c31c5533813"),
  "name": "Pikachu",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Rato",
  "attack": 55,
  "defense": 40,
  "height": 0.41,
  "active": false,
  "moves": [
    "investida",
    "static",
    "static",
    "lightning rod",
    "desvio"
  ],
  "type": "elétrico"
}

{
  "_id": ObjectId("56491a36d6663c31c553380b"),
  "name": "Charmander",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Lagarto",
  "attack": 52,
  "defense": 43,
  "height": 0.61,
  "active": false,
  "moves": [
    "investida",
    "blaze",
    "blaze",
    "solar power",
    "desvio"
  ],
  "type": "fogo"
}

{
  "_id": ObjectId("56491c70d6663c31c5533810"),
  "name": "Rattata",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Rato",
  "attack": 56,
  "defense": 35,
  "height": 0.3,
  "active": false,
  "moves": [
    "investida",
    "run away",
    "desvio"
  ],
  "type": "normal"
}

{
  "_id": ObjectId("56491d2dd6663c31c5533812"),
  "name": "Ekans",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Cobra",
  "attack": 60,
  "defense": 44,
  "height": 2.01,
  "active": false,
  "moves": [
    "investida",
    "shed skin",
    "desvio"
  ],
  "type": "veneno"
}

{
  "_id": ObjectId("56491d9fd6663c31c5533814"),
  "name": "Sandshrew",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Rato",
  "attack": 75,
  "defense": 85,
  "height": 0.61,
  "active": false,
  "moves": [
    "investida",
    "sand veil",
    "desvio"
  ],
  "type": "solo"
}

{
  "_id": ObjectId("56491e50d6663c31c5533816"),
  "name": "Clefairy",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Fada",
  "attack": 45,
  "defense": 48,
  "height": 0.61,
  "active": false,
  "moves": [
    "investida",
    "cute charm",
    "desvio"
  ],
  "type": "fada"
}

{
  "_id": ObjectId("56491e7fd6663c31c5533817"),
  "name": "Vulpix",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Raposa",
  "attack": 41,
  "defense": 40,
  "height": 0.61,
  "active": false,
  "moves": [
    "investida",
    "flash fire",
    "desvio"
  ],
  "type": "fogo"
}

Fetched 19 record(s) in 6ms



## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##
maba(mongod-3.0.7) be-mean-pokemons> var query = { moves: { $all: ['investida', 'inner focus'] } }

maba(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)

{
  "_id": ObjectId("56491f1cd6663c31c5533819"),
  "name": "Zubat",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Morcego",
  "attack": 45,
  "defense": 35,
  "height": 0.79,
  "active": false,
  "moves": [
    "investida",
    "inner focus",
    "desvio"
  ],
  "type": "voador"
}

Fetched 1 record(s) in 1ms



## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##
maba(mongod-3.0.7) be-mean-pokemons> var query = { type: { $not: /elétrico/i } }

maba(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)

{
  "_id": ObjectId("564a66f9d6663c31c553381d"),
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "height": 2.1,
  "description": "Pokemon de teste",
  "moves": [
    "desvio"
  ]
}

{
  "_id": ObjectId("56491fe1d6663c31c553381c"),
  "name": "Venonat",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Inseto",
  "attack": 55,
  "defense": 50,
  "height": 0.99,
  "active": false,
  "moves": [
    "investida",
    "compound eyes",
    "desvio"
  ],
  "type": "inseto"
}

{
  "_id": ObjectId("56491fabd6663c31c553381b"),
  "name": "Paras",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Cogumelo",
  "attack": 70,
  "defense": 55,
  "height": 0.3,
  "active": false,
  "moves": [
    "investida",
    "effect spore",
    "desvio"
  ],
  "type": "inseto"
}

{
  "_id": ObjectId("56491f6bd6663c31c553381a"),
  "name": "Oddish",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Erva-Daninha",
  "attack": 50,
  "defense": 55,
  "height": 0.51,
  "active": false,
  "moves": [
    "investida",
    "chlorophyll",
    "desvio"
  ],
  "type": "grama"
}

{
  "_id": ObjectId("56535d75265a0972139880c2"),
  "name": "AindaNaoExisteMon",
  "type": null,
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações"
}

{
  "_id": ObjectId("56491f1cd6663c31c5533819"),
  "name": "Zubat",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Morcego",
  "attack": 45,
  "defense": 35,
  "height": 0.79,
  "active": false,
  "moves": [
    "investida",
    "inner focus",
    "desvio"
  ],
  "type": "voador"
}

{
  "_id": ObjectId("56491ec2d6663c31c5533818"),
  "name": "Jigglypuff",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Balão",
  "attack": 45,
  "defense": 20,
  "height": 0.51,
  "active": false,
  "moves": [
    "investida",
    "cute charm",
    "desvio"
  ],
  "type": "normal"
}

{
  "_id": ObjectId("56491e0ad6663c31c5533815"),
  "name": "Nidoran",
  "description": "Introduzido na Geração 1, é conhecido como Pokemón Venenoso",
  "attack": 47,
  "defense": 52,
  "height": 0.41,
  "active": false,
  "moves": [
    "investida",
    "poison point",
    "desvio"
  ],
  "type": "veneno"
}

{
  "_id": ObjectId("56491cadd6663c31c5533811"),
  "name": "Spearow",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Passarinho",
  "attack": 60,
  "defense": 30,
  "height": 0.3,
  "active": false,
  "moves": [
    "investida",
    "keen eye",
    "desvio"
  ],
  "type": "voador"
}

{
  "_id": ObjectId("56491c19d6663c31c553380f"),
  "name": "Pidgey",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Passarinho",
  "attack": 45,
  "defense": 40,
  "height": 0.3,
  "active": false,
  "moves": [
    "investida",
    "keen eye",
    "desvio"
  ],
  "type": "voador"
}

{
  "_id": ObjectId("56491b8bd6663c31c553380e"),
  "name": "Weedle",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Inseto Peludo",
  "attack": 35,
  "defense": 30,
  "height": 0.3,
  "active": false,
  "moves": [
    "investida",
    "shield dust",
    "desvio"
  ],
  "type": "inseto"
}

{
  "_id": ObjectId("56491afdd6663c31c553380d"),
  "name": "Caterpie",
  "description": "Introduzido na Geração 1, é conhecido como Verme Pokémon",
  "attack": 30,
  "defense": 35,
  "height": 0.3,
  "active": false,
  "moves": [
    "investida",
    "shield dust",
    "desvio"
  ],
  "type": "inseto"
}

{
  "_id": ObjectId("56491aa0d6663c31c553380c"),
  "name": "Squirtle",
  "description": "Introduzido na Geração 1, é conhecido como Pequena Tartaruga Pokémon",
  "attack": 48,
  "defense": 65,
  "height": 0.51,
  "active": false,
  "moves": [
    "investida",
    "torrent",
    "torrent",
    "rain dash",
    "desvio"
  ],
  "type": "agua"
}

{
  "_id": ObjectId("56534747265a0972139880c1"),
  "name": "Bulbasaur",
  "type": "grama",
  "description": "Introduzido na Geração 1, é conhecido como Pokemón Semente",
  "attack": 49,
  "defense": 49,
  "height": 0.7,
  "active": false,
  "moves": [
    "investida",
    "overgrow",
    "Chlorophyll",
    "desvio"
  ]
}

{
  "_id": ObjectId("56491a36d6663c31c553380b"),
  "name": "Charmander",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Lagarto",
  "attack": 52,
  "defense": 43,
  "height": 0.61,
  "active": false,
  "moves": [
    "investida",
    "blaze",
    "blaze",
    "solar power",
    "desvio"
  ],
  "type": "fogo"
}

{
  "_id": ObjectId("56491c70d6663c31c5533810"),
  "name": "Rattata",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Rato",
  "attack": 56,
  "defense": 35,
  "height": 0.3,
  "active": false,
  "moves": [
    "investida",
    "run away",
    "desvio"
  ],
  "type": "normal"
}

{
  "_id": ObjectId("56491d2dd6663c31c5533812"),
  "name": "Ekans",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Cobra",
  "attack": 60,
  "defense": 44,
  "height": 2.01,
  "active": false,
  "moves": [
    "investida",
    "shed skin",
    "desvio"
  ],
  "type": "veneno"
}

{
  "_id": ObjectId("56491d9fd6663c31c5533814"),
  "name": "Sandshrew",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Rato",
  "attack": 75,
  "defense": 85,
  "height": 0.61,
  "active": false,
  "moves": [
    "investida",
    "sand veil",
    "desvio"
  ],
  "type": "solo"
}

{
  "_id": ObjectId("56491e50d6663c31c5533816"),
  "name": "Clefairy",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Fada",
  "attack": 45,
  "defense": 48,
  "height": 0.61,
  "active": false,
  "moves": [
    "investida",
    "cute charm",
    "desvio"
  ],
  "type": "fada"
}

{
  "_id": ObjectId("56491e7fd6663c31c5533817"),
  "name": "Vulpix",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Raposa",
  "attack": 41,
  "defense": 40,
  "height": 0.61,
  "active": false,
  "moves": [
    "investida",
    "flash fire",
    "desvio"
  ],
  "type": "fogo"
}

Fetched 20 record(s) in 5ms



## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##
maba(mongod-3.0.7) be-mean-pokemons> var query = { $and: [ { moves: { $in: [ 'investida' ] } }, { attack: { $not: { $lte: 49 } } } ] }

maba(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)

{
  "_id": ObjectId("56491fe1d6663c31c553381c"),
  "name": "Venonat",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Inseto",
  "attack": 55,
  "defense": 50,
  "height": 0.99,
  "active": false,
  "moves": [
    "investida",
    "compound eyes",
    "desvio"
  ],
  "type": "inseto"
}

{
  "_id": ObjectId("56491fabd6663c31c553381b"),
  "name": "Paras",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Cogumelo",
  "attack": 70,
  "defense": 55,
  "height": 0.3,
  "active": false,
  "moves": [
    "investida",
    "effect spore",
    "desvio"
  ],
  "type": "inseto"
}

{
  "_id": ObjectId("56491f6bd6663c31c553381a"),
  "name": "Oddish",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Erva-Daninha",
  "attack": 50,
  "defense": 55,
  "height": 0.51,
  "active": false,
  "moves": [
    "investida",
    "chlorophyll",
    "desvio"
  ],
  "type": "grama"
}

{
  "_id": ObjectId("56491cadd6663c31c5533811"),
  "name": "Spearow",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Passarinho",
  "attack": 60,
  "defense": 30,
  "height": 0.3,
  "active": false,
  "moves": [
    "investida",
    "keen eye",
    "desvio"
  ],
  "type": "voador"
}

{
  "_id": ObjectId("56491d6ad6663c31c5533813"),
  "name": "Pikachu",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Rato",
  "attack": 55,
  "defense": 40,
  "height": 0.41,
  "active": false,
  "moves": [
    "investida",
    "static",
    "static",
    "lightning rod",
    "desvio"
  ],
  "type": "elétrico"
}

{
  "_id": ObjectId("56491a36d6663c31c553380b"),
  "name": "Charmander",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Lagarto",
  "attack": 52,
  "defense": 43,
  "height": 0.61,
  "active": false,
  "moves": [
    "investida",
    "blaze",
    "blaze",
    "solar power",
    "desvio"
  ],
  "type": "fogo"
}

{
  "_id": ObjectId("56491c70d6663c31c5533810"),
  "name": "Rattata",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Rato",
  "attack": 56,
  "defense": 35,
  "height": 0.3,
  "active": false,
  "moves": [
    "investida",
    "run away",
    "desvio"
  ],
  "type": "normal"
}

{
  "_id": ObjectId("56491d2dd6663c31c5533812"),
  "name": "Ekans",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Cobra",
  "attack": 60,
  "defense": 44,
  "height": 2.01,
  "active": false,
  "moves": [
    "investida",
    "shed skin",
    "desvio"
  ],
  "type": "veneno"
}

{
  "_id": ObjectId("56491d9fd6663c31c5533814"),
  "name": "Sandshrew",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Rato",
  "attack": 75,
  "defense": 85,
  "height": 0.61,
  "active": false,
  "moves": [
    "investida",
    "sand veil",
    "desvio"
  ],
  "type": "solo"
}

Fetched 9 record(s) in 4ms



## Remova **todos** os pokemons do tipo água e com attack menor que 50.
maba(mongod-3.0.7) be-mean-pokemons> var query = { $and: [ { type: 'água' }, { attack: { $lt: 50 } } ] }

maba(mongod-3.0.7) be-mean-pokemons> db.pokemons.remove(query)
Removed 0 record(s) in 1ms
WriteResult({
  "nRemoved": 0
})