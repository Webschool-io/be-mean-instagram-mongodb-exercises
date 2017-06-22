MongoDB - Aula 03 - Exercício

Autor: Angelo Rogério Rubin

Liste todos Pokemons com a altura menor que 0.5; (passo 1)

> var query = { height: { $lte: 0.5 } }
> db.pokemons.find(query)
{ "_id" : ObjectId("5644ead9a2c7f2543fe0ff45"), "name" : "Pikachu", "description" : "Rato Elétrico", "type" : "eletric", "attack" : 55, "height" : 0.4 }
{ "_id" : ObjectId("5644f3f9a2c7f2543fe0ff48"), "name" : "Bulbassauro", "description" : "O chicote estrala", "type" : "grama", "attack" : 49, "height" : 0.4 }
{ "_id" : ObjectId("5644f4bca2c7f2543fe0ff4a"), "name" : "Squirtle", "description" : "Ejeta agua", "type" : "agua", "attack" : 48, "height" : 0.5 }
{ "_id" : ObjectId("5644fd892d657aa215659584"), "name" : "Caterpie", "description" : "Larva lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3, "defense" : 35 }

Liste todos Pokemons com a altura maior ou igual que 0.5; (passo 2)

> var query = { height: { $gte: 0.5 } }
> db.pokemons.find(query)
{ "_id" : ObjectId("5644f44da2c7f2543fe0ff49"), "name" : "Charmander", "description" : "Taca fogo nele chessuis", "type" : "fogo", "attack" : 52, "height" : 0.6 }
{ "_id" : ObjectId("5644f4bca2c7f2543fe0ff4a"), "name" : "Squirtle", "description" : "Ejeta agua", "type" : "agua", "attack" : 48, "height" : 0.5 }

Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama; (passo 3)

> var query = { $and: [{ height: { $lte : 0.5 }}, { type: "grama" }]}
> db.pokemons.find(query)
{ "_id" : ObjectId("5644f3f9a2c7f2543fe0ff48"), "name" : "Bulbassauro", "description" : "O chicote estrala", "type" : "grama", "attack" : 49, "height" : 0.4 }

Liste todos Pokemons com name 'Pikachu' OU com attack menor ou igual que 0.5 (passo 4)

> var query = { $or: [{ name: "Pikachu" }, { attack: { $lte : 0.5 }}]}
> db.pokemons.find(query)
{ "_id" : ObjectId("5644ead9a2c7f2543fe0ff45"), "name" : "Pikachu", "description" : "Rato Elétrico", "type" : "eletric", "attack" : 55, "height" : 0.4 }

Liste todos Pokemons com attack maior ou igual que 48 E com height menor ou igual que 0.5 (passo 5)

> var query = { $and: [{attack: {$gte : 48}}, {height: {$lte : 0.5}}]}
> db.pokemons.find(query)
{ "_id" : ObjectId("5644ead9a2c7f2543fe0ff45"), "name" : "Pikachu", "description" : "Rato Elétrico", "type" : "eletric", "attack" : 55, "height" : 0.4 }
{ "_id" : ObjectId("5644f3f9a2c7f2543fe0ff48"), "name" : "Bulbassauro", "description" : "O chicote estrala", "type" : "grama", "attack" : 49, "height" : 0.4 }
{ "_id" : ObjectId("5644f4bca2c7f2543fe0ff4a"), "name" : "Squirtle", "description" : "Ejeta agua", "type" : "agua", "attack" : 48, "height" : 0.5 }