## MongoDb - Aula 03 - Exercício

Autor: Henrique Ferraz

## Exercício - 03.1

```
> var query = {height: {$lt: 0.5}}
> db.pokemons.find(query)
{ "_id" : ObjectId("5901e7812a5b13c09de316f4"), "name" : "Rattata", "description" : "Pokemon tipo 1", "types" : "normal", "attack" : 56, "defense" : 35, "height" : 0.3 }
> 
```

## Exercício - 03.2

```
> var query = {height: {$gte: 0.5}}
> db.pokemons.find(query)
{ "_id" : ObjectId("5901e7812a5b13c09de316f5"), "name" : "Charmander", "description" : "Pokemon com nova descrição", "types" : "fire", "attack" : 52, "defense" : 43, "height" : 0.5 }
{ "_id" : ObjectId("5901e7812a5b13c09de316f6"), "name" : "Charmeleon", "description" : "Pokemon tipo 2", "types" : "fire", "attack" : 64, "defense" : 58, "height" : 11 }
{ "_id" : ObjectId("5901e7812a5b13c09de316f7"), "name" : "Wartortle", "description" : "Pokemon tipo 3", "types" : "water", "attack" : 63, "defense" : 80, "height" : 10 }
{ "_id" : ObjectId("5901e7812a5b13c09de316f8"), "name" : "Blastoise", "description" : "Pokemon tipo 4", "types" : "water", "attack" : 83, "defense" : 100, "height" : 16 }
{ "_id" : ObjectId("5901e7812a5b13c09de316f9"), "name" : "Caterpie", "description" : "Pokemon tipo 5", "types" : "bug", "attack" : 30, "defense" : 35, "height" : 3 }
{ "_id" : ObjectId("5901e7812a5b13c09de316fa"), "name" : "Metapod", "description" : "Pokemon tipo 6", "types" : "bug", "attack" : 20, "defense" : 55, "height" : 7 }
{ "_id" : ObjectId("5901e7812a5b13c09de316fb"), "name" : "Butterfree", "description" : "Pokemon tipo 7", "types" : "flying", "attack" : 45, "defense" : 50, "height" : 11 }
> 

```
## Exercício - 03.3

```
> var query = {$and: [{height: {$gte: 0.5}}, {types: "grama"}]}
> db.pokemons.find(query)
{ "_id" : ObjectId("5901e7812a5b13c09de316f9"), "name" : "Caterpie", "description" : "Pokemon tipo 5", "types" : "grama", "attack" : 30, "defense" : 35, "height" : 3 }
> 

```
## Exercício - 03.4

```
> var query = {$or: [{attack: {$lte: 0.5}}, {name: "Pikachu"}]}
> db.pokemons.find(query)
{ "_id" : ObjectId("5901e7812a5b13c09de316f7"), "name" : "Pikachu", "description" : "Pokemon tipo 3", "types" : "water", "attack" : 63, "defense" : 80, "height" : 10 }
```
## Exercício - 03.5

```
> var query = {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}
> db.pokemons.find(query)
{ "_id" : ObjectId("5901e7812a5b13c09de316f4"), "name" : "Rattata", "description" : "Pokemon tipo 1", "types" : "grama", "attack" : 56, "defense" : 35, "height" : 0.3 }
{ "_id" : ObjectId("5901e7812a5b13c09de316f5"), "name" : "Charmander", "description" : "Pokemon com nova descrição", "types" : "fire", "attack" : 52, "defense" : 43, "height" : 0.5 }
> 

```