# MongoDB - Aula 03 - Exercício
autor: Evandro Santos

## Pokemons com a altura menor que 0.5

```
Evandros-Mini(mongod-3.0.7) be-mean-instagram> var query = {height: {$lt: 0.5}}
Evandros-Mini(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56492b2650b7aff94f25c32f"),
  "name": "pikachu",
  "description": "Rato elétrico",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("56492dee7b6c3094d7d697ea"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grass",
  "attack": 46,
  "height": 0.4
}
{
  "_id": ObjectId("56492f197b6c3094d7d697ed"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "insect",
  "attack": 30,
  "height": 0.3,
  "defense": 35
}
Fetched 3 record(s) in 3ms
```

## Pokemons com a altura maior ou igual que 0.5
```
Evandros-Mini(mongod-3.0.7) be-mean-instagram> var query = {height: {$gte: 0.5}}

Evandros-Mini(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56492df17b6c3094d7d697eb"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "water",
  "attack": 48,
  "height": 0.5
}
{
  "_id": ObjectId("56492e187b6c3094d7d697ec"),
  "name": "Charmander",
  "description": "O cão chupando manga",
  "type": "fire",
  "attack": 52,
  "height": 0.6
}
Fetched 2 record(s) in 2ms
```

## Pokemons com a altura menor ou igual que 0.5 E do tipo grama
```
Evandros-Mini(mongod-3.0.7) be-mean-instagram> var query = {$and: [{height: {$lte: 0.5}}, {type: 'grass'}]}
Evandros-Mini(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56492dee7b6c3094d7d697ea"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grass",
  "attack": 46,
  "height": 0.4
}
Fetched 1 record(s) in 3ms
```

## Pokemons com o nome Pikachu ou ataque menor ou igual a 0.5
```
Evandros-Mini(mongod-3.0.7) be-mean-instagram> var query = {$or: [{name: 'pikachu'}, {attack:  {$lte: 0.5}}]}
Evandros-Mini(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56492b2650b7aff94f25c32f"),
  "name": "pikachu",
  "description": "Rato elétrico",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
Fetched 1 record(s) in 1ms
```

## Pokemons com o ataque maior ou igual a 48 e altura menor ou igual a 0.5
```
Evandros-Mini(mongod-3.0.7) be-mean-instagram> var query = {$and: [{attack: {$gte: 48}}, {attack:  {$lte: 0.5}}]}
Evandros-Mini(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
Fetched 0 record(s) in 0ms
Evandros-Mini(mongod-3.0.7) be-mean-instagram>
```
