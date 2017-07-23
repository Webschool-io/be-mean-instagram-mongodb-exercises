# MongoDB - Aula 03 - Exercício
autor: Marcelo Santana Martins

## Liste todos Pokemons com a altura menor que 0.5 (passo 1)
marcelo-VirtualBox(mongod-3.0.7) be-mean-pokemons> var query = {height: {$lt: 0.5}}
marcelo-VirtualBox(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5644c6ffe1e9cc030fc3830f"),
  "name": "Pichu",
  "description": "Pichu charges itself with electricity more easily on days with thunderclouds or when the air is very dry.",
  "attack": 20,
  "defense": 10,
  "height": 0.3
}
{
  "_id": ObjectId("5644c6ffe1e9cc030fc38310"),
  "name": "Togepi",
  "description": "As its energy, Togepi uses the positive emotions of compassion and pleasure exuded by people and Pokémon",
  "attack": 10,
  "defense": 30,
  "height": 0.3
}
Fetched 2 record(s) in 1ms


## Liste todos Pokemons com a altura maior ou igual que 0.5 (passo 2)
marcelo-VirtualBox(mongod-3.0.7) be-mean-pokemons> var query = {height: {$gte: 0.5}}
marcelo-VirtualBox(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5644c6ffe1e9cc030fc3830d"),
  "name": "Squirtle",
  "description": "Squirtles shell is not merely used for protection.",
  "attack": 30,
  "defense": 30,
  "height": 0.5
}
{
  "_id": ObjectId("5644c6ffe1e9cc030fc3830e"),
  "name": "Chinchou",
  "description": "Chinchou lets loose positive and negative electrical charges from its two antennas to make its prey faint.",
  "attack": 20,
  "defense": 20,
  "height": 0.5
}
{}
  "_id": ObjectId("5644c6ffe1e9cc030fc38311"),
  "name": "Pikachu",
  "description": "Togetic is said to be a Pokémon that brings good fortune.",
  "attack": 20,
  "defense": 40,
  "height": 0.4,
  "type": "grama"
}
Fetched 3 record(s) in 0ms
var query = {}


## Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama (passo 3)
marcelo-VirtualBox(mongod-3.0.7) be-mean-pokemons> var query = { $and: [ {height: { $lte: 0.5 }}, {type: 'grama'}]}
marcelo-VirtualBox(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5644c6ffe1e9cc030fc38311"),
  "name": "Pikachu",
  "description": "Togetic is said to be a Pokémon that brings good fortune.",
  "attack": 20,
  "defense": 40,
  "height": 0.4,
  "type": "grama"
}
Fetched 1 record(s) in 0ms


## Liste todos Pokemons com o name `Pikachu` OU com o attack menor ou igual que 0.5 (passo 4)
marcelo-VirtualBox(mongod-3.0.7) be-mean-pokemons> var query = { $or: [ {name: 'Pikachu'}, {attack: {$lte: 0.5} } ]}
marcelo-VirtualBox(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5644c6ffe1e9cc030fc38311"),
  "name": "Pikachu",
  "description": "Togetic is said to be a Pokémon that brings good fortune.",
  "attack": 20,
  "defense": 40,
  "height": 0.4,
  "type": "grama"
}
Fetched 1 record(s) in 28ms


## Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com height menor ou igual que 0.5 (passo 4)
marcelo-VirtualBox(mongod-3.0.7) be-mean-pokemons> var query = { $and: [{attack: {$gte:48}}, {height:{$lte: 0.5} }]}
marcelo-VirtualBox(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5644c6ffe1e9cc030fc3830d"),
  "name": "Squirtle",
  "description": "Squirtles shell is not merely used for protection.",
  "attack": 50,
  "defense": 30,
  "height": 0.5
}
Fetched 1 record(s) in 1ms



