# MongoDB - Aula 03 - Exercício
autor: Jean F. Santos

## Liste todos Pokemons com a altura **menor que** 0.5;
```
MacBook-Pro-de-jean(mongod-3.0.7) be-mean-pokemons> var query = {height: {$lt: 0.5}};
MacBook-Pro-de-jean(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query);
{
  "_id": ObjectId("56478e8a946eb268a71e80d3"),
  "name": "Weedle",
  "description": "Weedle has an extremely acute sense of smell. It is capable of distinguishing its favorite kinds of leaves from those it dislikes just by sniffing with its big red proboscis (nose).",
  "attack": 20,
  "defense": 20,
  "height": 0.3
}
```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5
```
acBook-Pro-de-jean(mongod-3.0.7) be-mean-pokemons> var query = {height: {$gte: 0.5}};
MacBook-Pro-de-jean(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query);
{
  "_id": ObjectId("56478e8a946eb268a71e80d0"),
  "name": "Bulbasaur",
  "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
  "attack": 30,
  "defense": 20,
  "height": 0.7
}
{
  "_id": ObjectId("56478e8a946eb268a71e80d1"),
  "name": "Charmander",
  "description": "alterando description",
  "attack": 30,
  "defense": 20,
  "height": 0.6
}
{
  "_id": ObjectId("56478e8a946eb268a71e80d2"),
  "name": "Squirtle",
  "description": "Squirtle's shell is not merely used for protection. The shell's rounded shape and the grooves on its surface help minimize resistance in water, enabling this Pokémon to swim at high speeds.",
  "attack": 30,
  "defense": 30,
  "height": 0.5
}
{
  "_id": ObjectId("56478e8a946eb268a71e80d4"),
  "name": "Clefairy",
  "description": "On every night of a full moon, groups of this Pokémon come out to play. When dawn arrives, the tired Clefairy return to their quiet mountain retreats and go to sleep nestled up against each other.",
  "attack": 20,
  "defense": 20,
  "height": 0.6
}
```

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama
```
var query = {$and: [{height: {$lte: 0.5}}, {type: 'grama'}]};
MacBook-Pro-de-jean(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query);
Fetched 0 record(s) in 8ms
```

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5
```
var query = {$or: [{name: 'Pikachu'}, {attack: {$lte: 0.5}}]};
MacBook-Pro-de-jean(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query);
Fetched 0 record(s) in 4ms
```

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5
```
var query = {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]};
MacBook-Pro-de-jean(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query);
Fetched 0 record(s) in 0ms
```
