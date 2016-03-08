# MongoDB - Aula 03 - Exercício
autor: MARCO COMASSETTO


LISTA TODOS OS POKEMONS COM A ALTURA MENOR QUE 0.5

> db.pokemons.find(query)
> var query = {height:{$lt:0.5}}

> db.pokemons.find(query)
{ "_id" : ObjectId("56dc829d88bfdffaf08efa43"), "name" : "Pikachu", "description" : "Raio elétrico", "type" : "eletric", "attack" : 55, "height" : 0.4 }
{ "_id" : ObjectId("56dc83e588bfdffaf08efa44"), "name" : "Bulbassauro", "description" : "Chicote", "type" : "grama", "attack" : 49, "height" : 0.4 }
{ "_id" : ObjectId("56dc84df88bfdffaf08efa47"), "name" : "Caterpie", "description" : "Larva", "type" : "inseto", "attack" : 30, "height" : 0.3, "defense" : 35 }



LISTA TODOS OS POKEMONS COM A ALTURA MAIOR OU IGUAL QUE 0.5

> var query = {height:{$gte:0.5}}
> db.pokemons.find(query)
{ "_id" : ObjectId("56dc83ef88bfdffaf08efa45"), "name" : "Charmander", "description" : "Rabo de fogo", "type" : "fogo", "attack" : 52, "height" : 0.6 }
{ "_id" : ObjectId("56dc83f688bfdffaf08efa46"), "name" : "Squirtle", "description" : "Ejeta Agua", "type" : "agua", "attack" : 48, "height" : 0.5 }


LISTA TODOS OS POKEMONS COM A ALTURA MENOR OU IGUAL QUE 0.5 E DO TIPO GRAMA

> var query = {$and: [{height:{$lte:0.5}},{type:'grama'} ]}
> db.pokemons.find(query)
{ "_id" : ObjectId("56dc83e588bfdffaf08efa44"), "name" : "Bulbassauro", "description" : "Chicote", "type" : "grama", "attack" : 49, "height" : 0.4 }


LISTA TODOS OS POKEMONS COM O NAME 'PIKACHU' OU COM ATTACK MENOR OU IGUAL QUE 0.5

> var query = {$or: [{name:'Pikachu'},{attack:{$lte:0.5}} ]}
> db.pokemons.find(query)
{ "_id" : ObjectId("56dc829d88bfdffaf08efa43"), "name" : "Pikachu", "description" : "Raio elétrico", "type" : "eletric", "attack" : 55, "height" : 0.4 }



LISTA TODOS OS POKEMONS COM O ATTACK MAIOR OU IGUAL QUE 48 E COM HEIGHT MENOR U IGUAL QUE 0.5

> var query = {$and: [{attack:{$gte:48}}, {height: {$lte:0.5 }} ]}
> db.pokemons.find(query)
{ "_id" : ObjectId("56dc829d88bfdffaf08efa43"), "name" : "Pikachu", "description" : "Raio elétrico", "type" : "eletric", "attack" : 55, "height" : 0.4 }
{ "_id" : ObjectId("56dc83e588bfdffaf08efa44"), "name" : "Bulbassauro", "description" : "Chicote", "type" : "grama", "attack" : 49, "height" : 0.4 }
{ "_id" : ObjectId("56dc83f688bfdffaf08efa46"), "name" : "Squirtle", "description" : "Ejeta Agua", "type" : "agua", "attack" : 48, "height" : 0.5 }

