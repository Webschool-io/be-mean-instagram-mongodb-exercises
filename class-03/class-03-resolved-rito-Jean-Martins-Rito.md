# MongoDB - Aula 03 - Exercício
autor: Jean Martins Rito
gitHub: http://github.com/rito

## Liste todos Pokemons com a altura **menor que** 0.5;
```
var query = {height: {$lt: 0.5}}
db.pokemons.find(query)

db.pokemons.find(query)
Fetched 0 record(s) in 45ms
Mockingjay(mongod-3.0.7) be-mean-pokemons>


```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5

```
var query = {height: {$gte: 0.5}}
Mockingjay(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56439131e25bbeb0b9427a5f"),
  "name": "Sandslash",
  "description": "Sandslash's body is covered by tough spikes, which are hardened sections of its hide. Once a year, the old spikes fall out, to be replaced with new spikes that grow out from beneath the old ones.",
  "attack": 45,
  "defense": 55,
  "height": 1
}
{
  "_id": ObjectId("56439131e25bbeb0b9427a60"),
  "name": "Nidoking",
  "description": "Nidoking's thick tail packs enormously destructive power. With one swing, it can topple a metal transmission tower. Once this Pokémon goes on a rampage, there is no stopping it.",
  "attack": 85,
  "defense": 75,
  "height": 1.4
}
{
  "_id": ObjectId("56439131e25bbeb0b9427a61"),
  "name": "Clefable",
  "description": "Clefable moves by skipping lightly as if it were flying using its wings. Its bouncy step lets it even walk on water. It is known to take strolls on lakes on quiet, moonlit nights.",
  "attack": 95,
  "defense": 90,
  "height": 1.3
}
{
  "_id": ObjectId("56439131e25bbeb0b9427a62"),
  "name": "Ninetales",
  "description": "Ninetales casts a sinister light from its bright red eyes to gain total control over its foe's mind. This Pokémon is said to live for a thousand years.",
  "attack": 81,
  "defense": 100,
  "height": 1.1
}
{
  "_id": ObjectId("56439131e25bbeb0b9427a64"),
  "name": "Greninja",
  "description": "It creates throwing stars out of compressed water. When it spins them and throws them at high speed, these stars can split metal in two.",
  "attack": 95,
  "defense": 67,
  "height": 1.5
}
{
  "_id": ObjectId("56439131e25bbeb0b9427a63"),
  "name": "Vivillon",
  "description": "Vivillon possui o ID 666. Vivillon with many different patterns are found all over the world. These patterns are affected by the climate of their habitat.",
  "attack": 90,
  "defense": 50,
  "height": 1.2
}
Fetched 6 record(s) in 7ms
Mockingjay(mongod-3.0.7) be-mean-pokemons>

```


## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama

```
var query = {$and: [{height:{$lte:0.5}}, {type: "grama"}]}

Mockingjay(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 24ms
Mockingjay(mongod-3.0.7) be-mean-pokemons>
```
:: Nesse caso não retornou nada, pois não há atributos TYPE na Collection. Aqui um EXEMPLO com informação que existe:
```
var query = {$and: [{height:{$lte:1.2}}, {name: "Vivillon"}]}
db.pokemons.find(query)
{
  "_id": ObjectId("56439131e25bbeb0b9427a63"),
  "name": "Vivillon",
  "description": "Vivillon possui o ID 666. Vivillon with many different patterns are found all over the world. These patterns are affected by the climate of their habitat.",
  "attack": 90,
  "defense": 50,
  "height": 1.2
}
Fetched 1 record(s) in 2ms
Mockingjay(mongod-3.0.7) be-mean-pokemons>
```


## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5
```
var query = {$or: [{name: "Pikachu"}, {attack:{$lte:0.5}}]}

Mockingjay(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 23ms
Mockingjay(mongod-3.0.7) be-mean-pokemons>

```
## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5

```
var query = {$and: [{attack:{$gte:48}}, {height: {$lte:0.5}}]}

Mockingjay(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 0ms
Mockingjay(mongod-3.0.7) be-mean-pokemons>

```
