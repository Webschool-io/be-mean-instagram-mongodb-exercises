# MongoDB - Aula 02 - Exercício
autor: Matheus Joveliano

## Listagem das databases (passo 2)

...
> use be-mean-pokemons
switched to db be-mean-pokemons
> show dbs
be-mean            0.078GB
be-mean-instagram  0.078GB
be-mean-pokemons   0.078GB
local              0.078GB
...

## Listagem das coleções (passo 3)

...
> show collections
pokemon
system.indexes
...

## Cadastro dos pokemons (passo 4)

...
> db.pokemon.insert({"name":"Bulbasaur","description":"Pokemons 01",attack:49,defense:49,height:0.5})
WriteResult({ "nInserted" : 1 })
> db.pokemon.insert({"name":"Charmander","description":"Pokemons 02",attack:50,defense:50,height:0.4})
WriteResult({ "nInserted" : 1 })
> db.pokemon.insert({"name":"Squirtle","description":"Pokemons 03",attack:48,defense:78,height:0.6})
WriteResult({ "nInserted" : 1 })
> db.pokemon.insert({"name":"Abra","description":"Pokemons 04",attack:35,defense:30,height:0.4})
WriteResult({ "nInserted" : 1 })
> db.pokemon.insert({"name":"Golbat","description":"Pokemons 05",attack:80,defense:70,height:0.7})
WriteResult({ "nInserted" : 1 })
...


## Lista dos pokemons (passo 5)

...
> db.pokemon.find()
{ 
	"_id" : ObjectId("564789109a9dcf2bfbb5985f"),
	"name" : "Bulbasaur",
    "description" : "Pokemons 01",
    "attack" : 49,
    "defense" : 49,
    "height" : 0.5 
}
{ 
	"_id" : ObjectId("564789549a9dcf2bfbb59860"),
    "name" : "Charmander",
    "description" : "Pokemons 02",
    "attack" : 50,
    "defense" : 50,
    "height" : 0.4 
}
{ 
	"_id" : ObjectId("564789a39a9dcf2bfbb59861"),
    "name" : "Squirtle",
    "description" : "Pokemons 03",
    "attack" : 48,
    "defense" : 78,
    "height" : 0.6 
}
{ 
   	"_id" : ObjectId("564789e09a9dcf2bfbb59862"),
    "name" : "Abra",
    "description" : "Pokemons 04",
    "attack" : 35,
    "defense": 30,
    "height" : 0.4 
}
{ 
	"_id" : ObjectId("56478a399a9dcf2bfbb59863"),
    "name" : "Golbat",
    "description" : "Pokemons 05",
    "attack" : 80,
    "defense" : 70,
    "height" : 0.7
}


## Pikachu (passo 6)

...
> var p = {name:"Abra"}
> var poke = db.pokemon.findOne(p)
> poke
{
        "_id" : ObjectId("564789e09a9dcf2bfbb59862"),
        "name" : "Abra",
        "description" : "Pokemons 04",
        "attack" : 35,
        "defense" : 30,
        "height" : 0.4
}
...

## Atualização do Pikachu (passo 6)

...
> poke.description = "Pokemon 04 - Modificado"
Pokemon 04 - Modificado
> poke
{
        "_id" : ObjectId("564789e09a9dcf2bfbb59862"),
        "name" : "Abra",
        "description" : "Pokemon 04 - Modificado",
        "attack" : 35,
        "defense" : 30,
        "height" : 0.4
}
> db.pokemon.save(poke)
WriteResult({ 
	"nMatched" : 1,
	"nUpserted" : 0,
	"nModified" : 1
})
> db.pokemon.find(poke)
{ 
	"_id" : ObjectId("564789e09a9dcf2bfbb59862"),
	"name" : "Abra",
	"description" : "Pokemon 04 - Modificado",
	"attack" : 35,
	"defense" : 30,
	"height" : 0.4 
}
...

