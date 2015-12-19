# MongoDB - Aula 03 - Exercício
autor: Charles de Freitas Garcia

## Liste todos Pokemons com a altura **menor que** 0.5;

> var consulta = {height :{$lt: 0.5}}
> db.pokemons.find(consulta)
...

## Liste todos Pokemons com a altura **maior ou igual que** 0.5

> var consulta = {height :{$gte: 0.5}}
> db.pokemons.find(consulta)

{ "_id" : ObjectId("5643ef812549be4e41d3afdf"), "name" : "Mewtwo", "description" : "Descrição super, hiper, mega, modificada", "attack" : 110, "defense" : 90, "height" : 2.01, "type" : "psychic" }
{ "_id" : ObjectId("5643f0262549be4e41d3afe0"), "name" : "Heracross", "description" : "Heracross é um Bug / Lutar tipo Pokémon introduzida na Generation 2. É conhecida como o chifre único Pokémon.", "attack" : 125,"defense" : 75, "height" : 1.5, "type" : "Bug" }
{ "_id" : ObjectId("5643f0462549be4e41d3afe1"), "name" : "Groudon", "description" : "Groudon é uma terra Pokémon tipo introduzido na Geração 3. Ele é conhecido como o Continente Pokémon.", "attack" : 150, "defense" : 140, "height" : 3.51, "type" : "ground" }
{ "_id" : ObjectId("5643f0722549be4e41d3afe2"), "name" : "Rayquaza", "description" : "Rayquaza é um dragão/ Voador tipo Pokémon introduzida na Geração 3. Ele é conhecido como o Sky High Pokémon.", "attack" : 150,"defense" : 90, "height" : 7.01, "type" : "dragon" }
{ "_id" : ObjectId("5643f07f2549be4e41d3afe3"), "name" : "Deoxys", "description" : "Deoxys é um Psychic Pokémon tipo introduzido na Geração 3. Ele é conhecido como o DNA Pokémon.", "attack" : 150, "defense" : 50, "height" : 1.7, "type" : "psychic" }

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama (* GrassIce *)

> var consulta = {height :{$lte: 0.5}, $and : [{type : "GrassIce"}]}
> db.pokemons.find(consulta)
...

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5

> var consulta = {$or : [{name : "Pikachu"}, {attack : {$lte : 0.5}}]}
> db.pokemons.find(consulta)
...

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5
> var consulta = {$and : [{attack : {$gte : 48}}, {height : {$lte : 0.5}}]}
> db.pokemons.find(consulta)
...

Como o meu é com Pokemons mais fortes e mais altos, fiz tbm com valores maiores, invertendo sempre que > (Menor que) para < (Maior que) e mudei o type para Dragon, ao inves de GrassIce (Grama)

## Liste todos Pokemons com a altura **maior ou igual que** @(menor ou igual que) 0.5 **E** do tipo grama (* dragon *) @( * grama *)

> var consulta = {height :{$gte: 0.5}, $and : [{type : "dragon"}]}
> db.pokemons.find(consulta)

{ "_id" : ObjectId("5643f0722549be4e41d3afe2"), "name" : "Rayquaza", "description" : "Rayquaza é um dragão/ Voador tipo Pokémon introduzida na Geração 3. Ele é conhecido como o Sky High Pokémon.", "attack" : 150,"defense" : 90, "height" : 7.01, "type" : "dragon" }

## Liste todos Pokemons com o name `Pikachu` @('Mewtwo') **OU** com attack **menor ou igual que** 0.5    @(maior ou igual que) 

> var consulta = {$or : [{name : "Mewtwo"}, {attack : {$gte : 0.5}}]}
> db.pokemons.find(consulta)

{ "_id" : ObjectId("5643ef812549be4e41d3afdf"), "name" : "Mewtwo", "description" : "Descrição super, hiper, mega, modificada", "attack" : 110, "defense" : 90, "height" : 2.01, "type" : "psychic" }
{ "_id" : ObjectId("5643f0262549be4e41d3afe0"), "name" : "Heracross", "description" : "Heracross é um Bug / Lutar tipo Pokémon introduzida na Generation 2. É conhecida como o chifre único Pokémon.", "attack" : 125, "defense" : 75, "height" : 1.5, "type" : "Bug" }
{ "_id" : ObjectId("5643f0462549be4e41d3afe1"), "name" : "Groudon", "description" : "Groudon é uma terra Pokémon tipo introduzido na Geração 3. Ele é conhecido como o Continente Pokémon.", "attack" : 150, "defense" : 140, "height" : 3.51, "type" : "ground" }
{ "_id" : ObjectId("5643f0722549be4e41d3afe2"), "name" : "Rayquaza", "description" : "Rayquaza é um dragão/ Voador tipo Pokémon introduzida na Geração 3. Ele é conhecido como o Sky High Pokémon.", "attack" : 150,"defense" : 90, "height" : 7.01, "type" : "dragon" }
{ "_id" : ObjectId("5643f07f2549be4e41d3afe3"), "name" : "Deoxys", "description" : "Deoxys é um Psychic Pokémon tipo introduzido na Geração 3. Ele é conhecido como o DNA Pokémon.", "attack" : 150, "defense" : 50, "height" : 1.7, "type" : "psychic" }

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 150 @(48) **E** com  height **menor ou igual que** @(maior ou igual que ) 0.5. Like a Boss esses aqui.

> var consulta = {$and : [{attack : {$gte : 150}}, {height : {$gte : 0.5}}]}
> db.pokemons.find(consulta)

{ "_id" : ObjectId("5643f0462549be4e41d3afe1"), "name" : "Groudon", "description" : "Groudon é uma terra Pokémon tipo introduzido na Geração 3. Ele é conhecido como o Continente Pokémon.", "attack" : 150, "defense" : 140, "height" : 3.51, "type" : "ground" }
{ "_id" : ObjectId("5643f0722549be4e41d3afe2"), "name" : "Rayquaza", "description" : "Rayquaza é um dragão/ Voador tipo Pokémon introduzida na Geração 3. Ele é conhecido como o Sky High Pokémon.", "attack" : 150, "defense" : 90, "height" : 7.01, "type" : "dragon" }
{ "_id" : ObjectId("5643f07f2549be4e41d3afe3"), "name" : "Deoxys", "description" : "Deoxys é um Psychic Pokémon tipo introduzido na Geração 3. Ele é conhecido como o DNA Pokémon.", "attack" : 150, "defense" : 50, "height" : 1.7, "type" : "psychic" }

