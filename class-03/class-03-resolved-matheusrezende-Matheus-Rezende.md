# MongoDB - Aula 03 - Exercício
Autor: Matheus Rezende Figueira

## Pokémons com altura menor que 0.5

```
matheus(mongod-3.0.12) be-mean-instagram> var query = {height: {$gt: 0.5}}
matheus(mongod-3.0.12) be-mean-instagram> query
{
  "height": {
    "$gt": 0.5
  }
}
matheus(mongod-3.0.12) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("573c98bdaa189a69976d2d51"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
Fetched 1 record(s) in 2ms

```

## Pokémons com altura maior ou igual a 0.5

```
matheus(mongod-3.0.12) be-mean-instagram> var query = {height: {$gte: 0.5}}
matheus(mongod-3.0.12) be-mean-instagram> query
{
  "height": {
    "$gte": 0.5
  }
}
matheus(mongod-3.0.12) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("573c98bdaa189a69976d2d51"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("573c9923aa189a69976d2d52"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
Fetched 2 record(s) in 2ms

```

## Pokémons com altura menor ou igual a 0.5 e do tipo grama

```
matheus(mongod-3.0.12) be-mean-instagram> var query = {$and: [{type:'grama'},{height: {$gte: 0.5}}]}
matheus(mongod-3.0.12) be-mean-instagram> db.pokemons.find(query)
Fetched 0 record(s) in 1ms
matheus(mongod-3.0.12) be-mean-instagram>


```

## Pokémons com nome 'Pikachu' ou com attack menor ou igual a 0.5

```
matheus(mongod-3.0.12) be-mean-instagram> var query = {$or: [{name:'Pikachu'},{attack:{$lte: 0.5}}]}
matheus(mongod-3.0.12) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("573c91dbbcdf32828867cbdf"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "atack": 100,
  "height": 0.4,
  "attack": 55
}
Fetched 1 record(s) in 1ms

```

## Pokémons com nome attack maior ou igual a 48 e altura menor ou igual a 0.5

```
matheus(mongod-3.0.12) be-mean-instagram> var query = {$and:[{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}
matheus(mongod-3.0.12) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("573c91dbbcdf32828867cbdf"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "atack": 100,
  "height": 0.4,
  "attack": 55
}
{
  "_id": ObjectId("573c9858aa189a69976d2d50"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("573c9923aa189a69976d2d52"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
Fetched 3 record(s) in 2ms

```
