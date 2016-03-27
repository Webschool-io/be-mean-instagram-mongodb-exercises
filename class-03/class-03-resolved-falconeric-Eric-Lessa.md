# MongoDB - Aula 03 - Exercício
autor: ERIC LESSA

## Liste todos Pokemons com a altura menor que 0.5;

```
var query = {"height":{$lt:0.5}}
elcarvalho(mongod-3.2.4) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56ea003b69e48ecf93ac6a95"),
  "name": "Pikachu",
  "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, it's evidence that this Pokémon mistook the intensity of its charge.",
  "attack": 55,
  "defense": 30,
  "height": 0.4
}
Fetched 1 record(s) in 2ms
```

## Liste todos Pokemons com a altura maior ou igual que 0.5;

```
var query = {"height":{$gte:0.5}}
elcarvalho(mongod-3.2.4) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56e9b5cd5cf4bdfce34de41d"),
  "name": "Bulbasaur",
  "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
  "attack": 49,
  "defense": 49,
  "height": 0.7
}
Fetched 1 record(s) in 2ms
```

## Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama;

```
var query = { $and:[ {"height":{$lte:0.5}}, {"Type":"Grass"} ] }
elcarvalho(mongod-3.2.4) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56ea04e469e48ecf93ac6a96"),
  "name": "Paras",
  "description": "Paras has parasitic mushrooms growing on its back called tochukaso. They grow large by drawing nutrients from this Bug Pokémon host. They are highly valued as a medicine for extending life.",
  "attack": 70,
  "defense": 55,
  "height": 0.3,
  "Type": "Grass"
}
{
  "_id": ObjectId("56ea04e469e48ecf93ac6a97"),
  "name": "MissingNo",
  "description": "Is an unofficial Pokémon species found in the video games Pokémon Red and Blue. Standing for Missing Number, MissingNo. are used as error handlers by game developer Game Freak",
  "attack": 0.4,
  "defense": 55,
  "height": 0.3,
  "Type": "Grass"
}
Fetched 2 record(s) in 2ms
```

## Liste todos Pokemons com o name `Pikachu` OU com attack menor ou igual que 0.5;

```
var query = { $or:[ {"attack":{$lte:0.5}}, {"name":"Pikachu"} ] }
elcarvalho(mongod-3.2.4) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56ea003b69e48ecf93ac6a95"),
  "name": "Pikachu",
  "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, it's evidence that this Pokémon mistook the intensity of its charge.",
  "attack": 55,
  "defense": 30,
  "height": 0.4
}
{
  "_id": ObjectId("56ea04e469e48ecf93ac6a97"),
  "name": "MissingNo",
  "description": "Is an unofficial Pokémon species found in the video games Pokémon Red and Blue. Standing for Missing Number, MissingNo. are used as error handlers by game developer Game Freak",
  "attack": 0.4,
  "defense": 55,
  "height": 0.3,
  "Type": "Grass"
}
Fetched 2 record(s) in 104ms
```

## Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com  height menor ou igual que 0.5;

```
var query = { $and:[ {"attack":{$gte:48}}, {"height":{$lte:0.5}} ] }
elcarvalho(mongod-3.2.4) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56e9b5cd5cf4bdfce34de423"),
  "name": "Squirtle",
  "description": "Squirtle's shell is not merely used for protection. The shell's rounded shape and the grooves on its surface help minimize resistance in water, enabling this Pokémon to swim at high speeds.",
  "attack": 48,
  "defense": 65,
  "height": 0.5
}
{
  "_id": ObjectId("56ea003b69e48ecf93ac6a95"),
  "name": "Pikachu",
  "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, it's evidence that this Pokémon mistook the intensity of its charge.",
  "attack": 55,
  "defense": 30,
  "height": 0.4
}
{
  "_id": ObjectId("56ea04e469e48ecf93ac6a96"),
  "name": "Paras",
  "description": "Paras has parasitic mushrooms growing on its back called tochukaso. They grow large by drawing nutrients from this Bug Pokémon host. They are highly valued as a medicine for extending life.",
  "attack": 70,
  "defense": 55,
  "height": 0.3,
  "Type": "Grass"
}
Fetched 3 record(s) in 3ms
```