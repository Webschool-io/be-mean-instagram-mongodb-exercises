# MongoDB - Aula 02 - Exercício
autor: MARCO COMASSETTO


CRIANDO A DATABASE

> use be-mean-pokemons
switched to db be-mean-pokemons


LISTANDO AS DATABASES
> show databases
be-mean-instagram   0.000GB
be-mean-instragram  0.000GB
local               0.000GB


LISTAGEM DAS COLECOES
> show collections


CADASTRO DOS POKEMONS
>var pokemon =[ { 'name':'Zapdos', description:'Tipo Elétrico', atack:60, defense:50, height:5.3 }, { 'name':'Articuno', description:'Tipo Gelo', atack:50, defense:50, height:4.1 }, { 'name':'Charizard', description:'Tipo Dragão Voador', atack:47, defense:49, height:90.5 }, { 'name':'Bulbasaur', description:'Tipo Planta', atack:25, defense:25, height:6.9 }, { 'name':'Tauros', description:'Tipo Boi', atack:56, defense:40, height:88.4 } ]

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


LISTAGEM POKEMONS EXISTENTES NA COLECAO POKEMONS
> db.pokemons.find()
{ "_id" : ObjectId("56dca4c673b4028b00c88879"), "name" : "Zapdos", "description" : "Tipo Elétrico", "atack" : 60, "defense" : 50, "height" : 5.3 }
{ "_id" : ObjectId("56dca4c673b4028b00c8887a"), "name" : "Articuno", "description" : "Tipo Gelo", "atack" : 50, "defense" : 50, "height" : 4.1 }
{ "_id" : ObjectId("56dca4c673b4028b00c8887b"), "name" : "Charizard", "description" : "Tipo Dragão Voador", "atack" : 47, "defense" : 49, "height" : 90.5 }
{ "_id" : ObjectId("56dca4c673b4028b00c8887c"), "name" : "Bulbasaur", "description" : "Tipo Planta", "atack" : 25, "defense" : 25, "height" : 6.9 }
{ "_id" : ObjectId("56dca4c673b4028b00c8887d"), "name" : "Tauros", "description" : "Tipo Boi", "atack" : 56, "defense" : 40, "height" : 88.4 }


BUSCA POKEMON PELO NOME

> var poke = {'name':'Tauros' }
> var p = db.pokemons.findOne(poke)


MODIFICANDO A DESCRIPTION DO POKEMON E SALVANDO
> p.description = 'Tipo touro'
Tipo touro
> db.pokemons.save(p)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
> db.pokemons.find()
{ "_id" : ObjectId("56dca4c673b4028b00c88879"), "name" : "Zapdos", "description" : "Tipo Elétrico", "atack" : 60, "defense" : 50, "height" : 5.3 }
{ "_id" : ObjectId("56dca4c673b4028b00c8887a"), "name" : "Articuno", "description" : "Tipo Gelo", "atack" : 50, "defense" : 50, "height" : 4.1 }
{ "_id" : ObjectId("56dca4c673b4028b00c8887b"), "name" : "Charizard", "description" : "Tipo Dragão Voador", "atack" : 47, "defense" : 49, "height" : 90.5 }
{ "_id" : ObjectId("56dca4c673b4028b00c8887c"), "name" : "Bulbasaur", "description" : "Tipo Planta", "atack" : 25, "defense" : 25, "height" : 6.9 }
{ "_id" : ObjectId("56dca4c673b4028b00c8887d"), "name" : "Tauros", "description" : "Tipo touro", "atack" : 56, "defense" : 40, "height" : 88.4 }

