# MongoDB - Aula 02 - Exercício
autor: Janderson Cassan

## Criar uma database chamada be-mean-pokemons
> use be-mean-pokemons
switched to db be-mean-pokemons
>

## Liste quais Databases você possui nesse servidor
> show dbs
be-mean-instagran  0.078GB
local              0.078GB
>

## Liste quais coleções você possui nessa Database
> show collections
>

## Insira pelo meno 5 pokemons a sua escolha
var pokemon = {name: 'Glaceon', description: 'Gelado', type: 'gelo', attack: 60, defense: 110, height: 1.0}
var pokemon = {name: 'Jolteon', description: 'Irado', type: 'eletrico', attack: 65, defense: 60, height: 0.8}
var pokemon = {name: 'Flareon', description: 'Maneiro', type: 'fogo', attack: 130,  defense: 60, height: 1.0}
var pokemon = {name: 'Leafon', description: 'Calmo', type: 'grama', attack: 110,  defense: 130,height: 0.9}
var pokemon = {name: 'Espeon', description: 'Preguica', type: 'psiquico', attack: 65,  defense: 60,height: 1.0}
var pokemon = {name: 'Eevee', description: 'Lindinho', type: 'normal', attack: 55, defense: 50, height: 0.3}

db.pokemons.insert(pokemon) 6x

## Liste os pokemons existentes na sua coleção
> db.pokemons.find()
{ 
	"_id" : ObjectId("565735b419ca786ebd5fa184"), 
	"name" : "Glaceon", 
	"description" : "Gelado", 
	"type" : "gelo", 
	"attack" : 60, 
	"defense" : 110, 
	"height" : 1 
}
{ 
	"_id" : ObjectId("565735c419ca786ebd5fa185"), 
	"name" : "Jolteon", 
	"description" : "Irado", 
	"type" : "eletrico", 
	"attack" : 65, 
	"defense" : 60, 
	"height" : 0.8
}
{ 
	"_id" : ObjectId("565735ce19ca786ebd5fa186"), 
	"name" : "Flareon", 
	"description" : "Maneiro", 
	"type" : "fogo", 
	"attack" : 130, 
	"defense" : 60, 
	"height" : 1 
}
{ 
	"_id" : ObjectId("565735d819ca786ebd5fa187"), 
	"name" : "Leafon", 
	"description" : "Calmo", 
	"type" : "grama", 
 	"attack" : 110, 
 	"defense" : 130,
 	"height" : 0.9 
 }
{ 
	"_id" : ObjectId("565735df19ca786ebd5fa188"), 
	"name" : "Espeon", 
	"description" : "Preguica", 
	"type" : "psiquico", 
	"attack" : 65, 
	"defense" : 60, 
	"height" : 1
}
{ 
	"_id" : ObjectId("565735e919ca786ebd5fa189"), 
	"name" : "Eevee", 
	"description": "Lindinho", 
	"type" : "normal", 
	"attack" : 55, 
	"defense" : 50, 
	"height" : 0.3 
}

## Busque o 'pickachu' e armazene-o em umavariavel chamada 'poke'
> var query = {name:"Espeon"}
> var poke = db.pokemons.findOne(query)

## Modifique sua description e salvê-o
> poke.description = "Altera Preguica"
Altera Preguica
> db.pokemons.save(poke)
WriteResult({ 
	"nMatched" : 1, 
	"nUpserted" : 0, 
	"nModified" : 1 
	})

> db.pokemons.findOne(query)
{
        "_id" : ObjectId("565735df19ca786ebd5fa188"),
        "name" : "Espeon",
        "description" : "Altera Preguica",
        "type" : "psiquico",
        "attack" : 65,
        "defense" : 60,
        "height" : 1
}
>

