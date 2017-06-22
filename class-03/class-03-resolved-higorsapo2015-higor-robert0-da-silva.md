#MongoDB - Aula 02 - Exercício

Autor: Higor Roberto da Silva


##Listar todos Pokemons com altura menor que 0.5

> db.pokemons.find(query)
{
 "_id" : ObjectId("564bedce8c1034120d25773b"), 
 "name" : "Persian", 
 "description" : "Esse gato é lessi", 
 "attack" : 24, 
 "defense" : 69, 
 "heigth" : 0.4 
}

##Listar todos Pokemons com altura maior ou igual que 0.5

> db.pokemons.find(query)
{
 "_id" : ObjectId("564bedce8c1034120d257739"), 
 "name" : "Vileplume", 
 "description" : "Chapeu de flor", 
 "attack" : 24, 
 "defense" : 25, 
 "heigth" : 0.5 
}
{
 "_id" : ObjectId("564bedce8c1034120d25773a"), 
 "name" : "Psyduck", 
 "description" : "Esse pato é doidão", 
 "attack" : 44, 
 "defense" : 28, 
 "heigth" : 0.8 
}
{ 
 "_id" : ObjectId("564bedce8c1034120d25773c"), 
 "name" : "Alakazam", 
 "description" : "Essa porro é do mal", 
 "attack" : 54, 
 "defense" : 28, 
 "heigth" : 0.9 
}
{ 
 "_id" : ObjectId("564bedce8c1034120d25773d"), 
 "name" : "Machamp", 
 "description" : "Eu bebi muito ou esse cara tem 4 braços", 
 "attack" : 54, 
 "defense" : 25, 
 "heigth" : 0.9 
}


####Listar todos Pokemons com altura menor ou igual que 0.5 E com a defesa 25

var query = {$and:[{heigth:{$lte: 0.5}},{defense: 25}]}
> db.pokemons.find(query)
{ 
 "_id" : ObjectId("564bedce8c1034120d257739"), 
 "name" : "Vileplume", 
 "description" : "Chapeu de flor", 
 "attack" : 24, 
 "defense" : 25, 
 "heigth" : 0.5 
}


##Listar todos Pokemons com name Alakazam OU com attack menor ou igual que 30

> var query = {$or:[{name: 'Alakazam'}, {attack: {$lte: 30}}]}
> db.pokemons.find(query)
{ 
 "_id" : ObjectId("564bedce8c1034120d257739"), 
 "name" : "Vileplume", 
 "description" : "Chapeu de flor", 
 "attack" : 24, 
 "defense" : 25, 
 "heigth" : 0.5 
}
{
 "_id" : ObjectId("564bedce8c1034120d25773b"), 
 "name" : "Persian", 
 "description" : "Esse gato é lessi", 
 "attack" : 24, 
 "defense" : 69, 
 "heigth" : 0.4 
 }
{
 "_id" : ObjectId("564bedce8c1034120d25773c"), 
 "name" : "Alakazam", 
 "description" : "Essa porro é do mal", 
 "attack" : 54, 
 "defense" : 28, 
 "heigth" : 0.9 
}


##Liste todos Pokemons com attack MAIOR OU IGUAL QUE 48 E com heigth menor ou igual que 0.5

> var query = {$and:[{attack:{$gte: 48}}, {heigth:{$lte: 0.5}}]}