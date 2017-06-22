MongoDB - Aula 02 - Exercício autor: Gustavo Guimarães

0 - Pokemons Existentes na base para Validação dos resultados.

gustavorag-Inspiron-5437(mongod-3.0.7) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("5643e73f28d44182097ffec0"),
  "name": "Caterpie",
  "description": "For protection, it releases a horrible stench from the antennae on its head to drive away enemies.",
  "attack": 30,
  "defense": 55,
  "height": 0.4,
  "type": "Grama"
}
{
  "_id": ObjectId("5643e76c28d44182097ffec1"),
  "name": "Beedrill",
  "description": "If it becomes agitated during battle, it spouts intense flames, incinerating its surroundings.",
  "attack": 90,
  "defense": 40,
  "height": 0.5,
  "type": "Flame"
}
{
  "_id": ObjectId("5643e79528d44182097ffec2"),
  "name": "Clefairy",
  "description": "Adored for their cute looks and playfulness. They are thought to be rare, as they do not appear often.",
  "attack": 45,
  "defense": 48,
  "height": 6,
  "type": "Normal"
}
{
  "_id": ObjectId("5643e7bb28d44182097ffec3"),
  "name": "Wigglytuff",
  "description": "The body is soft and rubbery. When angered, it will suck in air and inflate itself to an enormous size.",
  "attack": 0.4,
  "defense": 45,
  "height": 10,
  "type": "Sonic"
}
{
  "_id": ObjectId("5643e7e128d44182097ffec4"),
  "name": "Vileplume",
  "description": "Esta é a nova descrição do Vileplume",
  "attack": 80,
  "defense": 85,
  "height": 12,
  "type": "Fungus"
}
{
  "_id": ObjectId("5643e7fc28d44182097ffec5"),
  "name": "Persian",
  "description": "Many adore it for its sophisticated air. However, it will lash out and scratch for little reason.",
  "attack": 70,
  "defense": 60,
  "height": 10,
  "type": "Cat"
}
Fetched 6 record(s) in 2ms

1 - Listagem de pokemons com altura menor do que 0.5

gustavorag-Inspiron-5437(mongod-3.0.7) be-mean-pokemons> db.pokemons.find({height:{$lt : 0.5}})
{
  "_id": ObjectId("5643e73f28d44182097ffec0"),
  "name": "Caterpie",
  "description": "For protection, it releases a horrible stench from the antennae on its head to drive away enemies.",
  "attack": 30,
  "defense": 55,
  "height": 0.4,
  "type": "Grama"
}
Fetched 1 record(s) in 0ms

2 - Listagem de pokemons com altura maior ou igual a 0.5

gustavorag-Inspiron-5437(mongod-3.0.7) be-mean-pokemons> db.pokemons.find({height:{$gte : 0.5}})
{
  "_id": ObjectId("5643e76c28d44182097ffec1"),
  "name": "Beedrill",
  "description": "If it becomes agitated during battle, it spouts intense flames, incinerating its surroundings.",
  "attack": 90,
  "defense": 40,
  "height": 0.5,
  "type": "Flame"
}
{
  "_id": ObjectId("5643e79528d44182097ffec2"),
  "name": "Clefairy",
  "description": "Adored for their cute looks and playfulness. They are thought to be rare, as they do not appear often.",
  "attack": 45,
  "defense": 48,
  "height": 6,
  "type": "Normal"
}
{
  "_id": ObjectId("5643e7bb28d44182097ffec3"),
  "name": "Wigglytuff",
  "description": "The body is soft and rubbery. When angered, it will suck in air and inflate itself to an enormous size.",
  "attack": 0.4,
  "defense": 45,
  "height": 10,
  "type": "Sonic"
}
{
  "_id": ObjectId("5643e7e128d44182097ffec4"),
  "name": "Vileplume",
  "description": "Esta é a nova descrição do Vileplume",
  "attack": 80,
  "defense": 85,
  "height": 12,
  "type": "Fungus"
}
{
  "_id": ObjectId("5643e7fc28d44182097ffec5"),
  "name": "Persian",
  "description": "Many adore it for its sophisticated air. However, it will lash out and scratch for little reason.",
  "attack": 70,
  "defense": 60,
  "height": 10,
  "type": "Cat"
}
Fetched 5 record(s) in 2ms


3 - Listagem de pokemons com altura menor ou igual a 0.5 e tipo grama

gustavorag-Inspiron-5437(mongod-3.0.7) be-mean-pokemons> db.pokemons.find({$and:[{height:{$lte : 0.5}},{type:'Grama'}]})
{
  "_id": ObjectId("5643e73f28d44182097ffec0"),
  "name": "Caterpie",
  "description": "For protection, it releases a horrible stench from the antennae on its head to drive away enemies.",
  "attack": 30,
  "defense": 55,
  "height": 0.4,
  "type": "Grama"
}
Fetched 1 record(s) in 3ms

4 - Listagem de pokemons com nome igual a 'Pikachu' ou attack menor ou igual a 0.5

gustavorag-Inspiron-5437(mongod-3.0.7) be-mean-pokemons> db.pokemons.find({$or:[ {name:'Pikachu'} , {attack:{$lte : 0.5}} ]})
{
  "_id": ObjectId("5643e7bb28d44182097ffec3"),
  "name": "Wigglytuff",
  "description": "The body is soft and rubbery. When angered, it will suck in air and inflate itself to an enormous size.",
  "attack": 0.4,
  "defense": 45,
  "height": 10,
  "type": "Sonic"
}
Fetched 1 record(s) in 2ms

5 - Listagem de pokemons com attack maior ou igual a 48 e com altura menor ou igual a 0.5

gustavorag-Inspiron-5437(mongod-3.0.7) be-mean-pokemons> db.pokemons.find({$and:[ {attack:{$gte : 48}} , {height:{$lte : 0.5}} ]})
{
  "_id": ObjectId("5643e76c28d44182097ffec1"),
  "name": "Beedrill",
  "description": "If it becomes agitated during battle, it spouts intense flames, incinerating its surroundings.",
  "attack": 90,
  "defense": 40,
  "height": 0.5,
  "type": "Flame"
}
Fetched 1 record(s) in 1ms



