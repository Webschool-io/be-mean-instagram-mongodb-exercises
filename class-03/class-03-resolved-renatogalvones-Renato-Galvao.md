# MongoDB - Aula 03 - Exercício
autor: Renato Galvão

## Lista todos os pokemons altura menor que 0.5

```
Renatos-Mac-Pro(mongod-3.2.0) be-mean-pokemons> db.pokemons.find({height: {$lt: 0.5}})
Fetched 0 record(s) in 1ms
```

## Lista todos os pokemons altura maior ou igual a 0.5

```
Renatos-Mac-Pro(mongod-3.2.0) be-mean-pokemons> db.pokemons.find({height: {$gte: 0.5}})
{
  "_id": ObjectId("56c1ce9965d70c166a207adf"),
  "name": "mewtwo",
  "description": "bichão fodão psicótico",
  "type": "psychic",
  "attack": 110,
  "height": 20
}
{
  "_id": ObjectId("56c1cf1965d70c166a207ae0"),
  "name": "dragonite",
  "description": "dragão que só voa a noite",
  "type": "dragon",
  "attack": 134,
  "height": 22
}
{
  "_id": ObjectId("56c1d02f65d70c166a207ae1"),
  "name": "dragonite",
  "description": "chocante",
  "type": "electric",
  "attack": 83,
  "height": 11
}
{
  "_id": ObjectId("56c1d05b65d70c166a207ae2"),
  "name": "magmar",
  "description": "queeeeeeente",
  "type": "fire",
  "attack": 95,
  "height": 13
}
{
  "_id": ObjectId("56c1d09165d70c166a207ae3"),
  "name": "staryu",
  "description": "estrelinha",
  "type": "water",
  "attack": 45,
  "height": 8
}
Fetched 5 record(s) in 2ms

```

## Lista todos os pokemons com altura menor ou igual a 0.5 e do tipo grama

```
Renatos-Mac-Pro(mongod-3.2.0) be-mean-pokemons> db.pokemons.find({$and: [{height: {$lte: 0.5}}, {type:'grass'}]})
Fetched 0 record(s) in 0ms

```

## Lista todos os pokemons com name 'Pikachu' ou com attack menor ou igual a 0.5

```
Renatos-Mac-Pro(mongod-3.2.0) be-mean-pokemons> db.pokemons.find({$or: [{name: 'Pikachu'}, {attack: {$lte: 0.5}}]})
Fetched 0 record(s) in 1ms

```

## Lista todos os pokemons com attack maior ou igual a 48 e altura menor ou igual a 0.5
```
Renatos-Mac-Pro(mongod-3.2.0) be-mean-pokemons> db.pokemons.find({$or: [{name: 'Pikachu'}, {height: {$lte: 0.5}}]})
Fetched 0 record(s) in 1ms

```
