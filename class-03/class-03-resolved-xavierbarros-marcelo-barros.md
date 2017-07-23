# MongoDB - Aula 03 - Exercício

autor: Marcelo Barros

## Liste todos Pokemons com a altura menor que 0.5
maba(mongod-3.0.7) be-mean-pokemons> var query = {height: {$lt: 0.5}}

maba(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56491afdd6663c31c553380d"),
  "name": "Caterpie",
  "description": "Introduzido na Geração 1, é conhecido como Verme Pokémon",
  "attack": 30,
  "defense": 35,
  "height": 0.3
}

{
  "_id": ObjectId("56491b8bd6663c31c553380e"),
  "name": "Weedle",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Inseto Peludo",
  "attack": 35,
  "defense": 30,
  "height": 0.3
}

{
  "_id": ObjectId("56491c19d6663c31c553380f"),
  "name": "Pidgey",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Passarinho",
  "attack": 45,
  "defense": 40,
  "height": 0.3
}

{
  "_id": ObjectId("56491c70d6663c31c5533810"),
  "name": "Rattata",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Rato",
  "attack": 56,
  "defense": 35,
  "height": 0.3
}

{
  "_id": ObjectId("56491cadd6663c31c5533811"),
  "name": "Spearow",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Passarinho",
  "attack": 60,
  "defense": 30,
  "height": 0.3
}

{
  "_id": ObjectId("56491d6ad6663c31c5533813"),
  "name": "Pikachu",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Rato",
  "attack": 55,
  "defense": 40,
  "height": 0.41
}

{
  "_id": ObjectId("56491e0ad6663c31c5533815"),
  "name": "Nidoran",
  "description": "Introduzido na Geração 1, é conhecido como Pokemón Venenoso",
  "attack": 47,
  "defense": 52,
  "height": 0.41
}

{
  "_id": ObjectId("56491fabd6663c31c553381b"),
  "name": "Paras",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Cogumelo",
  "attack": 70,
  "defense": 55,
  "height": 0.3
}

Fetched 8 record(s) in 2ms


## Liste todos Pokemons com a altura maior ou igual que 0.5
maba(mongod-3.0.7) be-mean-pokemons> var query = {height: {$gte: 0.5}}

maba(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564919d5d6663c31c553380a"),
  "name": "Bulbasaur",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Semente",
  "attack": 49,
  "defense": 49,
  "height": 0.71
}

{
  "_id": ObjectId("56491a36d6663c31c553380b"),
  "name": "Charmander",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Lagarto",
  "attack": 52,
  "defense": 43,
  "height": 0.61
}

{
  "_id": ObjectId("56491aa0d6663c31c553380c"),
  "name": "Squirtle",
  "description": "Introduzido na Geração 1, é conhecido como Pequena Tartaruga Pokémon",
  "attack": 48,
  "defense": 65,
  "height": 0.51
}

{
  "_id": ObjectId("56491d2dd6663c31c5533812"),
  "name": "Ekans",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Cobra",
  "attack": 60,
  "defense": 44,
  "height": 2.01
}

{
  "_id": ObjectId("56491d9fd6663c31c5533814"),
  "name": "Sandshrew",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Rato",
  "attack": 75,
  "defense": 85,
  "height": 0.61
}

{
  "_id": ObjectId("56491e50d6663c31c5533816"),
  "name": "Clefairy",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Fada",
  "attack": 45,
  "defense": 48,
  "height": 0.61
}

{
  "_id": ObjectId("56491e7fd6663c31c5533817"),
  "name": "Vulpix",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Raposa",
  "attack": 41,
  "defense": 40,
  "height": 0.61
}

{
  "_id": ObjectId("56491ec2d6663c31c5533818"),
  "name": "Jigglypuff",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Balão",
  "attack": 45,
  "defense": 20,
  "height": 0.51
}

{
  "_id": ObjectId("56491f1cd6663c31c5533819"),
  "name": "Zubat",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Morcego",
  "attack": 45,
  "defense": 35,
  "height": 0.79
}

{
  "_id": ObjectId("56491f6bd6663c31c553381a"),
  "name": "Oddish",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Erva-Daninha",
  "attack": 50,
  "defense": 55,
  "height": 0.51
}

{
  "_id": ObjectId("56491fe1d6663c31c553381c"),
  "name": "Venonat",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Inseto",
  "attack": 55,
  "defense": 50,
  "height": 0.99
}

Fetched 11 record(s) in 3ms


## Liste todos Pokemons com a altura menor ou igual que 0.5
maba(mongod-3.0.7) be-mean-pokemons> var query = {height: {$lte: 0.5} }

maba(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56491afdd6663c31c553380d"),
  "name": "Caterpie",
  "description": "Introduzido na Geração 1, é conhecido como Verme Pokémon",
  "attack": 30,
  "defense": 35,
  "height": 0.3
}

{
  "_id": ObjectId("56491b8bd6663c31c553380e"),
  "name": "Weedle",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Inseto Peludo",
  "attack": 35,
  "defense": 30,
  "height": 0.3
}

{
  "_id": ObjectId("56491c19d6663c31c553380f"),
  "name": "Pidgey",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Passarinho",
  "attack": 45,
  "defense": 40,
  "height": 0.3
}

