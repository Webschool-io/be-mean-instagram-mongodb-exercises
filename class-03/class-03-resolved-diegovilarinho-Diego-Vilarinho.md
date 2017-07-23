# MongoDB - Aula 03 - Exercício
autor: Diego Vilarinho

## Selecionando o banco be-mean-pokemons criado na aula 02 

```
use be-mean-pokemon
switched to db be-mean-pokemon

```

## Listagem de todos os Pokemons com a altura menor que 0.5 

```
var query = {height: {$lt: 0.5}}
db.pokemons.find(query)
{
  "_id": ObjectId("570bb48fb3b076c76964aaec"),
  "name": "Pikachu",
  "Description": "Rato Elétrico que voçê nao vai querer ver puto!",
  "attack": 30,
  "defense": 20,
  "height": 0.4,
  "type": "elétrico",
  "moves": [
    "investida",
    "recuar",
    "desvio"
  ]
}

```

## Listagem de todos os Pokemons com a altura maior ou igual que 0.5

```
var query = {height: {$gte: 0.5}}
db.pokemons.find(query)
{
  "_id": ObjectId("570ab598d05b19f568ad7499"),
  "name": "Bulbasaur",
  "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
  "attack": 30,
  "defense": 20,
  "height": 0.7,
  "type": "grama",
  "moves": [
    "investida",
    "recuar",
    "desvio"
  ]
}
{
  "_id": ObjectId("570ab71dd05b19f568ad749c"),
  "name": "Beedrill",
  "description": "New description of Beedrill.",
  "attack": 50,
  "defense": 20,
  "height": 1,
  "type": "inseto",
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("570ab795d05b19f568ad749d"),
  "name": "Mega Pidgeot",
  "description": "This Pokémon has a dazzling plumage of beautifully glossy feathers.",
  "attack": 40,
  "defense": 40,
  "height": 2.2,
  "type": "voador",
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("570ab698d05b19f568ad749a"),
  "name": "Charmeleon",
  "description": "Charmeleon mercilessly destroys its foes using its sharp claws",
  "attack": 30,
  "defense": 30,
  "height": 1.1,
  "type": "fogo",
  "moves": [
    "investida",
    "recuar",
    "desvio"
  ]
}

```

## Listagem de todos os Pokemons com a altura menor ou igual que 0.5 **E** do tipo grama

```
var query = {$and: [{height: {$gte: 0.5}}, {type: /grama/i}]}
db.pokemons.find(query)
{
  "_id": ObjectId("570ab598d05b19f568ad7499"),
  "name": "Bulbasaur",
  "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
  "attack": 30,
  "defense": 20,
  "height": 0.7,
  "type": "grama",
  "moves": [
    "investida",
    "recuar",
    "desvio"
  ]
}

```

## Listagem de todos os Pokemons com o nome Pikachu **OU** com attack menor ou igual que 0.5

```
var query = {$or: [{attack: {$lte: 0.5}}, {name: /pikachu/i}]}
db.pokemons.find(query)
{
  "_id": ObjectId("570bb48fb3b076c76964aaec"),
  "name": "Pikachu",
  "Description": "Rato Elétrico que voçê nao vai querer ver puto!",
  "attack": 30,
  "defense": 20,
  "height": 0.4,
  "type": "elétrico",
  "moves": [
    "investida",
    "recuar",
    "desvio"
  ]
}

```

## Listagem de todos os Pokemons com o attack maior ou igual que 48 **E** com height menor ou igual que 0.5

```
var query = {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}
db.pokemons.find(query)
Fetched 0 record(s) in 1ms

```