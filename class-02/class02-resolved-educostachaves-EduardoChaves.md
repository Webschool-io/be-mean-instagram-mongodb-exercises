###MongoDB - Aula 02 - Exercício
Autor: Eduardo Chaves

##Criando database
```
2015-11-20 19:17:00 ☆  Eduardo-Chaves in ~/projects/be-mean-instagram-mongodb-excercises
± |master → origin ?:1 ✗| → mongo be-mean-pokemons
MongoDB shell version: 3.0.7
connecting to: be-mean-pokemons
Welcome to the MongoDB shell.
For interactive help, type "help".
For more comprehensive documentation, see
 http://docs.mongodb.org/
Questions? Try the support group
 http://groups.google.com/group/mongodb-user
2015-11-20T19:17:36.377-0200 I STORAGE  In File::open(), ::open for '/Users/eduardochaves/.mongorc.js' failed with errno:2 No such file or directory
Server has startup warnings:
2015-11-20T17:53:32.919-0200 I CONTROL  [initandlisten]
2015-11-20T17:53:32.919-0200 I CONTROL  [initandlisten] ** WARNING: soft rlimits too low. Number of files is 256, should be at least 1000
>
```

##Listando databases
```
> show dbs
be-mean            0.078GB
be-mean-instagram  0.078GB
chimera-dev        0.078GB
local              0.078GB
test               0.078GB
>
```

##Listando collections
```
> show collections
pokemons
system.indexes
```

##Cadastro dos pokemons
```
> var pokemon = [{'name': 'Ivysaur', 'description': 'Mostro de feito de plantas', 'type': 'grama', 'attack': 65, 'defense': 40, 'height': 1.0}, {'name': 'Blastoise', 'description': 'Monstro de água muito poderoso', 'type': 'água', 'attack': 75, 'defense': '32', 'height': 1.6 },{'name': 'Venusaur', 'description': 'Monstro de veneno muito poderoso', 'type': 'grama', 'attack': 82, 'defense': '68', 'height': 2.2 },{'name': 'Mega Venusaur', 'description': 'Monstro de grama e veneno extremamente poderoso', 'type': 'grama', 'attack': 100, 'defense': '90', 'height': 2.4 },{'name': 'Charmeleon', 'description': 'Monstro de Fogo muito poderoso', 'type': 'fogo', 'attack': 32, 'defense': '31', 'height': 1.1 }]
> db.pokemons.save(pokemon)
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
>
```

##Lista de todos os pokemons
```
> db.pokemons.find()
{ "_id" : ObjectId("564f9168793b2b526913ebc8"), "name" : "Ivysaur", "description" : "Mostro de feito de plantas", "type" : "grama", "attack" : 65, "defense" : 40, "height" : 1 }
{ "_id" : ObjectId("564f9168793b2b526913ebc9"), "name" : "Blastoise", "description" : "Monstro de água muito poderoso", "type" : "água", "attack" : 75, "defense" : "32", "height" : 1.6 }
{ "_id" : ObjectId("564f9168793b2b526913ebca"), "name" : "Venusaur", "description" : "Monstro de veneno muito poderoso", "type" : "grama", "attack" : 82, "defense" : "68", "height" : 2.2 }
{ "_id" : ObjectId("564f9168793b2b526913ebcb"), "name" : "Mega Venusaur", "description" : "Monstro de grama e veneno extremamente poderoso", "type" : "grama", "attack" : 100, "defense" : "90", "height" : 2.4 }
{ "_id" : ObjectId("564f9168793b2b526913ebcc"), "name" : "Charmeleon", "description" : "Monstro de Fogo muito poderoso", "type" : "fogo", "attack" : 32, "defense" : "31", "height" : 1.1 }
>
```

##Query para buscar o pokemon
```
> var query = {name: 'Charmeleon'}
> var poke = db.pokemons.find(query)
> poke
{ "_id" : ObjectId("564f9168793b2b526913ebcc"), "name" : "Charmeleon", "description" : "Monstro de Fogo muito poderoso", "type" : "fogo", "attack" : 32, "defense" : "31", "height" : 1.1 }
>
```

##Atualizando a descrição do Pokemon
```
> var query = {name: 'Ivysaur'}
> var poke = db.pokemons.findOne(query)
> poke.defense = 41
41
> db.pokemons.save(poke)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
>
```
