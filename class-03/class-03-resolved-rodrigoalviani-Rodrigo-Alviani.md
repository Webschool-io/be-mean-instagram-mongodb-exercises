# MongoDB - Aula 03 - Exercício
autor: Rodrigo Alviani

## Liste todos Pokemons com a altura **menor que** 0.5;
```
WMD00096(mongod-3.0.7) be-mean-pokemons> db.pokemons.find({height: {$lt: 0.5}});
{
  "_id": ObjectId("564a330af3878aca0716bca2"),
  "name": "Caterpie",
  "description": "For protection, it releases a horrible stench from the antennae on its head to drive away enemies.",
  "attack": 30,
  "defense": 35,
  "height": 0.3,
  "type": "Bug"
}
{
  "_id": ObjectId("564a330af3878aca0716bca3"),
  "name": "Pikachu",
  "description": "It raises its tail to check its sur roundings. The tail is sometimes struck by light ning in this pose. (Version 2)",
  "attack": 55,
  "defense": 40,
  "height": 0.4,
  "type": "Eletric"
}
Fetched 2 record(s) in 2ms
```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5
```
WMD00096(mongod-3.0.7) be-mean-pokemons> db.pokemons.find({height: {$gte: 0.5}});
{
  "_id": ObjectId("564a330af3878aca0716bc9f"),
  "name": "Bulbasaur",
  "description": "The seed on its back is filled with nutrients. The seed grows steadily larger as its body grows.",
  "attack": 49,
  "defense": 49,
  "height": 0.7,
  "type": "Grass"
}
{
  "_id": ObjectId("564a330af3878aca0716bca0"),
  "name": "Charmander",
  "description": "Obviously prefers hot places. When it rains, steam is said to spout from the tip of its tail.",
  "attack": 52,
  "defense": 43,
  "height": 0.6,
  "type": "Fire"
}
{
  "_id": ObjectId("564a330af3878aca0716bca1"),
  "name": "Squirtle",
  "description": "After birth, its back swells and hardens into a shell. Powerfully sprays foam from its mouth.",
  "attack": 48,
  "defense": 65,
  "height": 0.5,
  "type": "Water"
}
Fetched 3 record(s) in 2ms
```

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama
```
WMD00096(mongod-3.0.7) be-mean-pokemons> db.pokemons.find({$and: [{height: {$lte: 0.5}}, {type: 'Grass'}]});
Fetched 0 record(s) in 0ms
```

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5
```
WMD00096(mongod-3.0.7) be-mean-pokemons> db.pokemons.find({$or: [{attack: {$lte: 50}}, {name: 'Pikachu'}]});
{
  "_id": ObjectId("564a330af3878aca0716bc9f"),
  "name": "Bulbasaur",
  "description": "The seed on its back is filled with nutrients. The seed grows steadily larger as its body grows.",
  "attack": 49,
  "defense": 49,
  "height": 0.7,
  "type": "Grass"
}
{
  "_id": ObjectId("564a330af3878aca0716bca1"),
  "name": "Squirtle",
  "description": "After birth, its back swells and hardens into a shell. Powerfully sprays foam from its mouth.",
  "attack": 48,
  "defense": 65,
  "height": 0.5,
  "type": "Water"
}
{
  "_id": ObjectId("564a330af3878aca0716bca2"),
  "name": "Caterpie",
  "description": "For protection, it releases a horrible stench from the antennae on its head to drive away enemies.",
  "attack": 30,
  "defense": 35,
  "height": 0.3,
  "type": "Bug"
}
{
  "_id": ObjectId("564a330af3878aca0716bca3"),
  "name": "Pikachu",
  "description": "It raises its tail to check its sur roundings. The tail is sometimes struck by light ning in this pose. (Version 2)",
  "attack": 55,
  "defense": 40,
  "height": 0.4,
  "type": "Eletric"
}
Fetched 4 record(s) in 58ms
```

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com height **menor ou igual que** 0.5
```
WMD00096(mongod-3.0.7) be-mean-pokemons> db.pokemons.find({$and: [{height: {$lte: 0.5}}, {attack: {$gte: 48}}]});
{
  "_id": ObjectId("564a330af3878aca0716bca1"),
  "name": "Squirtle",
  "description": "After birth, its back swells and hardens into a shell. Powerfully sprays foam from its mouth.",
  "attack": 48,
  "defense": 65,
  "height": 0.5,
  "type": "Water"
}
{
  "_id": ObjectId("564a330af3878aca0716bca3"),
  "name": "Pikachu",
  "description": "It raises its tail to check its sur roundings. The tail is sometimes struck by light ning in this pose. (Version 2)",
  "attack": 55,
  "defense": 40,
  "height": 0.4,
  "type": "Eletric"
}
Fetched 2 record(s) in 1ms
```
