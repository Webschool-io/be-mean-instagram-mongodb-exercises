# MongoBD - Aula 02 - Exercício
Autor: Higor Roberto da Silva


## Criar uma database

> use be-mean-pokemons
switched to db be-mean-pokemons


## Listar databases no servidor

> show dbs
be-mean            0.078GB
be-mean-instagran  0.078GB
be-mean-teste      0.078GB
local              0.078GB


## Listar collections no servidor

> show collections


## Inserir 5 pokemons

var pokemon = [
{'name':'Vileplume','description':'Chapeu de flor',attack: 24, defense: 25, heigth: 0.5},
{'name':'Psyduck','description':'Esse pato é chapado',attack: 44, defense: 28, heigth: 0.8},
{'name':'Persian','description':'Esse gato é lessi',attack: 24, defense: 69, heigth: 0.5},
{'name':'Alakazam','description':'Essa porro é do mal',attack: 54, defense: 28, heigth: 0.9},
{'name':'Machamp','description':'Eu bebi muito ou esse cara tem 4 braços',attack: 54, defense: 25, heigth: 0.9}
]


> db.pokemons.insert(pokemon)
BulkWriteResult({
        "writeErrors" : [ ],
        "writeConcernErrors" : [ ],
        "nInserted" : 5,
        "nUpserted" : 0,
        "nMatched" : 0,
        "nModified" : 0,
        "nRemoved" : 0,
        "upserted" : [ ]
})


## Listar os pokemons existentes na minha collection

> db.pokemons.find()
{ "_id" : ObjectId("564bedce8c1034120d257739"), "name" : "Vileplume", "description" : "Chapeu de flor", "attack" : 24, "defense" : 25, "heigth" : 0.5 }
{ "_id" : ObjectId("564bedce8c1034120d25773a"), "name" : "Psyduck", "description" : "Esse pato é chapado", "attack" : 44, "defense" : 28, "heigth" : 0.8 }
{ "_id" : ObjectId("564bedce8c1034120d25773b"), "name" : "Persian", "description" : "Esse gato é lessi", "attack" : 24, "defense" : 69, "heigth" : 0.5 }
{ "_id" : ObjectId("564bedce8c1034120d25773c"), "name" : "Alakazam", "description" : "Essa porro é do mal", "attack" : 54, "defense" : 28, "heigth" : 0.9 }
{ "_id" : ObjectId("564bedce8c1034120d25773d"), "name" : "Machamp", "description" : "Eu bebi muito ou esse cara tem 4 braços", "attack" : 54, "defense" : 25, "heigth" : 0.9 }


## Buscar um pokemon pelo nome


> var query = {name: 'Psyduck'}
> var poke = db.pokemons.findOne(query)
> poke
{
        "_id" : ObjectId("564bedce8c1034120d25773a"),
        "name" : "Psyduck",
        "description" : "Esse pato é chapado",
        "attack" : 44,
        "defense" : 28,
        "heigth" : 0.8
}


## Modificar a description e salvê-a


> poke.description = 'Esse pato é doidão'
Esse pato é doidão
> poke
{
        "_id" : ObjectId("564bedce8c1034120d25773a"),
        "name" : "Psyduck",
        "description" : "Esse pato é doidão",
        "attack" : 44,
        "defense" : 28,
        "heigth" : 0.8
}
> db.pokemons.save(poke)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