{
  "_id": ObjectId("56491c70d6663c31c5533810"),
  "name": "Rattata",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Rato",
  "attack": 56,
  "defense": 35,
  "height": 0.3
}

{
  "_id": ObjectId("56491cadd6663c31c5533811"),
  "name": "Spearow",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Passarinho",
  "attack": 60,
  "defense": 30,
  "height": 0.3
}

{
  "_id": ObjectId("56491d6ad6663c31c5533813"),
  "name": "Pikachu",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Rato",
  "attack": 55,
  "defense": 40,
  "height": 0.41
}

{
  "_id": ObjectId("56491e0ad6663c31c5533815"),
  "name": "Nidoran",
  "description": "Introduzido na Geração 1, é conhecido como Pokemón Venenoso",
  "attack": 47,
  "defense": 52,
  "height": 0.41
}

{
  "_id": ObjectId("56491fabd6663c31c553381b"),
  "name": "Paras",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Cogumelo",
  "attack": 70,
  "defense": 55,
  "height": 0.3
}

Fetched 8 record(s) in 1ms


## Liste todos Pokemons com o name 'Pikachu' OU com attack menor ou igual que 0.5
maba(mongod-3.0.7) be-mean-pokemons> var query1 = {name: 'Pikachu'}

maba(mongod-3.0.7) be-mean-pokemons> var query2 = {attack: {lte: 0.5}}

maba(mongod-3.0.7) be-mean-pokemons> db.pokemons.find({$or: [query1, query2]})
{
  "_id": ObjectId("56491d6ad6663c31c5533813"),
  "name": "Pikachu",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Rato",
  "attack": 55,
  "defense": 40,
  "height": 0.41
}
Fetched 1 record(s) in 1ms


## Liste todos Pokemons com attack maior ou igual que 48 e com height menor ou igual que 0.5

maba(mongod-3.0.7) be-mean-pokemons> var query1 = {attack: {$gte: 48}}

maba(mongod-3.0.7) be-mean-pokemons> var query2 = {height: {$lte: 0.5}}

maba(mongod-3.0.7) be-mean-pokemons> db.pokemons.find({$or: [query1, query2]})
{
  "_id": ObjectId("564919d5d6663c31c553380a"),
  "name": "Bulbasaur",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Semente",
  "attack": 49,
  "defense": 49,
  "height": 0.71
}

{
  "_id": ObjectId("56491a36d6663c31c553380b"),
  "name": "Charmander",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Lagarto",
  "attack": 52,
  "defense": 43,
  "height": 0.61
}

{
  "_id": ObjectId("56491aa0d6663c31c553380c"),
  "name": "Squirtle",
  "description": "Introduzido na Geração 1, é conhecido como Pequena Tartaruga Pokémon",
  "attack": 48,
  "defense": 65,
  "height": 0.51
}

{
  "_id": ObjectId("56491afdd6663c31c553380d"),
  "name": "Caterpie",
  "description": "Introduzido na Geração 1, é conhecido como Verme Pokémon",
  "attack": 30,
  "defense": 35,
  "height": 0.3
}

{
  "_id": ObjectId("56491b8bd6663c31c553380e"),
  "name": "Weedle",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Inseto Peludo",
  "attack": 35,
  "defense": 30,
  "height": 0.3
}

{
  "_id": ObjectId("56491c19d6663c31c553380f"),
  "name": "Pidgey",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Passarinho",
  "attack": 45,
  "defense": 40,
  "height": 0.3
}

{
  "_id": ObjectId("56491c70d6663c31c5533810"),
  "name": "Rattata",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Rato",
  "attack": 56,
  "defense": 35,
  "height": 0.3
}

{
  "_id": ObjectId("56491cadd6663c31c5533811"),
  "name": "Spearow",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Passarinho",
  "attack": 60,
  "defense": 30,
  "height": 0.3
}

{
  "_id": ObjectId("56491d2dd6663c31c5533812"),
  "name": "Ekans",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Cobra",
  "attack": 60,
  "defense": 44,
  "height": 2.01
}

{
  "_id": ObjectId("56491d6ad6663c31c5533813"),
  "name": "Pikachu",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Rato",
  "attack": 55,
  "defense": 40,
  "height": 0.41
}

{
  "_id": ObjectId("56491d9fd6663c31c5533814"),
  "name": "Sandshrew",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Rato",
  "attack": 75,
  "defense": 85,
  "height": 0.61
}

{
  "_id": ObjectId("56491e0ad6663c31c5533815"),
  "name": "Nidoran",
  "description": "Introduzido na Geração 1, é conhecido como Pokemón Venenoso",
  "attack": 47,
  "defense": 52,
  "height": 0.41
}

{
  "_id": ObjectId("56491f6bd6663c31c553381a"),
  "name": "Oddish",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Erva-Daninha",
  "attack": 50,
  "defense": 55,
  "height": 0.51
}

{
  "_id": ObjectId("56491fabd6663c31c553381b"),
  "name": "Paras",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Cogumelo",
  "attack": 70,
  "defense": 55,
  "height": 0.3
}

{
  "_id": ObjectId("56491fe1d6663c31c553381c"),
  "name": "Venonat",
  "description": "Introduzido na Geração 1, é conhecido como Pokémon Inseto",
  "attack": 55,
  "defense": 50,
  "height": 0.99
}

Fetched 15 record(s) in 4ms