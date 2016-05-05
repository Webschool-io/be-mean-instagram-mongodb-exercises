# MongoDB - Aula 01 - Exercício
Autor: Igor luíz

## Criando database __be-mean-pokemons__

```sh
localhost(mongod-3.0.8) test> use be-mean-pokemons
switched to db be-mean-pokemons
```

## Listando databases

```sh
localhost(mongod-3.0.8) be-mean-pokemons> show dbs
be-mean           → 0.078GB
be-mean-instagram → 0.078GB
local             → 0.078GB
```

## Listando todas as collections

```sh
localhost(mongod-3.0.8) be-mean-pokemons> show collections
localhost(mongod-3.0.8) be-mean-pokemons>
```

## Adicionando 5 pokemons

```sh
localhost(mongod-3.0.8) be-mean-pokemons> db.pokemons.insert({name: "Charmander", description: "pokemon de fogo lokão", type: "fogo", attack: 45, defense: 49, height: 0.6})
Inserted 1 record(s) in 466ms
WriteResult({
  "nInserted": 1
})
localhost(mongod-3.0.8) be-mean-pokemons> db.pokemons.insert({name: "Ivysaur", description: "bananeira ambulante, porém muito habilidoso", type: "grama",attack: 50, defense: 50, height: 1.0})
Inserted 1 record(s) in 3ms
WriteResult({
  "nInserted": 1
})
localhost(mongod-3.0.8) be-mean-pokemons> db.pokemons.insert({name: "Blastoise", description: "pokemon 'Vem monstro!'", type: "agua", attack: 60, defense: 60, height: 1.6})
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})
localhost(mongod-3.0.8) be-mean-pokemons> db.pokemons.insert({name: "Butterfree", description: "pokemon 'cuti cuti'", type: "voador", attack: 35, defense: 40, height: 1.1})
Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})
localhost(mongod-3.0.8) be-mean-pokemons> db.pokemons.insert({name: "Pidgeotto", description: "O que voa e bota moral", type: "voador", attack: 40, defense: 35, height: 1.1})
Inserted 1 record(s) in 3ms
WriteResult({
  "nInserted": 1
})
localhost(mongod-3.0.8) be-mean-pokemons> db.pokemons.insert({name: "Ninetales", description: "O que tem nove caldas", type: "fogo", attack: 50, defense: 40, height: 1.1})
Inserted 1 record(s) in 3ms
WriteResult({
  "nInserted": 1
})
localhost(mongod-3.0.8) be-mean-pokemons> db.pokemons.insert({name: "Psyduck", description: "Fica doidão, aí solta o poder", type: "agua", attack: 35, defense: 30, height: 0.8})
Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})
```

## Listando pokemons

```sh
localhost(mongod-3.0.8) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("56b137c521f82f17b072ce4e"),
  "name": "Charmander",
  "description": "pokemon de fogo mais que lokão!!!",
  "attack": 45,
  "defense": 49,
  "height": 0.6,
  "type": "fogo"
}
{
  "_id": ObjectId("56b1385b21f82f17b072ce4f"),
  "name": "Ivysaur",
  "description": "bananeira ambulante, porém muito habilidoso",
  "attack": 50,
  "defense": 50,
  "height": 1,
  "type": "grama"
}
{
  "_id": ObjectId("56b1390d21f82f17b072ce50"),
  "name": "Blastoise",
  "description": "pokemon 'Vem monstro!'",
  "attack": 60,
  "defense": 60,
  "height": 1.6,
  "type": "agua"
}
{
  "_id": ObjectId("56b139e721f82f17b072ce51"),
  "name": "Butterfree",
  "description": "pokemon 'cuti cuti'",
  "attack": 35,
  "defense": 40,
  "height": 1.1,
  "type": "voador"
}
{
  "_id": ObjectId("56b13a4d21f82f17b072ce52"),
  "name": "Pidgeotto",
  "description": "O que voa e bota moral",
  "attack": 40,
  "defense": 35,
  "height": 1.1,
  "type": "voador"
}
{
  "_id": ObjectId("56b13ad721f82f17b072ce53"),
  "name": "Ninetales",
  "description": "O que tem nove caldas",
  "attack": 50,
  "defense": 50,
  "height": 1.1,
  "type": "fogo"
}
{
  "_id": ObjectId("56b13b3721f82f17b072ce54"),
  "name": "Psyduck",
  "description": "Fica doidão, aí solta o poder",
  "attack": 35,
  "defense": 30,
  "height": 0.8,
  "type": "agua"
}
{
  "_id": ObjectId("56b173ecf3bf0cb1edd0f06d"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("56b1741cf3bf0cb1edd0f06e"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "agua",
  "attack": 48,
  "height": 0.5,
  "defense": 37
}
{
  "_id": ObjectId("56b17446f3bf0cb1edd0f06f"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletrico",
  "attack": 55,
  "height": 0.4,
  "defense": 50
}
Fetched 10 record(s) in 2ms
```

## Buscar um pokemon e armazenar em poke

```sh
localhost(mongod-3.0.8) be-mean-pokemons> var poke = db.pokemons.findOne({name:'Charmander'})
localhost(mongod-3.0.8) be-mean-pokemons> poke
{
  "_id": ObjectId("56b137c521f82f17b072ce4e"),
  "name": "Charmander",
  "description": "pokemon de fogo lokão",
  "type": "fogo"
  "attack": 45,
  "defense": 49,
  "height": 0.6
}
Fetched 1 record(s) in 28ms
```

## Modificando o __description__ e salvando

```sh
localhost(mongod-3.0.8) be-mean-pokemons> poke.description = "pokemon de fogo mais que lokão!!!"
pokemon de fogo mais que lokão!!!
localhost(mongod-3.0.8) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 21ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```
