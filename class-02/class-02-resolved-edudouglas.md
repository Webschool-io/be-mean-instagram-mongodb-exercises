# MongoDB - Aula 02 - Exercício
autor: Eduardo Douglas da Silva

# Criando database
> use be-mean-pokemons
switched to db be-mean-pokemons

# Listagem das databases (passo 2)
> show dbs
be-mean	0.203125GB
local	0.078125GB

# Listagem das coleções (passo 3)
> db.createCollection('pokemons')
{ "ok" : 1 }

> show collections
pokemons
system.indexes

# Cadastro dos pokemons (passo 4)
var pokemon =   
[
  {
  'name':'Zapdos',
  description:'Tipo Elétrico',
  atack:60,
  defense:50,
  height:5.3
  },

  {
  'name':'Articuno',
  description:'Tipo Gelo',
  atack:50,
  defense:50,
  height:4.1
  },

  {
  'name':'Charizard',
  description:'Tipo Dragão Voador',
  atack:47,
  defense:49,
  height:90.5
  },

  {
  'name':'Bulbasaur',
  description:'Tipo Planta',
  atack:25,
  defense:25,
  height:6.9
  },

  {
  'name':'Tauros',
  description:'Tipo Boi',
  atack:56,
  defense:40,
  height:88.4
  }
]
> db.pokemons.insert(pokemon)

# Lista dos pokemons (passo 5)
> db.pokemons.find()
{ "_id" : ObjectId("564747ba8990240dfd5b1a59"), "name" : "Zapdos", "description" : "Tipo Elétrico", "atack" : 60, "defense" : 50, "height" : 5.3 }
{ "_id" : ObjectId("564747ba8990240dfd5b1a5a"), "name" : "Articuno", "description" : "Tipo Gelo", "atack" : 50, "defense" : 50, "height" : 4.1 }
{ "_id" : ObjectId("564747ba8990240dfd5b1a5b"), "name" : "Charizard", "description" : "Tipo Dragão Voador", "atack" : 47, "defense" : 49, "height" : 90.5 }
{ "_id" : ObjectId("564747ba8990240dfd5b1a5c"), "name" : "Bulbasaur", "description" : "Tipo Planta", "atack" : 25, "defense" : 25, "height" : 6.9 }
{ "_id" : ObjectId("564747ba8990240dfd5b1a5d"), "name" : "Tauros", "description" : "Tipo Boi", "atack" : 56, "defense" : 40, "height" : 88.4 }

# Escolher um pokemon (passo 6)
> var poke = db.pokemons.findOne({name:'Tauros'})

# Atualização pokemon escolhido(passo 6)
> poke.description = "Tipo Touro Bravo"
> db.pokemons.save(poke)
> db.pokemons.find({name: 'Tauros'})
{ "_id" : ObjectId("564747ba8990240dfd5b1a5d"), "name" : "Tauros", "description" : "Tipo Touro Bravo", "atack" : 56, "defense" : 40, "height" : 88.4 }

