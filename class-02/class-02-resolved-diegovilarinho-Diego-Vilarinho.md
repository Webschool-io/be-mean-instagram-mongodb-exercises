# MongoDB - Aula 02 - Exercício
autor: Diego Vilarinho

## Criar Database

```
use be-mean-pokemon
switched to db be-mean-pokemon

```

## Listagem de Todas as dbs

```
show dbs
be-mean           → 0.078GB
be-mean-instagram → 0.078GB
local             → 0.078GB
```

## Listagem de todas as collections

```
show collections

```

## Criar cinco pokemons

```
db.pokemons.insert({name:"Bulbasaur", description: "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.", attack: 300, defense:200, height:0.7})

db.pokemons.insert({name:"Charmeleon", description: "Charmeleon mercilessly destroys its foes using its sharp claws", attack: 300, defense: 300, height: 1.1})

db.pokemons.insert({name:"Blastoise", description: "Blastoise has water spouts that protrude from its shell.", attack: 400, defense: 400, height: 1.6})

db.pokemons.insert({name:"Beedrill", description: "Beedrill is extremely territorial. No one should ever approach its nest—this is for their own safety.", attack: 500, defense: 200, height: 1.0})

db.pokemons.insert({name:"Mega Pidgeot", description: "This Pokémon has a dazzling plumage of beautifully glossy feathers.", attack: 400, defense: 400, height: 2.2})

```


## Listar todos os pokemons

```
db.pokemons.find()
{
  "_id": ObjectId("570ab598d05b19f568ad7499"),
  "name": "Bulbasaur",
  "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
  "attack": 300,
  "defense": 200,
  "height": 0.7
}
{
  "_id": ObjectId("570ab698d05b19f568ad749a"),
  "name": "Charmeleon",
  "description": "Charmeleon mercilessly destroys its foes using its sharp claws",
  "attack": 300,
  "defense": 300,
  "height": 1.1
}
{
  "_id": ObjectId("570ab6d7d05b19f568ad749b"),
  "name": "Blastoise",
  "description": "Blastoise has water spouts that protrude from its shell.",
  "attack": 400,
  "defense": 400,
  "height": 1.6
}
{
  "_id": ObjectId("570ab71dd05b19f568ad749c"),
  "name": "Beedrill",
  "description": "Beedrill is extremely territorial. No one should ever approach its nest—this is for their own safety.",
  "attack": 500,
  "defense": 200,
  "height": 1
}
{
  "_id": ObjectId("570ab795d05b19f568ad749d"),
  "name": "Mega Pidgeot",
  "description": "This Pokémon has a dazzling plumage of beautifully glossy feathers.",
  "attack": 400,
  "defense": 400,
  "height": 2.2
}

```

## Buscar um pokemon

```
var query = {name: "Beedrill"}
var poke = db.pokemons.findOne(query)
poke
{
  "_id": ObjectId("570ab71dd05b19f568ad749c"),
  "name": "Beedrill",
  "description": "Beedrill is extremely territorial. No one should ever approach its nest—this is for their own safety.",
  "attack": 500,
  "defense": 200,
  "height": 1
}
```

## Editar a description do pokemon escolhido

```
poke.description = "New description of Beedrill."
New description of Beedrill.

db.pokemons.save(poke)
Updated 1 existing record(s) in 3ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

db.pokemons.findOne(query)
{
  "_id": ObjectId("570ab71dd05b19f568ad749c"),
  "name": "Beedrill",
  "description": "New description of Beedrill.",
  "attack": 500,
  "defense": 200,
  "height": 1
}


```