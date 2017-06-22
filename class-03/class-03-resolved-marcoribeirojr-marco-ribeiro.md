# MongoDB - Aula 03 - Exercício
autor: Marco Ribeiro (https://github.com/marcoribeirojr)

## Exercício 1 - Listar os pokemons com altura menor que 0.5

```
var query = {height:{$lt:0.5}}
db.pokemons.find(query)
Fetched 0 record(s) in 0ms

```
## Exercício 2 - Listar os pokemons com altura maior ou igual que 0.5

```
var query = {height:{$gte:0.5}}
db.pokemons.find(query)
{
  "_id": ObjectId("5654a75bfce2889eeb597080"),
  "name": "Feraligatr",
  "description": "Great Crocodile",
  "type": "Water",
  "attack": 105,
  "defense": 100,
  "height": 23
}
{
  "_id": ObjectId("5654a75bfce2889eeb597081"),
  "name": "Scizor",
  "description": "Insect of Metal",
  "type": "Bug/Steel",
  "attack": 130,
  "defense": 100,
  "height": 18
}
{
  "_id": ObjectId("5654a75bfce2889eeb597082"),
  "name": "Salamence",
  "description": "A Dragon...",
  "type": "Flying/Dragon",
  "attack": 135,
  "defense": 80,
  "height": 15
}
{
  "_id": ObjectId("5654a75bfce2889eeb597083"),
  "name": "Charizard",
  "description": "Fire breathing and flying lizard",
  "type": "Flying/Fire",
  "attack": 84,
  "defense": 78,
  "height": 17
}
{
  "_id": ObjectId("5654a75bfce2889eeb597084"),
  "name": "Alakazam",
  "description": "Changed - Hungry, always with two spoons",
  "type": "Psychic",
  "attack": 50,
  "defense": 45,
  "height": 15
}
{
  "_id": ObjectId("5654a75bfce2889eeb597085"),
  "name": "Tyranitar",
  "description": "Looks like Godzilla a lil bit",
  "type": "Rock/Dark",
  "attack": 134,
  "defense": 110,
  "height": 20
}
{
  "_id": ObjectId("5654a75bfce2889eeb597086"),
  "name": "Lugia",
  "description": "Lendary big bird",
  "type": "Flying/Psychic",
  "attack": 90,
  "defense": 130,
  "height": 52
}
{
  "_id": ObjectId("5654a75bfce2889eeb597087"),
  "name": "Rayquaza",
  "description": "Lendary motherfucker dragon",
  "type": "Flying/Dragon",
  "attack": 150,
  "defense": 90,
  "height": 70
}
Fetched 8 record(s) in 4ms

```
## Exercício 3 - Listar os pokemons com altura menor ou igual que 0.5  do tipo grama
```
var query = {$and: [{height:{$gte:0.5}},{type:"grama"}]}
db.pokemons.find(query)
Fetched 0 record(s) in 1ms
```
## Exercício 4 - Listar os pokemons com name "Pikachu" ou attack menor ou igual que 0.5

```
var query = {$or: [{name:"Pikachu"},{attack:{$lte:0.5}}]}
db.pokemons.find(query)
Fetched 0 record(s) in 1ms

```
## Exercício 5 - Listar todos os pokemons attack maior ou igual que 48 e com height menor ou igual que 0.5

```
var query = {$and: [{height:{$lte:0.5}},{attack:{$gte:48}}]}
db.pokemons.find(query)
Fetched 0 record(s) in 0ms

```
