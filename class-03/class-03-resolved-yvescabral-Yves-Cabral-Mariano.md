# MongoDB - Aula 03 - Exercício
autor: Yves Cabral

## Listagem pokemons height < 0.5
'''
> db.pokemons.find({height: {$lt: 0.5}})
{ "_id" : ObjectId("5644dd0e5d659c5a3cf6cf67"), "name" : "Ponyta", "description" : "Cavalo de fogo", "attack" : 65, "defense" : 65, "height" : 0.3 }
{ "_id" : ObjectId("5644e3c25d659c5a3cf6cf68"), "name" : "Rapidash", "description" : "Evolução do Ponyta", "attack" : 80, "defense" : 80, "height" : 0.4 }
{ "_id" : ObjectId("5644e4325d659c5a3cf6cf69"), "name" : "Slowpoke", "description" : "Um pokemon com cara de retardado", "attack" : 40, "defense" : 40, "height" : 0.2 }
{ "_id" : ObjectId("5644e4725d659c5a3cf6cf6a"), "name" : "Slowbro", "description" : "Evolução do slowpoke", "attack" : 100, "defense" : 80, "height" : 0.3 }
{ "_id" : ObjectId("5644e88f67387c7ed9078e1c"), "name" : "Magnemite", "description" : "Pokemon imã vivo", "attack" : 95, "defense" : 70, "height" : 0.1 }
'''

## Listagem pokemons height >= 0.5
'''
> db.pokemons.find({height:{$gte: 0.5}})
> // sem pokemons cadastrados tão grandes assim
'''

## Listagem pokemons name "Pikachu" ou attack <= 0.5
'''
> db.pokemons.find({$or:[{name: 'Pikachu', attack: {$lte: 0.5}}]})
> // nada :(
'''

## Listagem pokemons attack >= 48 e height <= 0.5
'''
> db.pokemons.find({$and: [{attack: {$gte: 48}}, {height: {$lt: 0.5}}]})
{ "_id" : ObjectId("5644dd0e5d659c5a3cf6cf67"), "name" : "Ponyta", "description" : "Cavalo de fogo", "attack" : 65, "defense" : 65, "height" : 0.3 }
{ "_id" : ObjectId("5644e3c25d659c5a3cf6cf68"), "name" : "Rapidash", "description" : "Evolução do Ponyta", "attack" : 80, "defense" : 80, "height" : 0.4 }
{ "_id" : ObjectId("5644e4725d659c5a3cf6cf6a"), "name" : "Slowbro", "description" : "Evolução do slowpoke", "attack" : 100, "defense" : 80, "height" : 0.3 }
{ "_id" : ObjectId("5644e88f67387c7ed9078e1c"), "name" : "Magnemite", "description" : "Pokemon imã vivo", "attack" : 95, "defense" : 70, "height" : 0.1 }
'''

