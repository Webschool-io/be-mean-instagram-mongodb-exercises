# MongoDB - Aula 03 - Exercício
autor: Hudson Brendon Silva


## Liste todos Pokemons com a altura **menor que** 0.5;

```
ubuntu(mongod-3.0.7) pokemons> db.pokemons.find({height:{$lt: 0.5}})
{
  "_id": ObjectId("564d08317ba047cbf6497bc8"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("564d08a07ba047cbf6497bc9"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("564d0a817ba047cbf6497bcc"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35
}
Fetched 3 record(s) in 31ms

```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5

```
ubuntu(mongod-3.0.7) pokemons> db.pokemons.find({height:{$gte: 0.5}})
{
  "_id": ObjectId("564d08d37ba047cbf6497bca"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("564d09007ba047cbf6497bcb"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
Fetched 2 record(s) in 1ms

```

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama

```
ubuntu(mongod-3.0.7) pokemons> db.pokemons.find({$and: [{height: {$lt: 0.5}}, {type: "grama"}]})
{
  "_id": ObjectId("564d08a07ba047cbf6497bc9"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
Fetched 1 record(s) in 2ms

```

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5

```
ubuntu(mongod-3.0.7) pokemons> db.pokemons.find({$and: [{name: "Pikachu"}, {attack: {$lte: 0.5}}]})
Fetched 0 record(s) in 0ms

```

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5

```
ubuntu(mongod-3.0.7) pokemons> db.pokemons.find({$and: [{height: {$lte: 0.5}}, {attack: {$gte: 48}}]})
{
  "_id": ObjectId("564d08317ba047cbf6497bc8"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("564d08a07ba047cbf6497bc9"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("564d09007ba047cbf6497bcb"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
Fetched 3 record(s) in 49ms

```
