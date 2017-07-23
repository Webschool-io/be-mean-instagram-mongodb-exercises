 # MongoDB - Aula 03 - Exercício
autor: Diego Vieira

## 1- lista todos pokemons com altura menor que 0.5;
´´´
> query = {height: {$lt : 0.5}}
{ "height" : { "$lt" : 0.5 } }
> db.pokemons.find(query)
>
´´´
## 2- lista todos pokemons com altura maior ou igual a 0.5;
´´´
> query = {height: {$gte : 0.5}}
{ "height" : { "$gte" : 0.5 } }
> db.pokemons.find(query)
{ "_id" : ObjectId("56448b53e7835cf12d9fb4cc"), "name" : "Raikou", "description" : "Cachorro lendário eletrico", "defense" : 30, "attack" : 40, "height" : 1.9 }
{ "_id" : ObjectId("56448b53e7835cf12d9fb4cd"), "name" : "Entei", "description" : "Cachorro lendário de fogo bonito pra caramba", "defense" : 30, "attack" : 60, "height" : 2.1 }
{ "_id" : ObjectId("56448b53e7835cf12d9fb4ce"), "name" : "Suicune", "description" : "Cachorro lendário de gelo", "defense" : 50, "attack" : 40, "height" : 2 }
{ "_id" : ObjectId("56448b53e7835cf12d9fb4cf"), "name" : "Articuno", "description" : "Ave lendário de gelo", "defense" : 40, "attack" : 40, "height" : 1.7 }
{ "_id" : ObjectId("56448b53e7835cf12d9fb4d0"), "name" : "Lugia ", "description" : "lendário mais badass que existe", "defense" : 60, "attack" : 50, "height" : 5.2 }
´´´
## 3- lista todos pokemons com altura menor ou igual a 1.9 e do tipo eletrico;
´´´
> query = {$and : [{height : {$lte: 1.9}},{name : 'Raikou'}]}
{
        "$and" : [
                {
                        "height" : {
                                "$lte" : 1.9
                        }
                },
                {
                        "name" : "Raikou"
                }
        ]
}
> db.pokemons.find(query)
{ "_id" : ObjectId("56448b53e7835cf12d9fb4cc"), "name" : "Raikou", "description" : "Cachorro lendário eletrico", "defense" : 30, "attack" : 40, "height" : 1.9, "type" : "eletric" }

´´´ 
## 4- lista todos pokemons com o nome Raikou ou com atack menor ou igual a 40
´´´
> query = {$and : [{attack : {$lte: 40}},{name : 'Raikou'}]}
{
        "$and" : [
                {
                        "attack" : {
                                "$lte" : 40
                        }
                },
                {
                        "name" : "Raikou"
                }
        ]
}
> db.pokemons.find(query)
{ "_id" : ObjectId("56448b53e7835cf12d9fb4cc"), "name" : "Raikou", "description" : "Cachorro lendário eletrico", "defense" : 30, "attack" : 40, "height" : 1.9, "type" : "eletric" }
´´´     
## 5- lista todos pokemons com o atack maior ou igual que 48 e com height maior ou igual que 1.2
´´´
> var query = {$and : [{attack: {$gte : 48}}, {height: {$gte : 1.2}}]}
> db.pokemons.find(query)
{ "_id" : ObjectId("56448b53e7835cf12d9fb4cd"), "name" : "Entei", "description" : "Cachorro lendário de fogo bonito pra caramba", "defense" : 30, "attack" : 60, "height" : 2.1 }
{ "_id" : ObjectId("56448b53e7835cf12d9fb4d0"), "name" : "Lugia ", "description" : "lendário mais badass que existe", "defense" : 60, "attack" : 50, "height" : 5.2 }
´´´ 