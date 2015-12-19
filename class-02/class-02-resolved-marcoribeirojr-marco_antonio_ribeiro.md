# MongoDB - Aula 02 - Exercício
autor: Marco Antonio Ribeiro (https://github.com/marcoribeirojr)

## Criar a Database be-mean-pokemons
```
mongo be-mean-pokemons  
MongoDB shell version: 2.6.10
connecting to: be-mean-pokemons
Mongo-Hacker 0.0.9
```  
## Listar as databases do servidor

```
show dbs
local             → 0.078GB
be-mean-instagram → 0.078GB
admin             → (empty)
be-mean-pokemons  → (empty)

```
## Listar as collections

```
show collections

```
## Adicionar os pokemons

```
var pokemons = [
     {'name' : 'Feraligatr', 'description' : 'Great Crocodile', 'type' : 'Water', 'attack' : 105, 'defense' : 100, height: 23},
     {'name' : 'Scizor', 'description' : 'Insect of Metal', 'type' : 'Bug/Steel', 'attack' : 130, 'defense' : 100, height: 18},
     {'name' : 'Salamence', 'description' : 'A Dragon', 'type' : 'Flying/Dragon', 'attack' : 135, 'defense' : 80, height: 15},
     {'name' : 'Charizard', 'description' : 'Fire breathing and flying lizard', 'type' : 'Flying/Fire', 'attack' : 84, 'defense' : 78, height: 17},
     {'name' : 'Alakazam', 'description' : 'Hungry, always with two spoons', 'type' : 'Psychic', 'attack' : 50, 'defense' : 45, height: 15},
     {'name' : 'Tyranitar', 'description' : 'Looks like Godzilla a lil bit', 'type' : 'Rock/Dark', 'attack' : 134, 'defense' : 110, height: 20},
     {'name' : 'Lugia', 'description' : 'Lendary big bird', 'type' : 'Flying/Psychic', 'attack' : 90, 'defense' : 130, height: 52},
     {'name' : 'Rayquaza', 'description' : 'Lendary motherfucker dragon', 'type' : 'Flying/Dragon', 'attack' : 150, 'defense' : 90, height: 70}
   ]

db.pokemons.save(pokemons)
Inserted 1 record(s) in 377ms
BulkWriteResult({
  "writeErrors": [ ],
  "writeConcernErrors": [ ],
  "nInserted": 8,
  "nUpserted": 0,
  "nMatched": 0,
  "nModified": 0,
  "nRemoved": 0,
  "upserted": [ ]
})

```
## Listar todos os pokemons da collections

```
db.pokemons.find()
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
  "description": "Hungry, always with two spoons",
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
Fetched 8 record(s) in 6ms
```
## Buscar um pokemon de acordo com minha escolha

```
var query = {name : "Alakazam"}
var poke = db.pokemons.findOne(query)
poke
{
  "_id": ObjectId("5654a75bfce2889eeb597084"),
  "name": "Alakazam",
  "description": "Hungry, always with two spoons",
  "type": "Psychic",
  "attack": 50,
  "defense": 45,
  "height": 15
}
```
## Alterando a description
```
poke.description = "Changed - Hungry, always with two spoons"
Changed - Hungry, always with two spoons

poke
{
  "_id": ObjectId("5654a75bfce2889eeb597084"),
  "name": "Alakazam",
  "description": "Changed - Hungry, always with two spoons",
  "type": "Psychic",
  "attack": 50,
  "defense": 45,
  "height": 15
}

db.pokemons.save(poke)
Updated 1 existing record(s) in 39ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})


```
