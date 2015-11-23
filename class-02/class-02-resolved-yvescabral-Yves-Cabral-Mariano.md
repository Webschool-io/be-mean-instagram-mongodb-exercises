# MongoDB - Aula 02 - Exercício
autor: Yves Cabral

## Listagem das databases (passo 2)
'''
> use be-mean-pokemons
switched to db be-mean-pokemons
'''

## Listagem das coleções (passo 3)
'''
> show collections
> // nunhuma collection, suissa seu trollzão!
'''

## Cadastro dos pokemons (passo 4)
'''
> db.pokemons.insert({name:'Ponyta', description:'Cavalo de fogo', attack:65, defense: 65, height: 0.3})
> db.pokemons.insert({name:'Rapidash', description:'Cavalo de fogo grandão', attack:80, defense: 80, height: 0.4})
> db.pokemons.insert({name:'Slowpoke', description:'Um pokemon com cara de retardado', attack:40, defense: 40, height: 0.2})
> db.pokemons.insert({name:'Slowbro', description:'Evolução do slowpoke', attack:100, defense: 80, height: 0.3})
> db.pokemons.insert({name:'Magnemite', description:'Pokemon imã vivo', attack:95, defense: 70, height: 0.1})
'''

## Lista dos pokemons (passo 5)
'''
> db.pokemons.find()
{ "_id" : ObjectId("5644dd0e5d659c5a3cf6cf67"), "name" : "Ponyta", "description" : "Cavalo de fogo", "attack" : 65, "defense" : 65, "height" : 0.3 }
{ "_id" : ObjectId("5644e3c25d659c5a3cf6cf68"), "name" : "Rapidash", "description" : "Evolução do Ponyta", "attack" : 80, "defense" : 80, "height" : 0.4 }
{ "_id" : ObjectId("5644e4325d659c5a3cf6cf69"), "name" : "Slowpoke", "description" : "Um pokemon com cara de retardado", "attack" : 40, "defense" : 40, "height" : 0.2 }
{ "_id" : ObjectId("5644e4725d659c5a3cf6cf6a"), "name" : "Slowbro", "description" : "Evolução do slowpoke", "attack" : 100, "defense" : 80, "height" : 0.3 }
{ "_id" : ObjectId("5644e88f67387c7ed9078e1c"), "name" : "Magnemite", "description" : "Pokemon imã vivo", "attack" : 95, "defense" : 70, "height" : 0.1 }
'''

## Pokemon (passo 6)
'''
> poke = db.pokemons.findOne({name:'Rapidash'})
{
	"_id" : ObjectId("5644e3c25d659c5a3cf6cf68"),
	"name" : "Rapidash",
	"description" : "Cavalo de fogo grandão",
	"attack" : 80,
	"defense" : 80,
	"height" : 0.4
}
'''

## Atualização do Pokemon (passo 7)

'''
> poke.description = 'Evolução do Ponyta'
Evolução do Ponyta
> db.pokemons.save(poke)
> db.pokemons.findOne({name:'Rapidash'})
{
	"_id" : ObjectId("5644e3c25d659c5a3cf6cf68"),
	"name" : "Rapidash",
	"description" : "Evolução do Ponyta",
	"attack" : 80,
	"defense" : 80,
	"height" : 0.4
}
> //ih mlk, deu certo msm. vlw suissa!
'''
