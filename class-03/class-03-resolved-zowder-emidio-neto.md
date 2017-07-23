# MongoDB - Aula 03 - Exercício
autor: Emídio de Paiva Neto

## Liste todos Pokemons com a altura **menor que** 0.5;

```
ubuntu(mongod-3.0.7) be-mean-pokemons> var altura = {height: {$lt: 0.5}}
ubuntu(mongod-3.0.7) be-mean-pokemons> db.savepokemons.find(altura)
{
  "_id": ObjectId("566365c797534bcf952d5738"),
  "name": "Raichu",
  "description": "Irmão do Pikachu",
  "type": "electric",
  "attack": 110,
  "defense": 90,
  "height": 0.3
}
Fetched 1 record(s) in 0ms
```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5

```
ubuntu(mongod-3.0.7) be-mean-pokemons> var altura = {height: {$gte: 0.5}}
ubuntu(mongod-3.0.7) be-mean-pokemons> db.savepokemons.find(altura)
{
  "_id": ObjectId("566365c797534bcf952d5735"),
  "name": "Wartotle",
  "description": "Os arranhões na sua concha são a prova de resistência deste Pokémon como um combatente.",
  "type": "water",
  "attack": "90",
  "defense": "40",
  "height": 1
}
{
  "_id": ObjectId("566365c797534bcf952d5736"),
  "name": "Charizard",
  "description": "Respira fogo que derrete qualquer coisa",
  "type": "fire",
  "attack": 80,
  "defense": 60,
  "height": 1.7
}
{
  "_id": ObjectId("566365c797534bcf952d5737"),
  "name": "Vulpix",
  "description": "Possui umas caudas muito loucas",
  "type": "fire",
  "attack": 60,
  "defense": 40,
  "height": 0.6
}
{
  "_id": ObjectId("566365c797534bcf952d5739"),
  "name": "Blastoise",
  "description": "Blastoise tem bicas de água que se projetam de sua concha.",
  "type": "water",
  "attack": "110",
  "defense": 65,
  "height": 1.6
}

```

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama

```
ubuntu(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{height: {$lte: 0.5}}, {type: "grama"}]}
ubuntu(mongod-3.0.7) be-mean-pokemons> db.savepokemons.find(query)
Fetched 0 record(s) in 0ms

```

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5


```
ubuntu(mongod-3.0.7) pokemons> var query = {$or: [{name: "Pikachu"}, {attack: {$lte: 0.5}}]}
ubuntu(mongod-3.0.7) pokemons> db.pokemons.find(query)

{
  "_id": ObjectId("56634d1a7b3e97e09347bc77"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 100,
  "height": 0.4
}
Fetched 1 record(s) in 2ms

```

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5

```
ubuntu(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{height: {$lte: 0.5}}, {attack: {$gte: 48}}]}
ubuntu(mongod-3.0.7) be-mean-pokemons> db.savepokemons.find(query)
{
  "_id": ObjectId("566365c797534bcf952d5738"),
  "name": "Raichu",
  "description": "Irmão do Pikachu",
  "type": "electric",
  "attack": 110,
  "defense": 90,
  "height": 0.3
}
Fetched 1 record(s) in 1ms
```
