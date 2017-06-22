# MongoDB - Aula 03 - Exercício
Autor: Igor luíz

## Listar todos os pokemons com altura __menor que 0.5__

```sh
localhost(mongod-3.0.8) be-mean-pokemons> db.pokemons.find({"height": {$lt: 0.5}})
{
  "_id": ObjectId("56b173ecf3bf0cb1edd0f06d"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
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
Fetched 2 record(s) in 1ms
```

## Listar todos os pokemons com altura __menor ou iqual que 0.5__

```sh 
localhost(mongod-3.0.8) be-mean-pokemons> db.pokemons.find({"height": {$lte: 0.5}})
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
Fetched 3 record(s) in 1ms
```

## Listar todos os pokemons com altura __menor ou iqual que 0.5__ e do typo __grama__

```sh
localhost(mongod-3.0.8) be-mean-pokemons> db.pokemons.find({$and: [{"height": {$lte: 0.5}},{"type":"grama"}]})
{
  "_id": ObjectId("56b173ecf3bf0cb1edd0f06d"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
Fetched 1 record(s) in 1ms
```


## Listar todos os pokemons com o nome __Pikachu__ ou com o attack __menor ou iqual que 0.5__

```sh
localhost(mongod-3.0.8) be-mean-pokemons> db.pokemons.find({$or: [{"name":"Pikachu"},{"attack": {$lte: 0.5}}]})
{
  "_id": ObjectId("56b17446f3bf0cb1edd0f06f"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletrico",
  "attack": 55,
  "height": 0.4,
  "defense": 50
}
Fetched 1 record(s) in 1ms
```

## Listar todos do pokemons com attack __maior ou iqual que 48__ e com height __menor ou igual que 0.5__

```sh
localhost(mongod-3.0.8) be-mean-pokemons> db.pokemons.find({ $and: [ {"attack": {$gte: 48}}, {"height": {$lte: 0.5}} ]  })
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
Fetched 3 record(s) in 0ms
```

