# MongoDB - Aula 02 - Exercício
autor: Aguinaldo Alves Barbosa Silva

## Crie uma database chamada be-mean-pokemons;

```
MacBook-Pro-de-Aguinaldo(mongod-3.1.9) be-mean-instagram> use be-mean-pokemons
switched to db be-mean-pokemons

```
## 2. Liste quais databases você possui nesse servidor;

```
MacBook-Pro-de-Aguinaldo(mongod-3.1.9) be-mean-pokemons> show dbs
be-mean           → 0.004GB
be-mean-instagram → 0.000GB
local             → 0.000GB

```


## 3. Liste quais coleções você possui nessa database;
```
MacBook-Pro-de-Aguinaldo(mongod-3.1.9) be-mean-pokemons> show collections
pokemons → 0.000MB / 0.004MB

```

## 4. Insira pelo menos 5 pokemons A SUA ESCOLHA
```
var pk = {"name": "Bulbasaur", "description" :"Bulbasaur is a small quadruped", "type":"grass", "attack":49, "defense":49 }
MacBook-Pro-de-Aguinaldo(mongod-3.1.9) be-mean-pokemons> db.pokemons.save(pk)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})


var pk = {"name":"Ivysaur", "description" :"Ivysaur is a quadruped Pokémon similar to a dinosaur.", "type":"grass", "attack":62, "defense":63}
MacBook-Pro-de-Aguinaldo(mongod-3.1.9) be-mean-pokemons> db.pokemons.save(pk)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})

var pk = {"name":"Venusaur", "description" :"Venusaur is a squat quadruped Pokémon with bumpy bluish green skin","type":"grass","attack":82,"defense":83}
MacBook-Pro-de-Aguinaldo(mongod-3.1.9) be-mean-pokemons> db.pokemons.save(pk)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})

var pk = {"name":"Charmeleon", "description" :"Charmeleon is a bipedal reptilian creature. It has crimson scales and a cream underside. " ,"type":"fire", "attack":64,"evolveTo":"6"}
MacBook-Pro-de-Aguinaldo(mongod-3.1.9) be-mean-pokemons> db.pokemons.save(pk)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})
var pk = {"name":"Goldeen", "description" :"Goldeen is a white, fish-like Pokémon with orange markings on its tail, back, and fins.","type":"water", "attack":67,"defense":60}
MacBook-Pro-de-Aguinaldo(mongod-3.1.9) be-mean-pokemons> db.pokemons.save(pk)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})
```

## 5. Liste os pokemons existentes na sua coleção;
```

{
  "_id": ObjectId("5653a41a8fcd0c51644156e6"),
  "name": "Pikachu",
  "description": "Rato Eletrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("5653a4688fcd0c51644156e7"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("5653a4b08fcd0c51644156e8"),
  "name": "Chamander",
  "description": "Este é  o cão chupando manda de fofinho ",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("5653a50e8fcd0c51644156e9"),
  "name": "Caterpiee",
  "description": "Larva lutadora ",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35
}
{
  "_id": ObjectId("5653a5358fcd0c51644156ea"),
  "name": "Squirtle",
  "description": "Ejata água que passarinho não bebe ",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
{
  "_id": ObjectId("5653abd68fcd0c51644156eb"),
  "name": "Bulbasaur",
  "description": "Bulbasaur is a small quadruped",
  "type": "grass",
  "attack": 49,
  "defense": 49
}
{
  "_id": ObjectId("5653ac0f8fcd0c51644156ec"),
  "name": "Ivysaur",
  "description": "Ivysaur is a quadruped Pokémon similar to a dinosaur.",
  "type": "grass",
  "attack": 62,
  "defense": 63
}
{
  "_id": ObjectId("5653ac438fcd0c51644156ed"),
  "name": "Venusaur",
  "description": "Venusaur is a squat quadruped Pokémon with bumpy bluish green skin",
  "type": "grass",
  "attack": 82,
  "defense": 83
}
{
  "_id": ObjectId("5653ac778fcd0c51644156ee"),
  "name": "Charmeleon",
  "description": "Charmeleon is a bipedal reptilian creature. It has crimson scales and a cream underside. ",
  "type": "fire",
  "attack": 64,
  "evolveTo": "6"
}
{
  "_id": ObjectId("5653ad388fcd0c51644156ef"),
  "name": "Goldeen",
  "description": "Goldeen is a white, fish-like Pokémon with orange markings on its tail, back, and fins.",
  "type": "water",
  "attack": 67,
  "defense": 60
}
Fetched 10 record(s) in 6ms
```

## 6. Busque o pokemons a sua escolha, pelo nome, e armazene-o em uma variável chamada `poke`;
```
var poke = {name: 'Ivysaur'}
MacBook-Pro-de-Aguinaldo(mongod-3.1.9) be-mean-pokemons> db.pokemons.findOne(poke)
{
  "_id": ObjectId("5653ac0f8fcd0c51644156ec"),
  "name": "Ivysaur",
  "description": "Ivysaur is a quadruped Pokémon similar to a dinosaur.",
  "type": "grass",
  "attack": 62,
  "defense": 63
}

```

## 7. Modifique sua `description` e salvê-o
```
MacBook-Pro-de-Aguinaldo(mongod-3.1.9) be-mean-pokemons> var poke = db.pokemons.findOne(poke)
MacBook-Pro-de-Aguinaldo(mongod-3.1.9) be-mean-pokemons> poke.description = 'description changes  kkkk'
description changes  kkkk
MacBook-Pro-de-Aguinaldo(mongod-3.1.9) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 3ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})


```