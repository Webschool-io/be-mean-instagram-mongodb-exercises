# MongoDB - Aula 02 - Exercício
autor: RONEI CHIARANDI

## Criação DB (passo 1)

```
use be-mean-pokemons
switched to db be-mean-pokemons

```

## Listagem das databases (passo 2)

```
show dbs

be-mean              0.078GB
be-mean-instagram    0.078GB
local                0.078GB

```

## Listagem das coleções (passo 3)

```
show collections

```

## Cadastro dos pokemons (passo 4)

```
  var charmander = {'name':'Charmander','description':'Lizard Pokémon','attack': 52,'defense': 43,'height': 0.6}
  var pikachu = {'name':'Pikachu','description':'Mouse Pokémon','attack': 55,'defense': 40,'height': 0.4}
  var onix = {'name':'Onix','description':'Rock Snake Pokémon','attack': 45,'defense': 150,'height': 8.79}
  var charizard = {'name':'Charizard','description':'Flame Pokémon','attack': 84,'defense': 78,'height': 1.7}
  var snorlax = {'name':'Snorlax','description':'Sleeping Pokémon','attack': 110,'defense': 65,'height': 2.1}

  db.pokemons.insert(charmander)
  db.pokemons.insert(pikachu)
  db.pokemons.insert(onix)
  db.pokemons.insert(charizard)
  db.pokemons.insert(snorlax)

```

## Lista dos pokemons (passo 5)

```
db.pokemons.find()
{
  "_id": ObjectId("5648f699808f98084dfb711e"),
  "name": "Charmander",
  "description": "Lizard Pokémon",
  "attack": 52,
  "defense": 43,
  "height": 0.6
}
{
  "_id": ObjectId("5648f699808f98084dfb711f"),
  "name": "Pikachu",
  "description": "Mouse Pokémon",
  "attack": 55,
  "defense": 40,
  "height": 0.4
}
{
  "_id": ObjectId("5648f699808f98084dfb7120"),
  "name": "Onix",
  "description": "Rock Snake Pokémon",
  "attack": 45,
  "defense": 150,
  "height": 8.79
}
{
  "_id": ObjectId("5648f69a808f98084dfb7121"),
  "name": "Charizard",
  "description": "Flame Pokémon",
  "attack": 84,
  "defense": 78,
  "height": 1.7
}
{
  "_id": ObjectId("5648f69a808f98084dfb7122"),
  "name": "Snorlax",
  "description": "Sleeping Pokémon",
  "attack": 110,
  "defense": 65,
  "height": 2.1
}
Fetched 5 record(s) in 3ms

```

## Pikachu (passo 6)

```
var q = {name: "Pikachu"}
db.pokemons.find(q)
{
  "_id": ObjectId("5648f699808f98084dfb711f"),
  "name": "Pikachu",
  "description": "Mouse Pokémon",
  "attack": 55,
  "defense": 40,
  "height": 0.4
}
Fetched 1 record(s) in 1ms

```

## Atualização do Pikachu (passo 6)

```
var q = {name: "Pikachu"}
var pokemon = db.pokemons.findOne(q)

pokemon
{
  "_id": ObjectId("5648f699808f98084dfb711f"),
  "name": "Pikachu",
  "description": "Mouse Pokémon",
  "attack": 55,
  "defense": 40,
  "height": 0.4
}

pokemon.description = "Yellow Mouse Pokémon"
Yellow Mouse Pokémon

db.pokemons.save(pokemon)
Updated 1 existing record(s) in 5ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

```
