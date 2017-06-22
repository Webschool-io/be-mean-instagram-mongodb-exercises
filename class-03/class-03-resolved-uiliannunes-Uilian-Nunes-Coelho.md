# MongoDB - Aula 03 - Exercício
autor: Uilian Nunes Coelho

## Liste todos Pokemons com a altura **menor que** 0.5;

```
144(mongod-3.0.3) be-mean-pokemons> var query = {height: {$lte:0.5}}
144(mongod-3.0.3) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564fb465010a0d37f0f2516e"),
  "name": "Cacnea",
  "description": "Cacnea is a Grass type Pokémon introduced in Generation 3. It is known as the Cactus Pokémon.",
  "type": "Grass",
  "attack": 85,
  "height": 0.4
}
{
  "_id": ObjectId("5654f3f1cd1bdd189cd39d6e"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
Fetched 2 record(s) in 2ms

```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5

```
MacBook-Pro-de-Uilian-Nunes(mongod-3.0.3) be-mean-pokemons> var query = {height:{$gte:0.5}}
MacBook-Pro-de-Uilian-Nunes(mongod-3.0.3) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564687f79f36874a98ff79bf"),
  "name": "Zubat",
  "description": "Zubat is a Poison/Flying type Pokémon introduced in Generation 1. It is known as the Bat Pokémon",
  "type": "Poison/Flying",
  "attack": 45,
  "height": 0.79
}
{
  "_id": ObjectId("564687f79f36874a98ff79c0"),
  "name": "Jigglypuff",
  "description": "Jigglypuff is a Normal/Fairy type Pokémon introduced in Generation 1. It is known as the Balloon Pokémon",
  "type": "Fairy",
  "attack": 45,
  "height": 0.51
}
{
  "_id": ObjectId("564687f79f36874a98ff79c1"),
  "name": "Vileplume",
  "description": "Vileplume is a Grass/Poison type Pokémon introduced in Generation 1. It is known as the Flower Pokémon",
  "type": "Grass/Poison",
  "attack": 80,
  "height": 1.19
}
{
  "_id": ObjectId("564687f79f36874a98ff79c2"),
  "name": "Dragonite",
  "description": "Dragãozinho do Mal",
  "type": "Dragon/Flying",
  "attack": 134,
  "height": 2.21
}
{
  "_id": ObjectId("564687f79f36874a98ff79c3"),
  "name": "Raichu",
  "description": "Raichu is an Electric type Pokémon introduced in Generation 1. It is known as the Mouse Pokémon",
  "type": "electric",
  "attack": 90,
  "height": 0.79
}
{
  "_id": ObjectId("564687f79f36874a98ff79c4"),
  "name": "Pidgeot",
  "description": "Pidgeot is a Normal/Flying type Pokémon introduced in Generation 1. It is known as the Bird Pokémon",
  "type": "Flying",
  "attack": 80,
  "height": 1.5
}
Fetched 6 record(s) in 96ms
```

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama

```
MacBook-Pro-de-Uilian-Nunes(mongod-3.0.3) be-mean-pokemons> var query = {$and:[{height:{$lte:0.5}},{type:/grass/i}]}
MacBook-Pro-de-Uilian-Nunes(mongod-3.0.3) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564fb465010a0d37f0f2516e"),
  "name": "Cacnea",
  "description": "Cacnea is a Grass type Pokémon introduced in Generation 3. It is known as the Cactus Pokémon.",
  "type": "Grass",
  "attack": 85,
  "height": 0.4
}
Fetched 1 record(s) in 28ms

```

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5

```
MacBook-Pro-de-Uilian-Nunes(mongod-3.0.3) be-mean-pokemons> var query = {$or:[{attack:{$lte:0.5}},{name:/pikachu/i}]}
MacBook-Pro-de-Uilian-Nunes(mongod-3.0.3) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5654f3f1cd1bdd189cd39d6e"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
Fetched 1 record(s) in 1ms

```

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5

```
MacBook-Pro-de-Uilian-Nunes(mongod-3.0.3) be-mean-pokemons> var query = {$and:[{attack:{$gte:48}},{height:{$lte:0.5}}]}
MacBook-Pro-de-Uilian-Nunes(mongod-3.0.3) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564fb465010a0d37f0f2516e"),
  "name": "Cacnea",
  "description": "Cacnea is a Grass type Pokémon introduced in Generation 3. It is known as the Cactus Pokémon.",
  "type": "Grass",
  "attack": 85,
  "height": 0.4
}
{
  "_id": ObjectId("5654f3f1cd1bdd189cd39d6e"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
Fetched 2 record(s) in 1ms

```