# MongoDB - Aula 03 - Exercício
autor: Bruno Russi Lautenschlager

## 1- lista todos pokemons com altura menor que 0.5;
```
> var query = {height: {$lt: 0.5}}
> db.pokemons.find(query)
{ "_id" : ObjectId("56dcbe46874e289e60d249c0"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 55, "height" : 0.4 }
{ "_id" : ObjectId("56dcbe9c874e289e60d249c1"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4 }
```
## 2- lista todos pokemons com altura maior ou igual a 0.5;
```
> var query = {height: {$gte: 0.5}}
> db.pokemons.find(query)
{ "_id" : ObjectId("56dc9a7a20c79beeb285f0ec"), "name" : "BobMom", "description" : "Pokemon bob marley", "type" : "chapado", "attack" : 420, "defense" : 420, "height" : 4.2 }
{ "_id" : ObjectId("56dc9a7a20c79beeb285f0ed"), "name" : "LockMom", "description" : "Pokemon lock", "type" : "loko", "attack" : 100, "defense" : 10, "height" : 1.3 }
{ "_id" : ObjectId("56dc9a7a20c79beeb285f0ee"), "name" : "SanoMom", "description" : "pokemon sandia saia", "type" : "San", "attack" : 666, "defense" : 978, "height" : 1.9 }
{ "_id" : ObjectId("56dc9a7a20c79beeb285f0ef"), "name" : "OxiMom", "description" : "Pokemom paraiba", "type" : "paraiba", "attack" : 897, "defense" : 784, "height" : 1.6 }
{ "_id" : ObjectId("56dc9a7a20c79beeb285f0f0"), "name" : "chikungunya", "description" : "Passa peste pra geral", "type" : "peste", "attack" : 666, "defense" : 666, "height" : 1.87 }
{ "_id" : ObjectId("56dcbeaf874e289e60d249c2"), "name" : "Charmander", "description" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6 }
{ "_id" : ObjectId("56dcbfa4874e289e60d249c3"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5 }
```
## 3- lista todos pokemons com altura menor ou igual a 0.5 e do tipo grama;   
```
> var query = {$and: [{height: {$lte: 0.5}}, {type: /grama/}]}
> db.pokemons.find(query)
{ "_id" : ObjectId("56dcbe9c874e289e60d249c1"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4 }
```
## 4- lista todos pokemons com o nome pikachu ou com atack menor ou igual a 0.5
```
> var query = {$or: [{attack: {$lte: 0.5}}, {name: /pikachu/i}]}
> db.pokemons.find(query)
{ "_id" : ObjectId("56dcbe46874e289e60d249c0"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 55, "height" : 0.4 }
```   
## 5- lista todos pokemons com o atack maior ou igual que 48 e com height menor ou igual que 0.5
```
> var query = {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}
> db.pokemons.find(query)
Nothing :(
```
