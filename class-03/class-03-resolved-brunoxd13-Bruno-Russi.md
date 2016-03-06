# MongoDb - Aula 03 - Exercício

1. Liste todos Pokemons com a altura **menor que** 0.5;
2. Liste todos Pokemons com a altura **maior ou igual que** 0.5;
3. Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama;
4. Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5;
5. Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5;

## Estrutura

```md
# MongoDB - Aula 03 - Exercício
autor: Bruno Russi Lautenschlager

## Liste todos Pokemons com a altura **menor que** 0.5

> db.pokemons.find()
{ "_id" : ObjectId("56dc9a7a20c79beeb285f0ec"), "name" : "BobMom", "description" : "Pokemon bob marley", "type" : "chapado", "attack" : 420, "defense" : 420, "height" : 4.2 }
{ "_id" : ObjectId("56dc9a7a20c79beeb285f0ed"), "name" : "LockMom", "description" : "Pokemon lock", "type" : "loko", "attack" : 100, "defense" : 10, "height" : 1.3 }
{ "_id" : ObjectId("56dc9a7a20c79beeb285f0ee"), "name" : "SanoMom", "description" : "pokemon sandia saia", "type" : "San", "attack" : 666, "defense" : 978, "height" : 1.9 }
{ "_id" : ObjectId("56dc9a7a20c79beeb285f0ef"), "name" : "OxiMom", "description" : "Pokemom paraiba", "type" : "paraiba", "attack" : 897, "defense" : 784, "height" : 1.6 }
{ "_id" : ObjectId("56dc9a7a20c79beeb285f0f0"), "name" : "chikungunya", "description" : "Passa peste pra geral", "type" : "peste", "attack" : 666, "defense" : 666, "height" : 1.87 }

> var query = {height: {$lt: 0.5}}
> db.pokemons.find(query)

Nothing :(

## Liste todos Pokemons com a altura **maior ou igual que** 0.5

> var query = {height: {$gte: 0.5}}
> db.pokemons.find(query)
{ "_id" : ObjectId("56dc9a7a20c79beeb285f0ec"), "name" : "BobMom", "description" : "Pokemon bob marley", "type" : "chapado", "attack" : 420, "defense" : 420, "height" : 4.2 }
{ "_id" : ObjectId("56dc9a7a20c79beeb285f0ed"), "name" : "LockMom", "description" : "Pokemon lock", "type" : "loko", "attack" : 100, "defense" : 10, "height" : 1.3 }
{ "_id" : ObjectId("56dc9a7a20c79beeb285f0ee"), "name" : "SanoMom", "description" : "pokemon sandia saia", "type" : "San", "attack" : 666, "defense" : 978, "height" : 1.9 }
{ "_id" : ObjectId("56dc9a7a20c79beeb285f0ef"), "name" : "OxiMom", "description" : "Pokemom paraiba", "type" : "paraiba", "attack" : 897, "defense" : 784, "height" : 1.6 }
{ "_id" : ObjectId("56dc9a7a20c79beeb285f0f0"), "name" : "chikungunya", "description" : "Passa peste pra geral", "type" : "peste", "attack" : 666, "defense" : 666, "height" : 1.87 }


## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama

> var query = {$and: [{height: {$lte: 0.5}}, {type: /grama/}]}
> db.pokemons.find(query)
Nothing :(

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5

> var query = {$or: [{attack: {$lte: 0.5}}, {name: /pikachu/i}]}
> db.pokemons.find(query)
Nothing :(

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5

> var query = {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}
> db.pokemons.find(query)
Nothing :(
```
