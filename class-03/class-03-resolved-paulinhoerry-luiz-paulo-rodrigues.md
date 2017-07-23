# MongoDb - Aula 03 - Exercício

1. Liste todos Pokemons com a altura **menor que** 0.5;
2. Liste todos Pokemons com a altura **maior ou igual que** 0.5;
3. Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama;
4. Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5;
5. Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5;

## Estrutura

```md
# MongoDB - Aula 03 - Exercício
autor: **Luiz Paulo Rodrigues**

## Liste todos Pokemons com a altura **menor que** 0.5

var query = {height: {$lt: 0.5}}
db.pokemons.find(query)
{ "_id" : ObjectId("566739103becf421d1f1e500"), "name" : "Caterpie", "description" : "Caterpie has a voracious appetite", "type" : "bug", "attack" : 30, "defense" : 35, "height" : 0.3 }

## Liste todos Pokemons com a altura **maior ou igual que** 0.5

var query = {height: {$gte: 0.5} }
db.pokemons.find(query)
{ "_id" : ObjectId("5664fd4ef1c1c94fcaca1f8a"), "name" : "charizard", "description" : "flies around the sky in search of powerful opponents", "type" : "fire", "attack" : 84, "defense" : 78, "height" : 17 }
{ "_id" : ObjectId("5664fd80f1c1c94fcaca1f8b"), "name" : "nidoking", "description" : "Drilthick tail packs enormously destructive power", "type" : "poison", "attack" : 102, "defense" : 77, "height" : 14 }
{ "_id" : ObjectId("5664fd96f1c1c94fcaca1f8c"), "name" : "ninetales", "description" : "Casts a sinister light from its bright red eyes to gain total control over its foe's mind", "type" : "fire", "attack" : 76, "defense" : 75, "height" : 11 }
{ "_id" : ObjectId("5664fda3f1c1c94fcaca1f8d"), "name" : "arcanine", "description" : "fast, stronger and fire", "type" : "fire", "attack" : 110, "defense" : 80, "height" : 19 }
{ "_id" : ObjectId("5664fdb4f1c1c94fcaca1f8e"), "name" : "gyarados", "description" : "its brain cells undergo a structural transformation", "type" : "water", "attack" : 125, "defense" : 79, "height" : 65 }
{ "_id" : ObjectId("5664fdc8f1c1c94fcaca1f8f"), "name" : "articuno", "description" : "Is a legendary bird Pokémon that can control ice.", "type" : "ice", "attack" : 85, "defense" : 100, "height" : 17 }
{ "_id" : ObjectId("56673dcc3becf421d1f1e501"), "name" : "Pikachu", "description" : "Electric mouse", "type" : "electric", "attack" : 55, "defense" : 40, "height" : 4 }


## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo inseto

var query = {$and: [ {height: {$lte: 0.5}},{type: "bug"} ] }
db.pokemons.find(query)
{ "_id" : ObjectId("566739103becf421d1f1e500"), "name" : "Caterpie", "description" : "Caterpie has a voracious appetite", "type" : "bug", "attack" : 30, "defense" : 35, "height" : 0.3 }


## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5

var query = {$or: [{name: "Pikachu"}, {attack: {$lte: 0.5}}]}
db.pokemons.find(query)
{ "_id" : ObjectId("56673dcc3becf421d1f1e501"), "name" : "Pikachu", "description" : "Electric mouse", "type" : "electric", "attack" : 55, "defense" : 40, "height" : 4 }


## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5

var query = {$and: [ {attack: {$gte: 48}},{height: {$lte: 0.5}} ] }
db.pokemons.find(query)
{ "_id" : ObjectId("56673fb83becf421d1f1e502"), "name" : "Ratata", "description" : "Mouse crazy", "type" : "normal", "attack" : 56, "defense" : 35, "height" : 0.3 }
		
```
